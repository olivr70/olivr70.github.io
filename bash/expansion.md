


### Quotes

- quote ANSI C`$''`  
permet d'utiliser toutes les options de ANSI C, et en particulier ``r`, `\n`, `\t`, `\xHH`, `\uHHHH`; `\UHHHHHHHH`
  - Ex : `$'val1\tval2'`
  - voir [ANSI-C Quoting](https://www.gnu.org/software/bash/manual/html_node/ANSI_002dC-Quoting.html#ANSI_002dC-Quoting)


## Expansions 
Chaque commande fait l'objet d'une série d'expansions : 
brace expansion; tilde expansion, parameter and variable expansion, arithmetic expansion, and command substitution (done in a left-to-right fashion); word splitting; and filename expansion


### Expansion arithmétique

`$(( 2 + 3 ))` donne 5. A noter :

- On peut utiliser des nombres hexa, ou en base spécifique  
  - `echo $(( 0x20 ))` => *32*  
  - `echo $(( 2#100 ))` => *8*
- Pas besoin de $ pour utiliser une variable. Avec *x=3* :
  - `$(( x + 1))` => *4*
- Si une variable n'est pas un nombre, 0 est utilisé  
  - `x=A; echo $(( ++x ))` => *1*
- `++` et `--` permettent d'incrémenter ou décrémenter une variable  
  - `$(( ++x ))` =>  *4*, et désormais X vaut 4
- on peut faire des assignations, y compris avec une opération. `+=`, `*=`, `%=`, `<<=`, `&=` ... 
- on peut faire des comparaisons avec `==`, `<`, `<=`...
- on dispose de l'opérateur ternaire `? :`  
  - `echo $(( x % 2 ? +1 : -1 ))` => *1*
- la `,` permet d'enchainer plusieurs opérations, seul le dernier résultat est renvoyé  
 - `$(( ++x, x * 2 ))` => *8* (incrémente x, retourne le double)

Les opérations possibles sont [Shell Arithmetic (Bash Reference Manual)](https://www.gnu.org/software/bash/manual/html_node/Shell-Arithmetic.html#Shell-Arithmetic).

### substitution de process

`<( ls )` crée un fichier, dont le chemin est retourné. Lire ce fichier permet d'accéder au résultat de la commande
- `echo <(ls)` => */dev/fd/63*
- `cat <(ls)` => affiche le contenu du répertoire


### Appel de commande

`$(cmd)` exécute la commande, et insère le texte de la sortie standard.  
Le résultat de *cmd* est analysé (word splitting et substitution de noms de fichiers) 
Ex : 
- `wc $(cd ~; echo '*.sh')` affiche bien tous les fichiers du répertoire en cours
- `wc $(cd ~; echo *.sh)` produit la plupart du temps une erreur, car l'expansion de `*.sh` a lien lors de l'exécution de la sous-commande

Par contre `"$(cmd)"` le résultat de cmd est inséré tel quel (sans word splitting et analyse)  
Ex : `wc "$(echo a.sh b.sh")` échoue, car le fichier '*a.sh b.sh*' n'existe pas

### Découpage en mots

Le résultat de $1, de $VAR, $() est découpé en mots qui sont insérés dans la ligne de commande (utilisation de la variable IFS)

Ex  : avec `set -- 'file1.sh file2.sh'` :
- `echo "$1"` => * *.sh*
- `wc $1` => *294 1039 7877 file1.sh /  32  137 1184 file2.sh
 / 326 1176 9061 total*  
 *$1* a été expansé, et le résultat découpé en mots, chacun est devenu un paramètre

Ex : `wc $(find ./ -maxdepth 1 -type f)`  
*find* retourne un fichier par ligne, chaque saut de ligne est un séparateur de mots, et donc chaque fichier renvoyé est un argument positionnel pour *wc*

### Expansion de liste

Le shell interprète 
- `echo file{1,2,3}.txt` => *file1.txt file2.txt file3.txt*
- `echo dir/file{1..3}.txt` => *dir/file1.txt file2.txt file3.txt*
  - ATTENTION : utilisation de `..` et non `-` pour un intervalle

### Expansion de noms de fichiers

Si un mot comprend un *, ? ou [], alors l'expansion de fichiers est activée

Attention : une fois l'expansion effectuée, tous les fichiers qui correspondent
à un pattern fixé dans la variable **GLOBIGNORE** sont retirés

- `*` match toute série de caractère, sauf :
  - un `/`
  - un `.` en début de fichier. Donc `echo *` ne liste pas les
fichiers _.profile_, _.bashrc_ ...
- `[a-d]*.sh` tous les fichiers qui commencent pas a,b,c ou d
  - il y a toujours au moins un caractère, donc `[]]` est légal, et matche `]`
  - le `-` n'est pas interpreté en début et fin de liste, donc `[-+]` est légal
       et match **+** ou **-**
  - **ATTENTION** : fonctionnement différent de l'expansion de liste  `{a..d}.sh` ne tient pas compte des fichiers effectivement présents (et donne toujours le même résultat)  
  l'expansion de liste intervient avant, et chaque item subira l'expension de fichier 
  Ex : `ls {a..c}*.sh` est équivalent à `ls a*.sh b*.sh c*.sh`
- `?(a|d)` - occurence optionnelle d'une des branches  
- `*(ab|cd)` - 0 ou plusieurs occurences de l'une des branches
  `*.sh.*(.bak)` - fichiers *.sh* ou *.sh.bak*
- `+(ab|cd)` - 1 ou plusieurs occurences de l'une des branches
  - ex : `ls +(a|d)*` - tous les fichiers qui commencent par *a* ou *d* 
- `@()` - exactement 1 des altenatives  
- `!()` - match tout sauf un des pattern
  - `ls !(*.jpg)` - tous les fichiers sauf les .jpg

PLus de détails sur [Pattern Matching (Bash Reference Manual)](https://www.gnu.org/software/bash/manual/html_node/Pattern-Matching.html#Pattern-Matching) et sur 
[Patterns and pattern matching [Bash Hackers Wiki]](https://wiki.bash-hackers.org/syntax/pattern)

Suivant les options de [`shopt`](https://www.gnu.org/software/bash/manual/html_node/The-Shopt-Builtin.html), si aucun fichier n'est trouvé pour un pattern, les résultats sont différents (pour mémoire `shopt` affiche les options, et `shopt -s` et `shopt -u` permettent de 
les activer ou désactiver)
- avec *failglob*, une erreur est générée
- avec *nullglob*, un mot vide est généré
- sinon, **le pattern est laissé tel quel**
  - donc `echo *.jpg` produit `*.jpg`

Certaines options sont actives par défaut :
- avec *extglob* 
D'autres options permettent de controler l'expansion
- avec *nocaseglob*, les patterns ignorent la casse
- avec *dotglob*, * 