
## les paramètres d'un script

`$0` à `$9` pour les premiers, `${10}` au delà

`$#` pour le nombre de paramètres

`$@` pour tous les paramètres

`set` pour fixer les paramètres. Ex : `set $(ls)`

## la substitution de variables

### Valeurs par défaut
- `${VAR:-def}` 
- `${VAR:?}` ou `${VAR:?Missing}` => message sur STANDARD ERR

### Changement de casse
avec V qui contient `New-York`
- `${V^^}` => NEW-YORK
- `${V,,}` => new-york

### Sous-chaine d'une variable
avec V qui contient `1,2,3,4`
- `${V:2}` => `2,3,4`
- `${V:2:2}` => `2,`
- `${V:2:-2}` => `2,3`

### suppresion d'un préfixe : ${VAR#} et ${VAR##} 

avec V qui contient `1,2,3,4`
- `${V#*,}` => `2,3,4` - supprime le plus court préfixe 
- `${V##*,}` => `4` - supprime le plus long préfixe 

### Suppression d'un suffixe : ${VAR%} et ${VAR%%} 
avec V qui contient `1,2,3,4`
- `${V%,*}` => `1,2,3` - supprime le plus court préfixe 
- `${V%%,*}` => `1` - supprime le plus long préfixe 

### Remplacement : ${VAR/target/repl}
avec V qui contient `1,2,3,4`
- `${V/1/A}` => `A,2,3,4` remplace la première occurence
- `${V//[0-9]/A` => `A,A,A,A` remplace toutes les occurences

## Tableaux

`T=(un deux trois)`

`echo ${T[0]}` => `un`  mais `echo $T` => `un` et `echo $T[0]` => `un[0]`

`echo ${T[*]}` => `un deux trois`

`echo ${#T[*]}` => `3`

`for m in ${tab[@]}; do echo $m; done` => `un/deux/trois`


`echo ${!T[*]}` ou `echo ${!T[@]}` => `0 1 2`

## Cas particuliers

### Liste des variables

`echo ${!U*}` => `USER UID`