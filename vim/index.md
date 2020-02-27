## VIM

### Racourcis

- **Ctrl+L** (ou `:redraw`)
- **K** affiche l'aide sur le mot-clé (avec `man`)

### Aide

- **:help**
- **Ctrl+]** permet de suivre un hyper-lien
  - il vaut mieux faire `set mouse=a` et utiliser le double-click
- **Ctrl+T** permet de revenir au sujet précédent  

### config
Le fichier de confif utilisateur **~/.vimrc** ou **~/.vim/vimrc** (plus de détails [Open vimrc file | Vim Tips Wiki](https://vim.fandom.com/wiki/Open_vimrc_file))


### indentation
Article très complet [Indenting source code | Vim Tips Wiki | FANDOM powered by Wikia](https://vim.fandom.com/wiki/Indenting_source_code)

#### indentation automatique
- **==** idente automatiquement la ligne courante
- **=3** indente la ligne courante et les deux suivantes
- **=G** indente automatiquement jusqu'à la fin du fichier
- **gg=G** pour indenter tout un fichier 

#### indentation manuelle

- **<<** et **>>** pour diminuer ou accroitre l'indentation
  - on peut indiquer le nombre de ligne avant **4>>** indevente les 4 lignes
- en mode insertion
   - **Ctrl+T** pour indenter, **Ctrl+D** pour désindenter
- en mode visuel par lignes (**V**)
   - **<** et **>**   pour indenter
   - **2<** et **2>** pour plusieurs degrés d'indentation

### naviguer

- **h**/**l** : car précédent/suivant
- **k**/**j** : ligne précédente/suivante
- **gg**/**G** : première/dernière ligne
- **<num>gg** : va à la ligne num
- **g\_** : dernier caractère utile de la ligne
- _n_**G** : aller à la ligne n
- **w**/**b**: début du mot suivant/précédent
  - mais aussi **W**/**B** pour des mots avec signe de ponctuation
- **ge**/**e****: début/fin du mot suivant
  - mais aussi **gE**/**E** pour les mots avec des signes de ponctuation
- **0**/**\$** : début de ligne/fin de ligne
- **f**_lettre_/**F**_lettre_ et **;**/**,** : occurence suivante/précédente de lettre (et repérer)
- **\*** / **#** : occurence suivante/dernière du mot courant

### défilement

- une ligne vers le haut **Ctrl+Y** / vers le bas **Ctrl+E**
- une page vers le haut **Ctrl+B** / vers le bas **Ctrl+F**
- Positionnement de la ligne courante
  - **zt** en haut
  - **zz** au milieu
  - **zb** en bas

### Visual mode

`!set mouse=a` - active la souris, pour entrer en mode visuel

### Shell

- **Ctrl+Z** ou **:su**spend puis `fg` : suspend VIM et revient au shell
- **:sh** démarre un nouveau shell. Quand il se termine, on revient à VIM
- **:!**_shell_ : exécute une commande du shell; puis revient à VIM
- **:r !**_shell_ : exécute une commande et insère le résultat dans le document

### copier/coller

- **v**/**V** : sélectionner caractères/lignes
- **d**/**y** : couper/copier la sélection
- **p**/**P** : coller la sélection (après le curseur, avant le curseur)

### Modifier

- **x**/**X** : supprimer suivant/précédent
- **d**_deplacement_ : supprime
  - **d$** ou **D** : supprime la fin de ligne
  - **d^** : supprime le début de ligne
  - **dw** : supprimer jusqu'à la fin du mot courant
  - **diw** : supprimer le mot courant
  - **dG** : supprime la fin du fichier
- **dd** : supprime la ligne courante

### Insert mode

- **i** / **a** (next char) / **A** (end of line) / **o** (next line)
- **c**_déplacement_ : remplace (change)
  - **c$** : remplace la fin de ligne
  - **c_** : remplace le début de la ligne
  - **cw** : remplace la fin du mot
  - **ciw** : remplace le mot courant
  - **cG** : remplace la fin du fichier
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
- **Ctrl+W **P** / **Ctrl+P** - fenêtre précédente

### Windows - dimensions

- **Ctrl+W** **=** : même hauteur à toutes les fenêtres
- **Ctrl+W** **\_** : hauteur max pour la fenêtre courante
- **z**_int_**C** : fixe la hauteur au nombre de ligne

### Windows - ouverture/fermeture

- **:n**ew <file> : ouvre le fichier dans une fenêtre
- **:sp**lit : ouvre une seconde fenêtre sur le même fichier
- **:vs**plit : ouvre une seconde fenêtre, verticale
- **:on**ly: ferme les autres fenêtres
- **:clo**se ou **Ctrl+wc**ferme la fenêtre active

### Onglets - 

- création
  - **:tabnew** crée un onglet vide
  - **:tabnew <file>** crée un onglet avec le fichier file
  - **:tabc** ferme l'onglet courant
- navigation
  - **gt** ou **gT** : va à l'onglet suivant/précédent
  - **2gt** : va à l'onglet 2

