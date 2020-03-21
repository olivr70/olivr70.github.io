

## `pushd`, `popd` et `dirs`

Gèrent une pile de chemins vers des répertoires.  le répertoire courant (`pwd`,
**$PWD**) correspond toujours au haut de la pile

Le tableau **DIRSTACK** contient la pile. Donc: 
- **$DIRSTACK**, ou **${DIRSTACK[0]}** contient le répertoire courant 
- **${DIRSTACK[-1]}** le bas de la pile 
- **${#DIRSTACK[@]}** (avec #) le nombre d'items
- **${DIRSTACK[@]}** tous les items

L'expansion tilde avec un chiffre permet d'obtenir la valeur d'un répertoire (voir [expansion bash]()./expansion) )
- `~0` ou `~+0` est remplacé par le haut de la pile (donc le répertoire courant)
- `~-0` est remplacé par le bas de la pile

`pushd` 
- `pushd DIR` ajoute le **dossier courant** sur la pile, PUIS change répertoire courant à DIR
- `pushd +n` le dossier ~n devient le répertoire courant, les dossiers au dessus  
dans la pile sont réinsérés par le bas  
Ex  ! **dir4 dir3 dir2 dir1** puis  `pushd +2`, la pile devient **dir2 dir1 dir4 dir3**


`dirs` affiche la pile (le haut à gauche) :
- `dirs -p` avec 1 dossier par ligne
- `dirs -v` avec le numéro (utilisable avec l'expansion ~1)
- `dirs +n` retourne le chemin 
  - `dirs +0` affiche le dossier en haut de la pile
- `dirs -n` retourne le chemin à partir du dernier
  - `dirs -0` affiche le dossier en bas de la pile
- `dirs -c` vide la pile de dossier

`popd`
- retire le haut de la pile, qui devient le répertoire courant
- `popd +n` retire le dossier **n**
  - `popd +0` équivalent à popd
- `popd -n` retire le dossier à partir de la fin
   `popd -0` retire le bas de la pilce