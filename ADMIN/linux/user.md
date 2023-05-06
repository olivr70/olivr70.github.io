


### Créer un utilisateur 

`adduser <name>` crée un nouvel utilisateur


### [`usermod`](https://linux.die.net/man/8/usermod) changer les options d'un utilisateur
`usermod -aG sudo <username>` le user est désormais membre du group sudo

### Environnement de l'utilisateur

Voir [XDG Base Directory Specification](https://specifications.freedesktop.org/basedir-spec/basedir-spec-latest.html)

- CONFIG
  - **$XDG_CONFIG_HOME** : défaut `$HOME/.config`
  - **$XDG_CONFIG_DIRS** : défaut `/etc/xdg`
- DATA
  - **$XDG_DATA_HOME** : défaut `$HOME/.local/share`
  - **$XDG_DATA_DIRS** : défaut ` /usr/local/share/:/usr/share/`
- TEMP
  - **$XDG_RUNTIME_DIR** ex : `/run/user/1000`  
    user-specific non-essential runtime files and other file objects  
    MUST be the only one having read and write access to it  
    MUST not survive reboot or a full logout/login cycle.  
    MUST be on a local file system and not shared with any other system  
    MAY be subjected to periodic clean-up (sauf si sticky bit ou accédé il y a moins de 6 heures)
  - **$XDG_CACHE_HOME** : non-essential data files -  défaut `$HOME/.cache`