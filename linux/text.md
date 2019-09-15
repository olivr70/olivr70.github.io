
### Nettoyage de texte

### [cut](https://linux.die.net/man/1/cut) - remove sections from each line of files
- `cut -f 2,4 -d "/"` - le 2e et le 4e item de chaque ligne

#### [`tr`](https://linux.die.net/man/1/tr) translate/delete char
- `tr "ab" "AB"` - remplace a par A et b par B 
- `tr -d "[:cntrl:]"` - supprime tous les caractères de controle
- `tr -s "[:alpha:]"` - supprime toutes les lettres qui se repétent


### [`sed](https://linux.die.net/man/1/sed) text stream editor


