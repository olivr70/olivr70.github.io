




## `locate` et `updatedb`

[`locate`](http://manpages.ubuntu.com/manpages/bionic/man1/locate.findutils.1.html) recherche les fichiers par leur nom dans une base de données globales.

La base de données est mise à jour périodiquement, ou par la commande  [`updatedb`](http://manpages.ubuntu.com/manpages/precise/man8/updatedb.8.html).

Un fichier de configuration */etc/updatedb.conf* détermine quels fichiers sont ignorés :
- `PRUNEFS=` liste des file system à ignorer (séparés par des espaces)
- `PRUNPATH=` liste des chemins à ignore (ex : `/tmp /var/lib/ceph`)
- `PRUNENAMES=` list des noms de dosiers à ignorer, inactif par défaut (ex : `.git .svn`)
- `PRUNEBINDMOUNTS=` `0`/`1`/`yes` si 1 ou yes, les bind mounts sont ignorés

La base de données est dans */var/lib/mlocate/mlocate.db*, accessible en lecture seul
aux membres du groupe *mlocate*.

Il faut donc être *root* pour utiliser `updatedb`