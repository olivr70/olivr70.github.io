
## les process

### les états

- **R**	Running or runnable (on run queue)
- **D**	Uninterruptible sleep (waiting for some event)
- **S**	Interruptible sleep (waiting for some event or signal)
- **T**	Stopped, either by a job control signal or because it is being traced by a debugger.
- **Z**	Zombie process, terminated but not yet reaped by its parent.

un process appartient toujours à un unique _process group_ (il peut y être seul). L'id
du process group est le groupe du premier process (mais le groupe peut survivre
à la disparition de ce premier process)

Par ailleurs, un process peut être :
- **session leader** : un ensemble de _process group_. Si un terminal est associé
à la session, le _session leader_ est aussi le _controling process_ de ce terminal
- **foreground process group** : à un instant donné, un terminal est toujours associé 
à un seul process group, le _foreground process group_. Il peut changer 

### la commande [`ps`](http://manpages.ubuntu.com/manpages/precise/man1/ps.1.html)

3 modes : BSD (options sans tirets), UNIX (options avec tirets) et GNU 
(options avec double tirets). Les options se recoupent, mais le filtrage par
défaut est différent :
- BSD : seulement les process du terminal courant
- UNIX : seulement les process de l'utlisateur effectif (euid)

les principales options en mode BSD 
- filtrage
  - `a` tous les users (sinon seulement l'utilisateur courant)
  - `T` seulement les process du terminal courant
  - `t` nom du terminal
- sortie
  - `o`
les principales options en mode Unix
- le filtrage
  - `-e` ou `-A` : tous les process
  - `-a` : tous, sauf les session leader 
  - `-U <userlist>` 
  - `x` : y compris les process sans terminal
  - `r` ; les process en courts d'exécution
- sortie
  - `-f`  full-format
  - `-F` extrafull
  - `-O` permet d'ajouter des colonnes


## les signaux

On peut envoyer un signal à un process. Ce signal est soit géré par l'OS,
soit pas le shell, soit par le programme lui-même.

Par défaut dans le terminal, certains racourcis claviers envoient des 
signaux au process courant :
- **Ctrl+S** STOP (stty stop)
- **Ctrl+Q** START (stty)

### la commande kill

- `kill -l` liste tous les signaux (nom et numéro)
- kill permet de connaitre le nom ou numéro d'un signal dooné
  - `kill -l 9` => `KILL`
  - `kill -l KILL` => `9`

La commande kill permet d'envoyer un signal à un process
- `kill -STOP <PID>` pour un process par son PID
- `kill -CONT %1` pour un numéro de jobs


## les jobs (bash)

Voir [Bash Features - Job Control](https://web.mit.edu/gnu/doc/html/features_5.html).

Chaque shell Bash gère plusieurs jobs (process). Un seul job est *Foreground*,
les autres sont en background (pas d'accès au terminal en lecture)

- `jobs -l` affiche la liste des jobs
- **Ctrl+Z** suspend le job Foreground et revient au shell
- `fg %n` met en foreground le jobs dont l'id est _n_
- `bg %n` relance le job _n_ en background
- `disown %n` retire un job. Il ne recevra pas le signal SIGHUP quand le  
shel parent le recevra

- `%+` et `%%` font référence au job courant
- `%-` font référence au job précédent ()