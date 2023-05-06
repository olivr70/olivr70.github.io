Au démarrage, Bash exécute de nombreux scripts

Voir [Bash Startup Files (Bash Reference Manual)](https://www.gnu.org/software/bash/manual/html_node/Bash-Startup-Files.html#Bash-Startup-Files)

## les types de shell

- **shell interactif** :
  - soit:
    - démarré avec `-i`
    - démarré sans commande à exécuter (avec `-c` ou sur la ligne de commande)
  - et avec input et error connectés à un terminal
  - peut être détecté :
    - si la variable **$PS1** est définie
    - si la variable **$-** contient i
- **shell restreint** (restricted)  
  - peut être détecté avec `shopt restricted_shell`
- **login shell**
  - Soit
    - le premier shell ouvert
    - un shell démarré avec l'option `--login`
  - peut être détecté avec `shopt | grep 'login_shell`


## les fichiers exécutés au démarrage

- si login shell, exécute :
  - **/etc/profile**
    - dans Ubuntu 18.04 : 
      - lance tous les scripts dans **/etc/profile.d/*.sh**
  - puis le premier parmi  **~/.bash_profile**, **~/.bash_login**, and **~/.profile**
    - par défaut, **~/.profile** lance **~/.bashrc** s'il existe
- si interactive et non-login shell, :
  - exécute **~/.bashrc**
     - exécute **~/.bash_aliases**
- si non interactive
  - exécute le fichier dont le chemin est dans **$BASH_ENV** s'il existe
 

## les options de bash


On peut aussi les fixer au lancement de bash avec :
- la variable **$BASHOPTS**
- les options en ligne de commande `-O optname` (set) et `+O optname`

On peut les consulter et modifier 
- avec [`shopt`](https://www.gnu.org/software/bash/manual/html_node/The-Shopt-Builtin.html) () `shopt -s` et `shopt -u` permettent de  les activer ou désactiver).
- avec la commande POSIX [`set`](https://ss64.com/bash/set.html)
  - `set -o option` ou `set +o option`, certaines options n'ayant pas de racourcis
    - `emacs`
    - `history`  
    Enable command history, as described above under HISTORY.  This option is  on by default in interactive shells.
    - `ignoreeof`  
    The  effect is as if the shell command 'IGNOREEOF=10' had been executed
    - `pipefail`  
    If set, the return value of a pipeline is the value of the (rightmost) command to exit with a non-zero status, or zero if all commands in the pipeline successfully.
    - `vi`  
    Use a vi-style command line editing interface.
  - et les racourcis
    - `allexport`   Same as `-a`.
    - `braceexpand` Same as `-B`.
    - `errtrace`    Same as `-E`.
    - `functrace`   Same as `-T`.
    - `errexit`     Same as `-e`.
    - `hashall`     Same as `-h`.
    - `histexpand`  Same as `-H`.
    - `keyword`     Same as `-k`.
    - `monitor`     Same as `-m`.
    - `noclobber`   Same as `-C`.
    - `noexec`      Same as `-n`.
    - `noglob`      Same as `-f`.
    - `notify`      Same as `-b`.
    - `nounset`     Same as `-u`.
    - `onecmd`      Same as `-t`.
    - `physical`    Same as `-P`.
    - `privileged`  Same as `-p`.
    - `verbose`     Same as `-v`.
    - `xtrace`      Same as `-x`.

On peut afficher les options courtes avec **$-**, qui contient la lettre 
correspondant aux options **on**. 
Par exemple `HmhBi`
- H - histexpand
- m - monitor
- h - hashall
- B - braceexpand
- i - interactive
