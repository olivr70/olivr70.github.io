## Gestion des disques et des partitions (LVM)

Structure d'installation de Lubuntu

- _/dev/sda_ - le disque dur
  - _/dev/sda1_  - montée sur **/boot** : partition de démarrage
  - _/dev/sda2_  - partition étendue
    - _/dev/sda5_ - partition **lvm2 pv**  (groupe *lubuntu_vg*)
      - _root_ - volume logique principal
      - *swap_1* - volume logique pour le swap

On peut voir les partitions avec `sudo gparted &`



## LVM Logical Volume Manager

On regroupe plusieurs _physical volume_ (pv) désignés (avec `pvcreate`) en _volume group_ (vg). On crée ensuite des _logical volume_ (lv)) avec `lvcreate`.

Les _logical volume_ peuvent intégrer une certaine redondance (si on a plusieurs disques physiques) (striped, raid1, raid5..)

L'intérêt est qu'on peut ajouter dynamiquement de nouveaux disques dans un groupe (`vgextend`), et ensuite étendre et redimenssioner les LV.

### voir les volumes physiques
Affiche tous les volumes formattés pour être utilisés avec LVM
- `sudo pvscan`
- `sudo pvs` - affichage compact des volumes physiques
  ```  
  PV         VG         Fmt  Attr PSize    PFree 
  /dev/sda5  lubuntu-vg lvm2 a--  <223,09g 44,00m
  ```
- `sudo pvdisplay`
  - `-m` pour voir à quoi sont utilisées les zones physiques (extents)


### voir les groupes logiques
- `sudo vgs` - affichage compact de tous les groupes
  -`-o +devices,lv_path` - affiche le device et les chemins
- `sudo vgdisplay` - affichage détaillé de chaque groupe (plus humain)
### voir les volumes logiques
- `sudo lvs` - affichage compact de tous les volumes
- `sudo lvdisplay` - affichage détaillé

Les volumes logiques sont souvent montés par référence à _dev/mapper/_.

### device manager

`sudo dmsetup ls` ou `sudo dmsetup info -c` affiche les devices et quelques info 

Un peu de doc :
- [man dmsetup](https://linux.die.net/man/8/dmsetup)
- [dmsetup command examples ~ Linux IQ](https://linuxadministrative.blogspot.com/2014/06/dmsetup-command-examples.html)



### Articles

[lvm [Wiki ubuntu-fr]](https://doc.ubuntu-fr.org/lvm)
[How To Use LVM To Manage Storage Devices on Ubuntu 16.04 | DigitalOcean](https://www.digitalocean.com/community/tutorials/how-to-use-lvm-to-manage-storage-devices-on-ubuntu-16-04) (excellent)