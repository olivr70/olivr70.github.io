
## Jeux de caractères

## [`file`](http://manpages.ubuntu.com/manpages/bionic/man1/file.1.html)
Permet notamment de déterminer les types de fin de ligne d'un fichier

Utile aussi pour savoir si on a bien mis le marquet Bash : `file *.sh`

## [`iconv`](https://doc.ubuntu-fr.org/iconv)
Pour convertir le jeu de caractère d'un fichier

## [`sort` - sort lines of text files](http://manpages.ubuntu.com/manpages/bionic/man1/sort.1.html)

`sort`
- `-k2` tri sur le second champ
- `-t,` utilise **,** comme séparateur de champ
- `-r,` en ordre inverse

ATTENTION : tri ne permet pas de distinguer une ligne d'entête. Plusieurs solutions :
- `head -n 1 afile && tail -n +2 afile | sort `. 
  - concatène
    - `head -n 1 afile` - la première ligne
    - `tail -n +2 afile | sort` - les lignes suivantes, triées


## Nettoyage de texte

### [cut](https://linux.die.net/man/1/cut) - remove sections from each line of files
- `cut -f 2,4 -d "/"` - le 2e et le 4e item de chaque ligne

#### [`tr`](https://linux.die.net/man/1/tr) translate/delete char
- `tr "ab" "AB"` - remplace a par A et b par B 
- `tr [a-z] [A-Z]` - remplace les minuscules simples par des majuscules
- `tr -d "[:cntrl:]"` - supprime tous les caractères de controle
- `tr -s "[:alpha:]"` - supprime toutes les lettres qui se repétent

### [`uconv` - convert data from one encoding to another](http://manpages.ubuntu.com/manpages/bionic/man1/uconv.1.html)

Extrêmement puissant par l'utilisation des translitérations Unicode
- `uconv -x Upper` pour convertir en majuscules ("Bébé" => "BÉBÉ")
- `uconv -x Hex` pour convertir en hexadécimal ("B" => "\u0042")
- `uconv -x Name` pour obtenir le nom des caractères ("B" -> "\N{LATIN CAPITAL LETTER B}"
- `uconv -x any-NFKD` pour obtenir la décomposition  
Ex : `echo "ê" | uconv -x "any-NKFD; name"` => *\N{LATIN SMALL LETTER E}\N{COMBINING CIRCUMFLEX ACCENT}*

Il semble y avoir deux syntaxes de translitérations:
- `uconv -x ''::nfkd; ::name;'`
Dans la syntaxe avec `::`, on peut créer des remplacements avec `>`
- `uconv -x "B > b"` remplace B par b
- `uconv -x "[:Mn:] >` supprime tous les non-spacing marks

Les translitérations peuvent être chaînées
- `any-NKFD; Name`

Les translitérations peuvent être filtrées
- `[aeiouy] remove` supprime toutes les voyelles
- `[\p{Ll}] name` en utilisant les [catégories Unicode](https://en.wikipedia.org/wiki/Unicode_character_property). Les principales (voir [Unicode](../formats/unicode))
  - *L* lettres, *Ll* minuscules, *Lu* majudscules...
  - *Mn" marque non-spacing, *Mc* marque combining, *Me* marque enclosing
  - *N* number, *Nd* decimal digit, *Nl* number letter, *No* Number others
  - *C* control, *C



### [`sed`](https://linux.die.net/man/1/sed) text stream editor


### [Jq](http://mikefarah.github.io/yq/read/) JSON parser

### [Yq](http://mikefarah.github.io/yq/read/) Yaml parser
#### Commandes
Lit un fichier YAML, produit un fichier YAML ou JSON
Commandes (qui produisent un nouveau YAML)
- `r` selection de certaines clés. 
- `w` modifie certaines clés.
- `p` préfixe toutes les clés
- `n` crée de nouvelles clés
- `d` supprime certaines clés
- `m` fusion de plusieurs documents (les clés présentes ne sont pas modifiées)  
  - `-x` pour écraser les anciennes valeurs par les nouvelles
  - `-a` pour que les champs tableaus soient fusionnés et non remplacés.  
    `-x` et `-a` ne peuvent pas être utilisées ensembles

#### Options:
- `-dN` choix du document
- `-j` produit du json

#### Exemples
- `cat file.yaml | yq r - bob.item*.name` 
- `yq r some.json` convertit un fichier JSON en YAML
- `yq r -j some.yaml` convertit un fichier YAML en JSON


