
Il faut utiliser [`apt`](http://manpages.ubuntu.com/manpages/xenial/man8/apt.8.html) (apt-get est plus ancien)

### repositories

`sudo apt edit-sources` pour voir le fichier /etc/apt/sources.list (attenion, ce fichier est
généré automatiquement) 

le répertoire **/etc/apt/sources.list.d** contient des fichiers **.list** avec des sources.
- deb|deb-src <URL> <xenial|bionic|...> multiverse
Par exemple : 
- `deb [arch=amd64] https://repo.mongodb.org/apt/ubuntu bionic/mongodb-org/4.0 multiverse`
- `deb [arch=i386,amd64] http://linux.dropbox.com/ubuntu bionic main`

La commande [`add-apt-repository`](http://manpages.ubuntu.com/manpages/bionic/en/man1/add-apt-repository.1.html) évite de manipuler directement cette liste. Ses options :
- `-u` pour faire `apt update` automatiquement
- `-r` pour supprimer le repository

#### Sécurité et confiance

Le répertoire **/etc/apt/trusted.gpg.d** contient des clés utilisées pour autentifier 
les repos, qui sont alors considérés comme *Trusted*.

On peut utiliser [`apt-key`]http://manpages.ubuntu.com/manpages/bionic/en/man8/apt-key.8.html)
pour :
- `apt-key list` - liste tous les certificats installés  
```
/etc/apt/trusted.gpg.d/projectatomic_ubuntu_ppa.gpg  
---------------------------------------------------  
pub   rsa4096 2017-06-26 [SC]  
      018B A5AD 9DF5 7A44 48F0  E6CF 8BEC F163 **7AD8 C79D**  
uid           [ unknown] Launchpad PPA for Project Atomic  
```
- apt-key remove **{keyid}**  
ou **keyid** correspond au 8 derniers chiffres hexa dans la ligne 'pub' (ex `7AD8C79D` )

### Les PPA (Personal Package Archive)

Elles sont disponibles sur [launchpad.net](https://launchpad.net/).
Exemple pour [nginx sur Launchpad](https://launchpad.net/nginx)

Pour ajouter : `sudo add-apt-repository ppa:`




### Articles

- [Using apt Commands in Linux [Complete Guide] - It's FOSS](https://itsfoss.com/apt-command-guide/)
- [What is PPA? Everything You Need to Know About PPA in Linux](https://itsfoss.com/ppa-guide/)
