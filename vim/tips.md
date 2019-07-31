## VIM

### naviguer

- **h**/**l** : car précédent/suivant
- **k**/**l** : ligne précédente/suivante
- **gg**/**G** : première/dernière ligne
- **g\_** : dernier caractère utile de la ligne
- _n_**G** : aller à la ligne n
- **w**/**b**: début du mot suivant/précédent
- **??\_**e\_\_: début/fin du mot suivant
- **0**/**\$** : début de ligne/fin de ligne
- **f**_lettre_/**F**_lettre_ et **;**/**,** : occurence suivante/précédente de lettre (et repérer)
- **\***/**#** : occurence suivante/dernière du mot courant

### Visual mode

`!set mouse=a` - active la souris, pour entrer en mode visuel

### Shell

- **Ctrl+Z** ou **:su**spend puis \*\*fg\*\* : suspend VIM et revient au shell
- **:!**_shell_ : exécute une commande du shell; puis revient à VIM
- **:r !**_shell_ : exécute une commande et insère le résultat dans le document

### copier/coller

- **v**/**V** : sélectionner caractères/lignes
- **d**/**y** : couper/copier la sélection
- **p**/**P** : coller la sélection (après le curseur, avant le curseur)

### Modifier

- **x**/**X** : supprimer suivant/précédent
- **d**_deplacement_ : supprime
  - **dG** : supprime la fin du fichier
  - **d\$** : supprime la fin de ligne
- **dd** : supprime la ligne courante

### Insert mode

- **i** / **a** / **A** (end of line) / **o** (next line)
- **c**_e/w/\$_ efface jusqu'à la marque (e ou w : fin du mot; \$ fin de ligne) et passe en insertion
- **Ctrl+P** : autocomplétion
- **Ctrl+X** **Ctrm+F** : autocomplétion de fichier
- **Ctrl+X** **Ctrl+L** : autocomplétion de lignes (y compris à partir d'autres fichiers ouverts)

### Chercher **/**

- **/**_A_ cherche la prochaine occurence de A
- **/**_A_**/**e\*\* cherche A et met le curseur sur le dernier car
- **/**_A_**/e+1** idem, curseur après le dernier car
- **/**_A_**/b+1** idem, curseur sur le second caractère

### Remplacer **:s**

- **:s/**_A_**/**_B_**/** remplace la prochaine occurence de A
- **:s/**_A_**/**_B_**/g** remplace tous les A sur la ligne courante
- **:%s/**_A_**/**_B_**/g** remplace tous les A dans tout le fichier
- **:%s/**_A_**/**_B_**/gc** remplace tous les A, avec confirmation

### Marks

- **'**_a-z_ : va à la marque dans le ficheir
- **''** : retourne à la position du curseur avant le dernier saut vers une marque
- **m**_a-z_ ou **:mark** _a-z_ : crée une marque dans le fichier
- **m**_A-Z_ ou **:mark** _A-Z_ : crée une marque de fichier

### Windows - navigation

- **Ctrl**+**+**/**-** Zoom in/Zoom out
- **Ctrl+W** **up**/**down**/**left**/**down** ( changer le focus )
- **Ctrl+W** **Ctrl+W** - cycler entre les fenêtres
- **Ctrl+W **P**/**Ctrl+P\*\* - fenêtre précédente

### Windows - dimensions

- **Ctrl+W** **=** : même hauteur à toutes les fenêtres
- **Ctrl+W** **\_** : hauteur max pour la fenêtre courante
- **z**_int_**C** : fixe la hauteur au nombre de ligne

### Windows - ouverture/fermeture

- **:n**ew <file> : ouvre le fichier dans une fenêtre
- **:sp**lit : ouvre une seconde fenêtre sur le même fichier
- **:vs**plit : ouvre une seconde fenêtre, verticale
- **:on**ly: ferme les autres fenêtres
- **:cl**ose ferme une fenêtre
