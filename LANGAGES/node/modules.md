## les variables globales

- `module` contient l'objet [Module](https://nodejs.org/api/modules.html#modules_the_module_object) du module courant. Quelques éléments utiles
  - `id` : l'id du module ("." pour le module principal, chemin du fichier dans la plupart des cas)
  - `filename` : le chemin du fichier définissant le module
  - `exports` les membres exportés par ce module. 
    C'est la valeur retournée par require()
  - `parent` : le premier module qui a chargé ce module 
- `__filename` le chemin du dossier script en cours d'exécution 
- `__dirname` le chemin du dossier script en cours d'exécution

## les modules builtin

### constants `= require('constants')`

### [os](https://nodejs.org/api/os.html) `= require('os')`

- `os.userInfo() \\` 
```json
{
  "uid": 1000,
  "gid": 1000,
  "username": "olivr70",
  "homedir": "/home/olivr70",
  "shell": "/bin/bash"
}
``` 
- os.hostName()
`"DELL"`
- os.networkInterfaces() 
`{ <name> : {} }`
- os.cpus()
`[{ model :  "", ... }]`
- os.totalmem() et os.freemem()
`4090454016` et `226729984`
- os.loadavg()
`[ 0.32568359375, 0.5361328125, 0.533203125 ]`

