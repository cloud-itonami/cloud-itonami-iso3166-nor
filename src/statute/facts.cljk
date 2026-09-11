(ns statute.facts
  "General-law compliance catalog for Norway (NOR) -- extends this repo's
  existing `marketentry.facts` (public-procurement market-entry only,
  narrow scope) with a second, orthogonal catalog of statutes a company
  generally must track for compliance. Mirrors
  cloud-itonami-iso3166-jpn/-usa/-esp/-swe's `statute.facts`
  (ADR-2607141700, cloud-itonami-compliance-fact-federation).

  Every entry cites an OFFICIAL lovdata.no (Lovdata, Norway's official
  legal information system) URL -- never fabricated. A law not in this
  table has NO spec-basis, full stop; extend `catalog`, do not invent an
  id/url. Title, LOV citation number, and entry-into-force date for
  every entry below were independently WebFetch-verified against the
  live lovdata.no page on 2026-07-15 (lovdata.no rendered directly,
  unlike e.g. fedlex.admin.ch which is JS-only).")

(def catalog
  "iso3 -> vector of statute entries."
  {"NOR"
   [{:statute/id "nor.aksjeloven-1997"
     :statute/title "Lov om aksjeselskaper (aksjeloven) (Norwegian Companies Act)"
     :statute/jurisdiction "NOR"
     :statute/kind :law
     :statute/law-number "LOV-1997-06-13-44"
     :statute/url "https://lovdata.no/lov/1997-06-13-44"
     :statute/url-provenance :official-lovdata
     :statute/enacted-date "1999-01-01"
     :statute/retrieved-at "2026-07-15"
     :statute/topic #{:corporate-governance :incorporation}}
    {:statute/id "nor.personopplysningsloven-2018"
     :statute/title "Act relating to the processing of personal data (The Personal Data Act)"
     :statute/jurisdiction "NOR"
     :statute/kind :law
     :statute/law-number "LOV-2018-06-15-38"
     :statute/url "https://lovdata.no/dokument/NLE/lov/2018-06-15-38"
     :statute/url-provenance :official-lovdata
     :statute/enacted-date "2018-07-20"
     :statute/retrieved-at "2026-07-15"
     :statute/topic #{:data-protection :privacy}}
    {:statute/id "nor.arbeidsmiljoloven-2005"
     :statute/title "Act relating to the working environment, working hours and employment protection, etc. (Working Environment Act)"
     :statute/jurisdiction "NOR"
     :statute/kind :law
     :statute/law-number "LOV-2005-06-17-62"
     :statute/url "https://lovdata.no/dokument/NLE/lov/2005-06-17-62"
     :statute/url-provenance :official-lovdata
     :statute/enacted-date "2006-01-01"
     :statute/retrieved-at "2026-07-15"
     :statute/topic #{:labor :employment}}]})

(defn spec-basis [iso3] (get catalog iso3))

(defn coverage
  ([] (coverage (keys catalog)))
  ([iso3s]
   (let [have (filter catalog iso3s)
         missing (remove catalog iso3s)]
     {:requested (count iso3s)
      :covered (count have)
      :covered-jurisdictions (vec (sort have))
      :missing-jurisdictions (vec (sort missing))
      :note (str "cloud-itonami-iso3166-nor statute.facts Wave 0 (ADR-2607141700): "
                 (count (get catalog "NOR")) " NOR statutes seeded with an "
                 "official lovdata.no citation. Extend "
                 "`statute.facts/catalog`, never fabricate a law-id or URL.")})))

(defn by-topic [iso3 topic]
  (filterv #(contains? (:statute/topic %) topic) (spec-basis iso3)))
