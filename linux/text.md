
### Nettoyage de texte

### [cut](https://linux.die.net/man/1/cut) - remove sections from each line of files
- `cut -f 2,4 -d "/"` - le 2e et le 4e item de chaque ligne

#### [`tr`](https://linux.die.net/man/1/tr) translate/delete char
- `tr "ab" "AB"` - remplace a par A et b par B 
- `tr -d "[:cntrl:]"` - supprime tous les caractères de controle
- `tr -s "[:alpha:]"` - supprime toutes les lettres qui se repétent


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


