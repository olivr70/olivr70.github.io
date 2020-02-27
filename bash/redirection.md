## output

`<file`

- `>file` ouvre file en écriture (échoue s'il existe déjà et si c'est un fichier) et redirige la sortie standard
- `>|file` ouvre file en écriture, même s'il existe déjà
- `>>file` ouvre file en mode append
- `&>file` ouvre file, et redirige la sortie standard et la sortie erreur
- `&>>file` ouvre file en mode append, et redirige la sortie standard et la sortie erreur

- `ls 2>file.log` redirige les erreurs vers file.log

### redirections vers un file descriptor

- `X>&Y` redirige le file descriptor X vers le file descriptor Y
  - `>&Y` redirige le FD 1 (stdout) vers le FD Y

### fermeture
- `X>&-` ferme le file descriptor X

### redirections permanentes

- `exec 1>outfile` redirige la sortie standard vers outfile pour toute la durée du script
- `exec 2>errors` redirige l'erreur standard vers outfile pour toute la durée du script
- `exec 0< infile` redirige infile dans l'entée standard
- `exec 3> somefile` redirige le file descriptor 3 vers somefile
  - on peut alors écrite "echo 'hello' 3>&

### redirection vers un process

La substitution de process >( ... ) réalise :
- création d'un pipe anonyme
- crée un process pour exéctuter la commande ...
  - avec son entrée standard connectée en lecture sur le pipe
- retourne le nom du pipe
  - `echo >(cat -n)` => `/dev/fd/63`

On peut l'utiliser directement comme une redirection de la sortie standard
- `ls | cat -n` et `ls > <(cat -n)` produisent la même sortie

### pipes

**PIPESTATUS** est un tableau qui contient le résultat de chaque étape du dernier pipe.
`echo ${PIPESTATUS[@]}` pour l'afficher

### coprocess

lance une commande dans un process autonome de manière asynhchrone. 
Dans le coprocess, les entrées et sorties standards sont redirigées.

Dans le process appelant :
- la commande retourne toujours SUCCESS
- les file descriptor des pipes sont stockés dans un tableau 
  - **NAME[0]** sortie standard
  - **NAME[1]** entrée standard
  - **NAME[2]** erreur standard
- le PID du process crée est dans la variable **NAME_PID**

Example
```bash
#!/bin/bash

coproc PING { ping -c 10 192.168.1.254; }
echo ${PING[0]}
while read res <& ${PING[0]}; do
  echo "-- $res"
done
```


