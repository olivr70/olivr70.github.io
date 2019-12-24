## [`ssh`](https://linux.die.net/man/1/ssh)

### se connecter en SSH à une machine distante

`ssh user@hostname` permet de se connecter à une machine distante par ssh. Les options :
- `-p port ` pour préciser le port du serveur distant

#### installer une clé SSH

Pour éviter de saisir le mot de passe à chaque fois, on peut installer sur la 
machine distante la clé publique d'un utilisateur local.

[`ssh-copy-id`](http://manpages.ubuntu.com/manpages/precise/man1/ssh-copy-id.1.html)
permet de copie une clé publique de la machine locale vers le serveur ssh.

Les clés sont copiées dans le dossier *.ssh/authorized_keys* du compte cible sur la 
machine distante.

:warning: Il faut éviter de créer des clés SSH sans passphrase, car il suffirait de les copier
pour permettre d'accéder à la machine distante.

#### activer une clé SSH pour éviter de saisir sa passphrase

Pour éviter de saisir le passphrase à cahque fois, on utilise **ssh-agent**

`ssh-agent -s` - affiche les informations sur le process ssh-agent en cours

[`ssh-add`](https://linux.die.net/man/1/ssh-add) - ajoute la clé aux clés actives

`ssh-add -l` - liste les clés actives
