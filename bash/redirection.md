## input

`<file`

- `>file` ouvre file en écriture (échoue s'il existe déjà et si c'est un fichier) et redirige la sortie standard
- `>|file` ouvre file en écriture, même s'il existe déjà
- `>>file` ouvre file en mode append
- `&>file` ouvre file, et redirige la sortie standard et la sortie erreur
- `&>>file` ouvre file en mode append, et redirige la sortie standard et la sortie erreur

- `ls 2>file.log` redirige les erreurs vers file.log


### redirections permanentes

- `exec 1>outfile` redirige la sortie standard vers outfile pour toute la durée du script
- `exec 2>errors` redirige l'erreur standard vers outfile pour toute la durée du script
- `exec 0< infile` redirige infile dans l'entée standard
- `exec 3> somefile` redirige le file descriptor 3 vers somefile
  - on peut alors écrite "echo 'hello' 3>&
- exec   


