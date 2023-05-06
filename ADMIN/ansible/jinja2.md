Ansible utilise Jinja2 qui offre de très nombreuses possiblités de mise
en forme

Toute la doc : [Template Designer Documentation — Jinja Documentation (2.10.x)](https://jinja.palletsprojects.com/en/2.10.x/templates/#expressions)

## les valeurs

### les opérateurs
- math
  - `+`, `-`, `*`, `/`
  - `//` division entière
  - `**` puissance
- texte
  `~` concaténation (ex : `"hello" ~ " " ~ "world"`)  
- comparaison
  - `is` (ex : `2 is even`)
  - `<`,`<=`...
  - `and`, `or`, `not` 
  - `in` (ex : `1 in [1,2,3]` => true)

## les filtres [doc](https://jinja.palletsprojects.com/en/2.10.x/templates/#list-of-builtin-filters)

Voir également : [Filters — Ansible Documentation](https://docs.ansible.com/ansible/latest/user_guide/playbooks_filters.html#defaulting-undefined-variables)

- sur des valeurs
  - `lower`, `upper`
  - `default('?')`
    - remplace une valeur *undefined*. Pour remplacer aussi une chaine vide, il faut
      passer true en second argument (par exemple après un lookup)  
      `"{{ lookup('env', 'SSH_USER') | default('foo', true) }}"`
  -  `int`, `float` - conversion
  - `trim`
  - `truncate`
  - `wordwrap`
  - `b62encode` et `b64decode` (non documenté)
- générer une valeur à partir d'une liste
  - `join(<sep>)`
  - `first`, `last`
  - `max`, `min`
  - `sum`
- modifier une liste
  - `unique`
  - `sort`
  - `select`, `reject` pour filtrer
  - `map(atribute='name')` - ne garde que l'attribut name d'une liste d'objet
  - `map('upper')` - applique le filtre à chaque item
- sur des objets
  - `to_json`  

## les tests

Plusieurs fonctions de test sont prédéfinies, pour utiliser en particulier
avec les filtres `select`, `reject`, mais aussi dans les tests (`if x is <test>`)
, les boucles for
- `even`,`odd`, `divisibleby`
- `undefined`, `number`, `string`
- `iterable` : une valeur itérable
- `mapping` : une table d'association
- `lower`,`upper`