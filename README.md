## Requêtes WikiData

### Question 1: juste les peintures de monet :


````
select distinct ?item
where {
    ?item wdt:P31/wdt:P279* wd:Q3305213 .
    ?item wdt:P170 wd:Q296 .
	}
````


### Question 2: avec les labels (via le service wikibase:label) et les images associées


````
select distinct ?item ?itemLabel ?img
where {
    ?item wdt:P31/wdt:P279* wd:Q3305213 .
    ?item wdt:P170 wd:Q296 .
	?item wdt:P18 ?img.
    SERVICE wikibase:label {
        bd:serviceParam wikibase:language "fr,en" .
    }}
````

### Question 3: avec en option (via OPTIONAL) les collections/lieux de conservation

````
select distinct ?item ?itemLabel ?img ?lieux ?lieuxLabel
where {
    ?item wdt:P31/wdt:P279* wd:Q3305213 .
    ?item wdt:P170 wd:Q296 .
	?item wdt:P18 ?img.
    SERVICE wikibase:label {
        bd:serviceParam wikibase:language "fr,en" .
    }
	 OPTIONAL{?item wdt:P195 ?lieux
    }}
````
