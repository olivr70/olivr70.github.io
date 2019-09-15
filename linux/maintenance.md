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