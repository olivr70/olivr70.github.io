



## Notation des valeurs qui changent dnas le temps

### [OWL-Time](https://www.w3.org/TR/owl-time/)

``` 
@prefix time: <http://www.w3.org/2006/time#>
```

[Un article du W3C](https://www.w3.org/2015/spatial/wiki/OWL_Time_Ontology_adoption) qui 
reprend l'historique et recense l'adoption

Le mécanisme est extrêmement ambitieux, avec la volonté de représenter une très grande
variété de calendrier, et même d'autres notations temporelles (ex : ères géologiques)

Pour les cas simples, il faut retenir les éléments suivants

- la propriété **time:hasTime** permet d'associer un instant ou un intervalle à une ressource

- time:Instant
  propriétés possibles : inXSDDate, inXSDDateTimeStamp:, :inXSD

#### Exemples

- ``` 
ex:aThing time:hasTime [time:inXSDDate "2001-01-01"^^xsd:date ] .


ex:aThing time:hasTime [time:hasBeginning [ time:inXSDDate "2001-01-01"^^xsd:date] ; time:hasEnd [ :inXSDDate "2010-12-31" ] ].
```