### SysV init (init.d)

Il s'agit du système de démarrage de Linux historique. Parmi les alternative,
[systemd](systemd.md) et [runit](runit.md).

<div style="border:2px solid red">init.d est considéré comme obsolète

Sur Ubuntu 18, les invocations de **/etc/init.d/SERVICE** et **service SERVICE** 
se traduisent en appels à [systemd](systemd.md).
</div>

#### Commandes

- `ls /etc/init.d` -- affiche la liste des services
- `/etc/init.d/SERVICE status` ou `service SERVICE status` -- affiche l'état d'un service
- `service --status-all` -- affiche l'état de tous les services (**+** démarré, **-** éteint)

#### Fonctionnement

Voir [System Initialization](http://refspecs.linuxbase.org/LSB_4.1.0/LSB-Core-generic/LSB-Core-generic/tocsysinit.html)

au démarrage, le système passe par plusieurs runlevel

A chaque runlevel, il exécute les scripts qui se trouvent dans les dossiers **rcX.d**. 
Dans chaque dossier les scripts se nomment **Kxx** ou **Sxx**.

Chaque script démarre un service.

On peut connaitre le runlevel avec `who -r`

Les scripts dans rcX.d sont en fait des liens, en général vers **/etc/init.d**.

Chacun des scripts peut-être invoqué avec comme premier paramètre `status`, `start`, `stop`, `reload`, `force-reload` ou `restart`.

la commande `status` retourne :
- **0**	program is running or service is OK
- **1**	program is dead and /var/run pid file exists
- **2**	program is dead and /var/lock lock file exists
- **3**	program is not running
- **4**	program or service status is unknown
