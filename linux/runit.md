
### [`sv`](http://smarden.org/runit/sv.8.html) Contrôle des services runsv
- `sv status <service1> <service2>`
  - `sv status $(ls /etc/service)` liste l'état de touts les services
-  `sv check <service>` vérifie que le service est bien dans l'état souhaité
- `sv up <service>` démarre un service, et le relance s'il échoue
- `sv once <service>` démarre un service une seule fois
- `sv <signal> <service>` envoie un signal au service
  - `pause` STOP
  - `cont` CONT 
  - `hup` HUP
  - `alarm` ALRM
  - `interrupt` INT 
  - `quit` QUIT
  - `1` USR1
  - `2` USR2
  - `term` TERM
  - `kill` KILL