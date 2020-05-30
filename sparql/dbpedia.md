
## DBPedia

DBpedia est un projet universitaire et communautaire d'exploration et extraction automatique de données dérivées de Wikipédia. Son principe est de proposer une version structurée et sous forme de données normalisées au format RDF des contenus encyclopédiques de chaque page de Wikipédia.

Il existe une version française [DBpedia FR](http://fr.dbpedia.org/sparqlTuto/tutoSparql.html)) et anglaise[Virtuoso SPARQL Query Editor](http://dbpedia.org/sparql)

[DBpedia Mappings](http://mappings.dbpedia.org/index.php/Main_Page)

### Pour tester

utiliser [Flint](http://fr.dbpedia.org/sparqlEditor/index.html), un éditeur SPARQL moderne avec coloration syntaxique & ci

### les préfixes

Sont définis par défaut
- rdf: http://www.w3.org/1999/02/22-rdf-syntax-ns#
- rdfs: http://www.w3.org/2000/01/rdf-schema#
- owl: http://www.w3.org/2002/07/owl#
- xsd: http://www.w3.org/2001/XMLSchema#
- dc: http://purl.org/dc/elements/1.1/
- foaf: http://xmlns.com/foaf/0.1/
- dbpedia: http://dbpedia.org/resource
- dbpedia-owl: http://dbpedia.org/ontology/
- dbpprop: http://dbpedia.org/property/


### Exemples

```sparql
PREFIX rdf:<http://www.w3.org/1999/02/22-rdf-syntax-ns#>

SELECT DISTINCT ?titre WHERE {

?film a <http://dbpedia.org/ontology/Film> .
?film rdfs:label ?titre
} LIMIT 10
```