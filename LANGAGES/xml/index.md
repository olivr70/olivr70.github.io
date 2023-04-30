


## XML Schema

- section de la documentation sur la [définition des types complexes](https://docs.microsoft.com/en-us/previous-versions/aa468557(v=msdn.10)?redirectedfrom=MSDN#defining-complex-types)
  - **elementFormDefault** et **attributeFormDefault** permettent de déterminer si dans
    une instance du type définis, les éléments enfants du type complexe doivent être par défaut qualifiés ou non
        - si **unqualified** (le défaut), alors les noeuds enfants n'ont pas besoin d'être qualifiés
        - si **qualified**, les noeuds enfants doivent être qualifiés (sinon ils sont recherchés dans le domaine null, et 
          donc le plus souvent indéfinis)
    - il est possible pour chaque élément d'inverser à l'aide de l'attribut **form** (rarement utilisé)