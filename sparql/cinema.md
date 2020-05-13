## Le cinéma dans RDF

L'entité pour un film est http://dbpedia.org/ontology/Film

Le schéma correspondant est [Movie - schema.org Type](https://schema.org/Movie)

On trouve une propriété http://dbpedia.org/ontology/idAllocine qui est l'identifiant d'un film sur AlloCiné.

Sur dbpedia, pour un film, on trouve les propriétés utiles:
- _foaf:isPrimaryTopicOf_ (lien inverse de) _foaf:primaryTopic_ : qui contient une ou plusieurs URL vers des pages web parlant du film  
En particulier wiki_fr:.... pour le lien vers Wikipedia



## Allocine

Les urls de page Allociné (2020) ont la forme http://www.allocine.fr/film/fichefilm_gen_cfilm=XXXX.html ou XXXX correspond à la valeur de la propriété RDF **idAllocine** ( [...](http://mappings.dbpedia.org/index.php/OntologyProperty:IdAllocine) )

Ex : pour la `La vie d'Adèle` : http://www.allocine.fr/film/fichefilm_gen_cfilm=203302.html
