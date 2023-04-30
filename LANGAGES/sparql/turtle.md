# Turtle

[spécification RDF 1.1 Turtle](https://www.w3.org/TR/turtle/)

le type MIME est `text/turtle`

## Principes

- chaque expression commence par un **subject** et est terminé par un .
- après le subjet on trouve une série de paires **prédicat** **objec** séparés par des ;
- la référence à un objet peut aussi être une liste, séparés par des virgules

La référence aux objets peut se faire :
- par des IRIs absolues, entre < > : `<http://....>`
- par des IRIS relatives,
    - par rapport à la l'URL de base du graphe
    - deux manières de la spécifier
      - `@base <http://one.example/> .`
      - `BASE <http://one.example/>`
- par des IRIs préfixées
  - les préfixes sont ajoutés au début du graphe
    - `@prefix p: <http://two.example/> .`
    - `PREFIX p: <http://two.example/>`
  - on fait ensuite référence à `p:XX` (sans les < >)
  - il est possible de définir le préfixe vide (`:`)


## Les litéraux
- il s'agit de chaines, éventuellement typées. Plusieurs quotes
   - **'** ou **"** pour les chaines sur une seule ligne
   - ***'''*** ou ***"""*** pour les chaines sur plusieurs lignes
- les échappements suivants sont possibles
  - **\u0000** et **\U00000000**
  - **\t** **\r** **\n**
- une chaine peut être typé avec **^^<IRI>** ou **^^prefix:IRI**  
  - les types courant sont les [types xsd](https://fr.wikipedia.org/wiki/XML_Schema#Types_de_donn%C3%A9es) (XML Schema), référencés avec l'ajout 
    d'un préfixe `@prefix xsd: <http://www.w3.org/2001/XMLSchema#> .`
  - quelques types utiles
    - xsd:string
    - [xsd:date](http://www.datypic.com/sc/xsd/t-xsd_date.html) date au format CCYY-MM-DD : ex : `2004-09-03`
      (et de nombreux dérivés xsd:gYear, xsd:gMonth ...)
    - [xsd:duration](http://www.datypic.com/sc/xsd/t-xsd_duration.html) : ex `P20M` pour 20 mois 
    - *xsd:float*, *xsd:double* et *xsd:decimal*
    - *xsd:integer*,*xsd:negativeInteger*, *xsd:positiveInteger*, *xsd:nonNegativeInteger*
    - [xsd:boolean](http://www.datypic.com/sc/xsd/t-xsd_boolean.html) ex : `true` ou `false`

## les objets anonymes
- le préfixe `_:` (ex: `_:john`) permet de désigner des objets nommés dans le graphe courant, mais sans IRI absolus 
- le groupe `[` et `]` permet de préciser les propritétés d'un objet anonyme
  - ex : ` [ foaf:name "Bob" ]`
  - on peut préciser `a` pour indiquer le type de l'objet anonyme


## les Collections
- une liste peut être représentée entre parenthèses `(` et `)`
   - cela corresponnd à une rdf:first et rdf:next
- il existe aussi des convetions RDF pour représenter des groupes
  - rdf:bag, rdf:seq et rdf:alt
  - on précise avec rdf:_1, rdf:_2... les items du groupe
  - ATTENTION : il s'agit de conventions, aucune vérification n'est faite en standard dans RDF