## `netstat` - voir les ports ouverts

`netstat -l -t -4 -e -p`

- `-l` : ports en écoute
- `-t` : TCP
- `-4` : seulement ipv4
- `-e` : afficher plus d'info (user en particulier)
- `-p` : afficher le programme (PID)

## `lsof`[`lsof`](https://linux.die.net/man/8/lsof) (list open files)

`sudo lsof -i -n | egrep '\<ssh\>'` - voir tous les tunnels ssh

## IP v6

- 8 blocks de 4 octets séparés par :
- 0 initiaux ne sont pas obligatoires `0012` => `12`
- 2 ou plus groupes de 0 peuvent être notés `::`
- on peut préciser une taille de sous réseau avec un suffixe. Ex: `/64`

`ping -6` pour faire un ping IPv6