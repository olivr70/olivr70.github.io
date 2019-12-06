
## alternatives

la plupart des exécutables dans /usr/bin sont en fait des liens vers 
/usr/bin/alternatives

La commande `update-alternatives` permet de lister et modifier l'alternative
utilisée pour un programme. Quelques exemples :
- *editor* editeur texte
- *ftp*
- *www-browser* navigateur texte
- *x-www-browser* navigateur graphique

`sudo update-alternatives --config editor` pour choisir interactivement l'éditeur

`update-alternatives --get-selections` pour faire la liste
