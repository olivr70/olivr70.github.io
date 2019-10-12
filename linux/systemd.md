Systemd permet de gérer de nombreux aspects, en particulier les services et leur démarrage

### systemd

#### [`systemctl`](https://www.commandlinux.com/man-page/man1/systemctl.1.html)

Consulter l'état
- `sudo systemctl list-units`
- `sudo systemctl list-units-files`
- `sudo systemctl list-sockets`
- `sudo systemctl show XXXX`
- `sudo systemctl cat XXX` affiche le fichier .service 
#### journalctl

`journalctl`
- `--unit=XXXX` 


### Fonctionnement

Systemd démarre et arrête des **units**, chacune décrite dans un fichier. 
Elles peuvent être de plusieurs type :
- [service](http://man7.org/linux/man-pages/man5/systemd.service.5.html) : un process
- [slice]
- [socket]

#### Emplacement des fichiers Units

##### en mode system

Soit dans un répertoire fixé par **$SYSTEMD_UNIT_PATH**, soit `/etc/systemd/system`, `/run/systemd/system` puis `/usr/lib/systemd/system`

Il est possible de 'patcher' un fichier Unit, en créant un dossier `<unit-name>.d` puis
en plaçant à l'intérieur un ou plusieurs fichiers `*.conf`
Ex : /etc/systemd/system/**syslog.service.d**/**10-restart60s.conf**.

##### en mode --user

Soit : 
- `$XDG_CONFIG_HOME/systemd/user` ou `$HOME/.config/systemd/user`  
par défaut, **$XDG_CONFIG_HOME** vaut `$HOME/.config`
- `/etc/systemd/user`
- $XDG_RUNTIME_DIR/systemd/user 
- /run/systemd/user 
- `$XDG_DATA_HOME/systemd/user` ou `$HOME/.local/share/systemd/user`  

### la création de son propre service
- créer le fichier unit
- vérifier : `systemd-analyze verify /path/to/your/file.service` 
-


### le lancement d'un service

1. exécute les commandes ExecStartPre=
1. exécute les commandes ExecStart=
  - si Type=`simple` ou `exec`  
    le processus lancé est considéré comme le process principal
  - si Type=`forking`  
    le processu lancé par crée un child process et ensuite s'arrête. On utilise
    **PIDFile=** pour indiquer ou trouver l'id du process principal
  - si **Type=**=`dbus`  
    le service est dépendant de **dbus.service**. Le service est considéré comme
    démarré quand le nom **BusName=** est acquis.

### le contenu des fichiers units

Ils sont organisés en section

les sections communes
- [[Unit]](https://www.freedesktop.org/software/systemd/man/systemd.unit.html#)
- [[Install]](https://www.freedesktop.org/software/systemd/man/systemd.unit.html#)
- [[Exec]](https://www.freedesktop.org/software/systemd/man/systemd.exec.html#)  
  for **service**, **socket**, **swap** and **mount**

les sections spécifiques
- [[Service]](https://www.freedesktop.org/software/systemd/man/systemd.service.html#)
- [[Socket]](https://www.freedesktop.org/software/systemd/man/systemd.socket.html#)

### Articles

- [Systemd — Lea Linux](https://lea-linux.org/documentations/Systemd)
- [Running Docker Containers with Systemd](https://blog.container-solutions.com/running-docker-containers-with-systemd)  
Utilisation de [`systemd-docker`](https://github.com/ibuildthecloud/systemd-docker) pour  
gérer les petites spécicités (en particulier s'assurer que systemd supervise bien
le container lui-même et pour générer l'image docker)