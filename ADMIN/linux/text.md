## [printf]()

La chaine de format est celle de la fonction C [printf](http://manpages.ubuntu.com/manpages/bionic/man3/printf.3.html)

la commande Bash printf supporte aussi : 
- `%q` qui insère les séquences d'échappement pour que l'argument soit considéré  
comme un seul mot Bash (utile pour générer une commande)
  - `printf "%q" "A B` => *A\ B*
- `%b` remplace les séquences \ par leur équivalent dans l'argument (ex : \t \n)
  - `printf "%b" "\u0042` => *B*


## Tri et alphabets

Les locales sont dans **/usr/share/i18n/locales**.

Pour installer les locales d'une langue, `sudo apt-get -y install language-pack-XX`

Sur touls les systèmes, on trouve les locales **C** et **POSIX**.


`locale -a` affiche les locales disponibles, et `locale -av` affiche les
détails pour chacune d'elle


Pour déterminer la locale à utiliser, le système examine dans l'ordre
- **LC_ALL** - si elle est fixée, c'est elle qui est utilisée  
On l'utilise en général avant de lancer une commande pour forcer la locale
- la catégorie concernée
  - **LC_CTYPE** - Character classification
  - **LC_NUMERIC** - Formatting of nonmonetary numeric values
  - **LC_TIME** - Formatting of date and time values
  - **LC_COLLATE** - String collation
  - **LC_MONETARY** - Formatting of monetary values
  - **LC_MESSAGES** (POSIX) - Localizable natural-language messages
  - **LC_PAPER** (GNU) - Settings related to the standard paper size
  - **LC_NAME** (GNU)- Formatting of salutations for persons 
  - **LC_ADDRESS** (GNU) - Formatting of addresses and geography-related items 
  - **LC_TELEPHONE** (GNU)- Formats to be used with telephone services
  - **LC_MEASUREMENT** (GNU)- Settings related to measurements (metric versus US customary)
  - **LC_IDENTIFICATION** (GNU)- Metadata describing the locale
- **LANG** - valeur par défaut


la commande `locale` affiche la valeur de chacune des catégories

la commande `locale -k LC_TELEPHONE` affiche tous les variables de la catégorie
(`-k` pour afficher aussi les noms, sinon on a que les valeurs)

la commande `locale yesexpr` (=> **^[+1oOyY]**) affiche la valeur d'une variable 
pour la locale courante. Quelques variables utiles : 
- LC_IDENTIFICATION : **territory**, **tile**
- LC_MESSAGES : **yesstr** et **nostr**, **yesexpr** et **noexpr**
- LC_NUMERIC : **decimal_point**, **thousands_sep**, **grouping**
- LC_TIME : **day** le nom des jours, **mon** le nom des mois, **d_fmt** le format de date,  
**first_weekday**...
- LC_MONETARY : **currency_symbol**  




## Jeux de caractères

## [`file`](http://manpages.ubuntu.com/manpages/bionic/man1/file.1.html)
Permet notamment de déterminer les types de fin de ligne d'un fichier

Utile aussi pour savoir si on a bien mis la marque Bash : `file *.sh`

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

### rev
inverse l'ordre des caractères sur chaque ligne.

ATTENTION : si le texte unicode est en forme décomposée, alors
les marques combinantes ne seront plus associées au bon caractère


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
- `uconv -x Hex` pour convertir en hexadécimal (*"B"* => *"\u0042"*)
- `uconv -x Hex-any` pour convertir depuis hexadécimal (*"\u0042"* => *"B"* )
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
- `[\p{Ll}] name` en utilisant les [catégories Unicode](https://en.wikipedia.org/wiki/Unicode_character_property). Les principales (voir [Unicode](unicode.md))
  - *L* lettres, *Ll* minuscules, *Lu* majudscules...
  - *Mn" marque non-spacing, *Mc* marque combining, *Me* marque enclosing
  - *N* number, *Nd* decimal digit, *Nl* number letter, *No* Number others
  - *C* control



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


