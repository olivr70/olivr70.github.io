

### cron

Voir [System Initialization](http://refspecs.linuxbase.org/LSB_4.1.0/LSB-Core-generic/LSB-Core-generic/sysinit.html#CRONJOBS)
Cron exécute des taches de manière périodique.

#### applications

Les applications peuvent installer des scripts pour une exécution périodique :
- dans les dossiers **/etc/cron.hourly/**, **/etc/cron.daily/**
, **/etc/cron.weekly/** et **/etc/cron.monthly/**.
- dans **/etc/cron.d/**, en réservant le nom sur [The Linux Assigned Names And Numbers Authority - LANANA](http://www.lanana.org/) ou en utilisant comme préfixe son domaine (ex : **lexcapio.fr-XXX**)

#### Utilisateurs - crontab

Il faut utiliser [`crontab` - Linux man page](https://linux.die.net/man/1/crontab).

Droits : 
- si **/etc/cron.allow** existe, alors seuls les utilisateurs listés peuvent utiliser `crontab`.  
par défaut à l'installation d'Ubuntu, ce fichier n'existe pas et donc tous les utilisateurs peuvent
invoquer crontab

- si **/etc/cron.deny** existe, alors les utilisateurs listés ne peunvet pas utiliser `crontab`

`crontab -e` pour éditer les taches de USER
`crontab -l` pour afficher le crontab de USER

Une entrée crontab comporte items suivants, séparés par au moins un espace
- minute :  
  - `0` à chaque heure
  - `*/2` toutes les deux minutes
  - `10,40` à 10 et 40 de chaque heure
- heure :
  - `9-12` toutes les heures de 9 à 12
  - `9-18/3` toutes les 3 heures entre 9 h et 18 h (9,12,15,18)
- day of month : 
  - `5,15,25` 3 fois par mois, les 5 15 et 25 du mois
- month :
  - `sep` en septembre (ou `jan`,`feb`,`mar`, `apr` ...)
- day of week : 
  - `0` ou `7` le dimanche
  - `mon` le lundi (ou `tue`, `wed`, `thu`, `fri`, `sat`)
- la commande à exécuter