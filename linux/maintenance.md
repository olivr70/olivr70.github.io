### Kernel

`uname -r` - voir la version du kernel
`cat /etc/issue` - voir la version de Linux

Mettre à jour le noyau avec UKUU ([Upgrade Kernel on Ubuntu 18.04 – Linux Hint](https://linuxhint.com/upgrade-kernel-ubuntu-1804/))


### Démarrage et arrêt

`reboot` pour relancer la machine
`poweroff` pour l'éteindre

#### [shutdown](https://linux.die.net/man/8/shutdown)
`shutdown -r 1:30` pour relancer la machine à une heure donnée
`shutdown -k` envoie un message d'alerte d'un arrêt prochain (sans le programmer)
`shutdown -c` annule un arrêt programmé

### init.d

le répertoire **/etc/init.d** contient une série de scripts pour gérer les
services.

Pour chacun, on peut faire `status`, `start`, `stop`, `reload`, `restart`

#### Articles
[Get To Know Linux: The /etc/init.d Directory - gHacks Tech News](https://www.ghacks.net/2009/04/04/get-to-know-linux-the-etcinitd-directory/)


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

### Containers

[containerd – An industry-standard container runtime with an emphasis on simplicity, robustness and portability](https://containerd.io/)