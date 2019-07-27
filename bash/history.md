## Bash History

### Insertion dans l'history

ignore une ligne commençant par `<space>`

ignore les commandes déjà présentes

`history -c` - efface l'historique de session

### Navigation

`Up`/`Down` - commande préc/suiv

`Ctrl+R` - recherche dans l'history

### Expansion

`!!` - la dernière commande

ex : `sudo !!` - exécute la dernière commande avec sudo

ex : `!! | grep "??"` - filtre la dernière commande

`!n` - la commande n (

`!-n` - la commande antérieure

(`!n`/`!!`/`!-n`)`:p` affiche la commande

## Expansion des arguments

- `!$` le dernier argument de la précédente commande
- `!*` tous les arguments de la précédente commande
- `!^` le premier argument de la commande précédente

**\$HISTFILE** - le fichier d'historique

**\$HISTSIZE** - la taille de l'historique
