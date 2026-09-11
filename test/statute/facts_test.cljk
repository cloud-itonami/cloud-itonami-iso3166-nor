(ns statute.facts-test
  (:require [kotoba.lang.text :as str]
            [clojure.test :refer [deftest is]]
            [statute.facts :as facts]))

(deftest nor-has-spec-basis
  (let [sb (facts/spec-basis "NOR")]
    (is (= 3 (count sb)))
    (is (every? #(str/starts-with? (:statute/url %) "https://lovdata.no/") sb))
    (is (every? :statute/law-number sb))))

(deftest unknown-jurisdiction-has-no-spec-basis
  (is (nil? (facts/spec-basis "ATL")))
  (is (nil? (facts/spec-basis "ZZZ"))))

(deftest coverage-is-honest
  (let [c (facts/coverage ["NOR" "JPN" "ATL"])]
    (is (= 3 (:requested c)))
    (is (= 1 (:covered c)))
    (is (= ["ATL" "JPN"] (:missing-jurisdictions c)))))

(deftest by-topic-filters
  (is (= ["nor.arbeidsmiljoloven-2005"]
         (mapv :statute/id (facts/by-topic "NOR" :labor))))
  (is (empty? (facts/by-topic "NOR" :environment)))
  (is (empty? (facts/by-topic "ATL" :labor))))
