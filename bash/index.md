All about Bash

En savoir plus sur 
- les [Variables](./variables)
- l'[history](./history)

## Tips

### Racourcis claviers
#### déplacer le curseur
- **Ctrl**-**A** : début de ligne
- **Ctrl**-**E** : fin de ligne
- **Alt**-**F** / **Ctrl**-**F**: mot suivant / caractère suivant
- **Alt**-**B** / **Ctrl**-**B** : mot précédent

#### Copier et coller
- **Ctrl**-**Y** : coller le texte
- **Ctrl**-**U** : couper le texte entre le début de le ligne et le curseur
- **Ctrl**-**K** : couper le texte entre le curseur et la fin de ligne
- **Ctrl**-**W** : ajouter le mot précédent au presse-papier 

### [`tput`(1) - Linux man page](https://linux.die.net/man/1/tput)
A utiliser en lien avec :
- `echo $TERM` => nom du terminal (ex : xterm-256color)
- `infocmp` => affiche les séquences reconnues par le terminal courant

#### Les commandes
- `tput` 
  - `sgr0` reset
  - `bold`, `rev`
  - `smul` et `emul` - début et fin de soulignement
  - `smso` et `emuso` - début et fin de standout (inversé)
  - `setaf 1` - fixe la couleur du texte (foreground)
  - `setab 1` - fixe la couleur de fond (background)

#### Les couleurs (pour `setaf` et `setab`)
- `0` 	Black
- `1` 	Red
- `2` 	Green
- `3` 	Yellow
- `4` 	Blue
- `5` 	Magenta
- `6` 	Cyan
- `7` 	White
- `8` 	Not used
- `9` 	Reset to default color

### 


### heredoc

```bash 
cat <<LIMIT
some text
LIMIT
```

Il y a aussi :
* ```cat <<-``` pour supprimer les tabs initiaux
* ```cat << "LIMIT"``` pour éviter la substitution de variables dans le text

## Articles

* [Here Documents](http://tldp.org/LDP/abs/html/here-docs.html)
* [Bash One-Liners Explained, Part III: All about redirections](https://catonmat.net/bash-one-liners-explained-part-three)
