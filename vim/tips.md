## VIM
### naviguer
- __h__/__l__ : car précédent/suivant
- __k__/__l__ : ligne précédente/suivante
- __gg__/__G__ : première/dernière ligne
- **g_** : dernier caractère utile de la ligne
- _n_**G** : aller à la ligne n
- **w**/**b**: début du mot suivant/précédent
- __??___e__: début/fin du mot suivant
- __0__/__$__ : début de ligne/fin de ligne
- __f__*lettre*/__F__*lettre* et **;**/**,** : occurence suivante/précédente de lettre (et repérer)
- __*__/__#__ : occurence suivante/dernière du mot courant
 
### Shell
- **Ctrl+Z** ou **:su__end**  puis **fg** : suspend VIM et revient au shell
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
  - **d$** : supprime la fin de ligne
- **dd** : supprime la ligne courante
 
### Insert mode
- **i** / **a** / **A** (end of line) / **o** (next line)
- **c**<e/w/$> efface jusqu'à la marque (e ou w : fin du mot; $ fin de ligne) et passe en insertion
- **Ctrl+P** : autocomplétion
- **Ctrl+X** **Ctrm+F** : autocomplétion de fichier
- **Ctrl+X** **Ctrl+L** : autocomplétion de lignes (y compris à partir d'autres fichiers ouverts)

 
### Chercher **/**
- **/**_A_ cherche la prochaine occurence de A
- **/**_A_**/**e** cherche A et met le curseur sur le dernier car
- **/**_A_**/e+1** idem, curseur après le dernier car
- **/**_A_**/b+1** idem, curseur sur le second caractère
 
### Remplacer **:s**
- **:s/**_A_**/**_B_**/** remplace la prochaine occurence de A
- **:s/**_A_**/**_B_**/g** remplace tous les A sur la ligne courante
- **:%s/**_A_**/**_B_**/g** remplace tous les A dans tout le fichier
- **:%s/**_A_**/**_B_**/gc** remplace tous les A, avec confirmation
 
### Marks
- '<a-z> : va à la marque dans le ficheir
- '' : retourne à la position du curseur avant le dernier saut vers une marque
- m<a-z> ou :mark <a-z> : crée une marque dans le fichier
- m<A-Z> ou :mark <A-Z>: crée une marque de fichier

### Windows - navigation
- **Ctrl**+**+**/**-** Zoom in/Zoom out
- **Ctrl+W** **up**/**down**/**left**/**down** ( changer le focus )
- **Ctrl+W** **Ctrl+W** - cycler entre les fenêtres
- **Ctrl+W **P**/**Ctrl+P** - fenêtre précédente

### Windows - dimensions
- **Ctrl+W** **=** :  même hauteur à toutes les fenêtres
- **Ctrl+W** **_** : hauteur max pour la fenêtre courante
- **z**_int_**C** : fixe la hauteur au nombre de ligne


### Windows - ouverture/fermeture
- **:new** <file> : ouvre le fichier dans une fenêtre
- **:split** : ouvre une seconde fenêtre sur le même fichier
- **:vsplit** : ouvre une seconde fenêtre, verticale
- **:only**: ferme les autres fenêtres
- **:close** ferme une fenêtre
