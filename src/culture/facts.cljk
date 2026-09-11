(ns culture.facts
  "Country-level regional-culture catalog for Norway (NOR) -- national
  dishes, protected products, beverages, crafts, festivals and heritage
  sites, per ADR-2607171400 addendum 2 (cloud-itonami-municipality-
  culture-catalog Wave 1, in com-junkawasaki/root). Sibling namespace to
  `marketentry.facts` / `statute.facts` (ADR-2607141700); city-level
  counterparts live in the cloud-itonami-municipality-* repos.

  Catalog is keyed by UPPERCASE ISO3 (mirrors `statute.facts`); entries
  carry no :culture/municipality (that attribute is city-level only).

  Every entry cites a source URL that was actually fetched and read on
  :culture/retrieved-at -- never fabricated. Summaries state only what the
  cited source confirms. An item not in this table has NO spec-basis, full
  stop; extend `catalog`, do not invent an id/url.")

(def catalog
  "iso3 -> vector of culture entries."
  {"NOR"
   [{:culture/id "nor.dish.farikal"
     :culture/name "Fårikål"
     :culture/country "NOR"
     :culture/kind :dish
     :culture/summary "Traditional Norwegian dish of mutton with bone and cabbage, widely regarded as the country's national dish."
     :culture/url "https://en.wikipedia.org/wiki/F%C3%A5rik%C3%A5l"
     :culture/url-provenance :wikipedia-en
     :culture/retrieved-at "2026-07-17"}
    {:culture/id "nor.dish.rakfisk"
     :culture/name "Rakfisk"
     :culture/country "NOR"
     :culture/kind :dish
     :culture/summary "Norwegian fish dish made from trout or char that is salted and fermented (autolyzed) for two to three months, or even up to a year."
     :culture/url "https://en.wikipedia.org/wiki/Rakfisk"
     :culture/url-provenance :wikipedia-en
     :culture/retrieved-at "2026-07-17"}
    {:culture/id "nor.dish.lutefisk"
     :culture/name "Lutefisk"
     :culture/country "NOR"
     :culture/kind :dish
     :culture/summary "Dried whitefish, usually cod, cured in lye; eaten across several Nordic countries and traditionally part of Norwegian Christmas (julebord) feasts."
     :culture/url "https://en.wikipedia.org/wiki/Lutefisk"
     :culture/url-provenance :wikipedia-en
     :culture/retrieved-at "2026-07-17"}
    {:culture/id "nor.dish.pinnekjott"
     :culture/name "Pinnekjøtt"
     :culture/country "NOR"
     :culture/kind :dish
     :culture/summary "Traditional Norwegian main-course dinner dish based on dried and salted lamb ribs, closely associated with Christmas."
     :culture/url "https://en.wikipedia.org/wiki/Pinnekj%C3%B8tt"
     :culture/url-provenance :wikipedia-en
     :culture/retrieved-at "2026-07-17"}
    {:culture/id "nor.beverage.akvavit"
     :culture/name "Akvavit"
     :culture/country "NOR"
     :culture/kind :beverage
     :culture/summary "Distilled spirit principally produced in Scandinavia since the 15th century; most Norwegian brands are matured in oak casks, including the Linje Aquavit tradition of maturing at sea."
     :culture/url "https://en.wikipedia.org/wiki/Akvavit"
     :culture/url-provenance :wikipedia-en
     :culture/retrieved-at "2026-07-17"}
    {:culture/id "nor.product.brunost"
     :culture/name "Brunost"
     :culture/country "NOR"
     :culture/kind :product
     :culture/summary "Norwegian brown whey cheese (mysost), primarily produced in Norway and regarded as one of the country's most iconic foodstuffs."
     :culture/url "https://en.wikipedia.org/wiki/Brunost"
     :culture/url-provenance :wikipedia-en
     :culture/retrieved-at "2026-07-17"}
    {:culture/id "nor.craft.rosemaling"
     :culture/name "Rosemaling"
     :culture/country "NOR"
     :culture/kind :craft
     :culture/summary "Scandinavian decorative folk painting of stylized floral scrollwork that flourished from the 1700s to the mid-1800s and became particularly prominent in Norway, especially in Hallingdal and Telemark."
     :culture/url "https://en.wikipedia.org/wiki/Rosemaling"
     :culture/url-provenance :wikipedia-en
     :culture/retrieved-at "2026-07-17"}
    {:culture/id "nor.craft.bunad"
     :culture/name "Bunad"
     :culture/country "NOR"
     :culture/kind :craft
     :culture/summary "Norwegian umbrella term for traditional folk costumes rooted in 18th-19th century rural dress and Norwegian national romanticism, worn at celebrations such as Constitution Day."
     :culture/url "https://en.wikipedia.org/wiki/Bunad"
     :culture/url-provenance :wikipedia-en
     :culture/retrieved-at "2026-07-17"}
    {:culture/id "nor.festival.constitution-day"
     :culture/name "Constitution Day"
     :culture/name-local "Syttende mai"
     :culture/country "NOR"
     :culture/kind :festival
     :culture/summary "The National Day of Norway, an official public holiday on 17 May commemorating the 1814 signing of Norway's constitution at Eidsvoll, marked nationwide by children's parades in traditional costume."
     :culture/url "https://en.wikipedia.org/wiki/Constitution_Day_(Norway)"
     :culture/url-provenance :wikipedia-en
     :culture/retrieved-at "2026-07-17"}
    {:culture/id "nor.heritage.bryggen"
     :culture/name "Bryggen"
     :culture/country "NOR"
     :culture/kind :heritage
     :culture/summary "Series of Hanseatic heritage commercial buildings lining the eastern side of the Vagen harbour in Bergen, Norway, on the UNESCO World Heritage list since 1979."
     :culture/url "https://en.wikipedia.org/wiki/Bryggen"
     :culture/url-provenance :wikipedia-en
     :culture/retrieved-at "2026-07-17"}]})

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
      :note (str "cloud-itonami-iso3166-nor culture catalog "
                 "(ADR-2607171400 addendum 2, Wave 1): " (count (get catalog "NOR"))
                 " NOR entries, each with a fetched-and-read citation. "
                 "Extend `culture.facts/catalog`, never fabricate an id/url.")})))

(defn by-kind [iso3 kind]
  (filterv #(= (:culture/kind %) kind) (spec-basis iso3)))
