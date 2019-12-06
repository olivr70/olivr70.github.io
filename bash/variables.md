

## les paramètres d'un script

`$0` à `$9` pour les premiers, `${10}` au delà

`$#` pour le nombre de paramètres

`$@` pour tous les paramètres

`set` pour fixer les paramètres. Ex : `set $(ls)`

## la substitution de variables

Voir [How To Use Bash Parameter Substitution Like A Pro - nixCraft](https://www.cyberciti.biz/tips/bash-shell-parameter-substitution-2.html) et [Shell Parameter Expansion (Bash Reference Manual)](https://www.gnu.org/software/bash/manual/html_node/Shell-Parameter-Expansion.html#Shell-Parameter-Expansion)

### Valeurs par défaut
- `${VAR:-def}` def si VAR n'existe pas, ou si VAR est vide
- `${VAR-def}` def si VAR n'existe pas
- `${VAR:?}` ou `${VAR:?Missing}` => message sur STANDARD ERR

### Assignation par défaut
- `${VAR:=def}` VAR vaut def, si VAR n'existe pas, ou si VAR est vide
- `${VAR=def}` VAR vaut def, def si VAR n'existe pas

### Remplacement si la variable est défini
- `${VAR:+repl}` repl si VAR existe et VAR est non vide
- `${VAR+repl}` repl si VAR n'existe pas et VAR est vide

| opération |  X indéfini | vide X= | X=A
| --- | ---- | ---- | -----
| ${X:-B} | B | B | A
| ${X-B} | B | NULL | A
| ${X:+B} | NULL | NULL | B
| ${X+B} | NULL | B | B



### Changement de casse
avec V qui contient `New-York`
- `${V^^}` => *NEW-YORK*
- `${V,,}` => *new-york*

### Sous-chaine d'une variable
avec V qui contient `1,2,3,4`
- `${V:2}` => *2,3,4*
- `${V:2:2}` => *2,*
- `${V:2:-2}` => *2,3*

### suppresion d'un préfixe : ${VAR#} et ${VAR##} 

avec V qui contient `1,2,3,4`
- `${V#*,}` => *2,3,4* - supprime le plus court préfixe 
- `${V##*,}` => *4* - supprime le plus long préfixe 

### Suppression d'un suffixe : ${VAR%} et ${VAR%%} 
avec V qui contient `1,2,3,4`
- `${V%,*}` => *1,2,3* - supprime le plus court préfixe 
- `${V%%,*}` => *1* - supprime le plus long préfixe 

### Remplacement : ${VAR/target/repl}
avec V qui contient `1,2,3,4`
- `${V/1/A}` => `A,2,3,4` remplace la première occurence
- `${V//[0-9]/A` => `A,A,A,A` remplace toutes les occurences

## Tableaux
**les tableaux sont indexés à partir de 0**

avec `T=(un deux trois quatre cinq)`
- un item  
`echo ${T[0]}` => *un*  
  - mais `echo $T` => *un*
  - mais attention au piège `echo $T[0]` => *un[0]*
- tous les items  
`echo ${T[*]}` => *un deux trois quatre cinq*
- nombre d'items 
`echo ${#T[*]}` => `3`  
ATTENTION  : un tableau bash peut être clairsemé  
`T[10]=dix ; echo ${#T[@]}` => *1*
- indices des slots qui sont assignés  
`echo ${!T[*]}` ou `echo ${!T[@]}` => *0 1 2 4 5*
- un intervalle d'items  
`echo ${T[@]:2:2}` => `trois quatre`
  - MAIS ATTENTION `${T:1:2}` => *n* (sous-chaine de l'item 0)
- les n derniers items (tail)  
` echo ${T[@]: -2}` => *quatre cinq*

## Paramètres
Attention : les paramètres sont indexés à partir de 1
avec `set -- un deux trois quatre`

- tous les paramètres  
`echo $@` => *un deux trois quatre*
- le premier paramètre  
`echo ${@:1}` => *un*
- le dernier paramètre  
`echo ${@: -1}` => *quatre*
- un intervalle de paramètres  
`echo ${@: 2:2}` => *deux trois*

`for m in ${tab[@]}; do echo $m; done` => *un/deux/trois*




## Cas particuliers

### Liste des variables

`echo ${!U*}` => `USER UID`