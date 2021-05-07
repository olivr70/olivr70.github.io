
## la reprsentation des données géographiques

- [wgs84](https://www.w3.org/2003/01/geo/wgs84_pos)
```@prefix geo: <http://www.w3.org/2003/01/geo/wgs84_pos#>```


## [Geonames](https://www.geonames.org/)

Une API pour accéder à une base mondiale de noms géographiques

De multiples Web Service sont disponibles

Un client .net existe [GeoNameDotOrgDotNet](https://archive.codeplex.com/?p=geonamesdotorgdotnet) sur CodePlex - ne sera plus disponible ). Il aussi disponible sur [java2s.com](http://www.java2s.com/Open-Source/CSharp_Free_Code/XML/Download_GeonamesDotOrgDotNet.htm.)

## Getty [Thesaurus of Geographic Names](http://www.getty.edu/research/tools/vocabularies/tgn/) (TGN)

un thesaurus mondial des noms géographiques

On peut retrouver tous les noms de pays, noms de régions, départements, communes françaises
La hiérarchie géographique est également décrite

Avec un [accès SPARQL](http://vocab.getty.edu/)

[API](http://www.getty.edu/research/tools/vocabularies/vocab_web_services.pdf)


# Base Adresse Nationale

API pour toutes les adresses en France. Avec une recherche full text avec adresse partielle.
Retourne un GeoJSON.

## [API](https://geo.api.gouv.fr/adresse)

### Exemples
`https://api-adresse.data.gouv.fr/search/?q=rue+de+montbrillant`
