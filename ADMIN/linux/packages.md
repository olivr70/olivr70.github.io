
## apt
### apt-list

sudo apt list | grep -e ^nginx

### [`dpkg`](http://manpages.ubuntu.com/manpages/xenial/man1/dpkg.1.html)

- `dpkg -l` affiche tous les paquets installés
- `dpkg -i` installe un paquet à partir d'un fichier .deb
- `dpkg -r NAME` ou `dpkg -p NAME` supprime un paquet  
  (`-p` supprime aussi les fichiersd de config)

### [`debconf-show`](http://manpages.ubuntu.com/manpages/trusty/man1/debconf-show.1.html)  - query the debconf database
- `sudo debconf-show --listdbs` liste des base de config  
   Sur Ubuntu : **configdb**, **configdb/config** et **configdb/passwords**
- `sudo debconf-show --listowners`
  - optionel :`-db=config|passwords` affiche la liste des packages qui ont des entrées dans la base
- `sudo debconf-show cups`

### dpkg-reconfigure

[How to Reconfigure Installed Package in Ubuntu and Debian](https://www.tecmint.com/dpkg-reconfigure-installed-package-in-ubuntu-debian/)

- `sudo dpkg-reconfigure PACKAGE`