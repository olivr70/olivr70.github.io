
## [Shebang](https://en.wikipedia.org/wiki/Shebang_(Unix))

La séquence **#!** en début de fichier est interprété par exec pour déterminer
l'interpréteur à utiliser.

Il doit être suivi du chemin absolu vers l'interpréteur. On peut utiliser
**/usr/bin/env** avec comme premier argument le nom de l'interpréteur  
Ex : `#!/usr/bin/env node`

## Commandes Linux diverses

Diverses commandes Linux
### [type](https://www.gnu.org/savannah-checkouts/gnu/bash/manual/bash.html#Bash-Builtins) 
- `type -a` pour voir toutes les possibilités
- `type -t` pour avoir juste le type



## [`watch`](https://linux.die.net/man/1/watch) exécute périodiquement une commane

- `-n <seconds>` fixe l'intervalle
- `-d` met en valeur les différences à chaque itération

## [`xdg-open`](https://linux.die.net/man/1/xdg-open) affiche une URL avec le navigateur

## [`ncal`](https://manpages.ubuntu.com/manpages/cosmic/man1/cal.1.html)
`ncal 03 2019` calendrier de mars 2019
- `-3` affiche 3 mois
- `-b` calendrier une semaine par ligne (par défaut tous les jours par ligne)


## [`who`](https://linux.die.net/man/1/who) : who is logged on

`-r` affiche le runlevel

## changer de terminal

Linux exécute plusieurs terminaux (**tty1** à **tty7**). **tty7** est la 
session de démmarrage.Pour passer de l'un à l'autre :
- `sudo chvt <n>` ( [chvt](http://www.man7.org/linux/man-pages/man1/chvt.1.html) - **CH**ange **V**irtual **T**erminal )
- **Ctrl**+**Alt**+**F1** à **F7**


## pwgen
un outil pout générer des mots de passe `pwgen 10 1` génère un mot de passe de 10 caractères

# mkpasswd
un outil pour encrypter un mot de passe.
`mkpasswd --method=sha-512 --rounds=4096` demande le mot de passe

On peut aussi utiliser `pass`
`mkpasswd --method=sha-512 --rounds=4096 $(pass show app/pass)`

## John the ripper
un outil pour cracker les mots de passe linux. 

Voir cet [John The Ripper - Comment cracker un mot de passe sous Linux ? - www.octetmalin.net](http://www.octetmalin.net/linux/tutoriels/john-the-ripper.php)


