## `netstat` - voir les ports ouverts

`netstat -l -t -4 -e -p`

- `-l` : ports en écoute
- `-t` : TCP
- `-4` : seulement ipv4
- `-e` : afficher plus d'info (user en particulier)
- `-p` : afficher le programme (PID)

## `lsof`[`lsof`](https://linux.die.net/man/8/lsof) (list open files)

`sudo lsof -i -n | egrep '\<ssh\>'` - voir tous les tunnels ssh
