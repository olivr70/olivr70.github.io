
## utilisateurs

la commande `id` permet d'afficher des infos sur un utilisateur ou l'utilisateur courant
- `id -u` => 1000 et `id -un` => _olivr70_
- `id -g` => 1000 et `id -gn` => _olivr70_
- `id -G` => _1000 24 27..._ et `id -Gn postgres` => _postgres ssl-cert_

le bit `setuid` sur un fichier exécutable permettent à celui qui invoque de le faire
avec les droits du propriétaire. De même le bit `setgid` avec le groupe propriétaire.
Pour modifier : 
- `chmod u+s myscript.sh` et `chmod g+s myscript.sh`


## [sudo](http://manpages.ubuntu.com/manpages/xenial/man8/sudo.8.html)

Configuration:
le fichier */etc/sudo.conf* permet de paramétrer :
- les plugins (par défaut sudoers)
- l'application askpass pour demander le mot de passe (*askpass*)  
et ne celle pour le pas exécuter (*noexec*)
- mettre certains exécutables en mode debug

### logs
par défaut, sudo écrit dans */var/log/auth.log*

Options:
- `-u` utilisateur dont on prend la personnalité
- `-g` groupe dont on prend la personnalité
- `-E` pour préserver les variables d'environnement
- `-b` en mode background
-  `-e` pour éditer un fichier (éditeur : SUDO_EDITOR, VISUAL, EDITOR)

`sudo -l` permet de voir les privilèges sudo pour l'utilisateur en cours

la commande [`sudo`](http://manpages.ubuntu.com/manpages/xenial/man8/sudo.8.html) peut être paramétrée par le plugin `sudoers`

`sudo visudo` permet d'éditer le fichier de config */etc/sudoers* ou les 
fichiers du dossier */etc/sudoers.d*, qui par défaut sont inclus par sudoers

### [`sudoers`](http://manpages.ubuntu.com/manpages/bionic/man5/sudoers.5.html)

Configuration dans le fichier */etc/sudoers* et dans les fichiers */etc/sudoers.d*

Format de chaque ligne : `user       host = (user) command`
Ex :
- `ALL ALL = ALL`  
Tous les utilisateurs autorisés à utiliser sudo peuvent exécuter toutes les commandes
- `john webserver = (webadmin) reboot`

On peut créer des alias
- `Host_Alias      LAN = mario.host.com, lucy.host.com`  
On peut utiliser LAN à la place de *host* : `john LAN = ALL`
- `User_Alias        WEBADMIN = ankit, sam`  
On peut utiliser WEBADMIN à la place de *user* : WEBADMIN webserver = reboot  
ankit et sam peuvent redémarrer le serveur web
- `Cmnd_Alias         SU = /bin/su`
On peut utiliser SU à la place de *command*  : john webserver = SU

## Articles

[Configuring sudo: Explaination with an example - Linux.com](https://www.linux.com/tutorials/configuring-sudo-explaination-example/)

