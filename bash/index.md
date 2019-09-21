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
