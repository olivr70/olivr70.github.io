
[Cloud-init](https://cloudinit.readthedocs.io/en/latest/index.html#) est un mécanisme de démarrage d'une instance très largement
utilisé par les fournisseurs de cloud (dont Hetzner)

Lire le [Cloud-init whitepaper](https://www.dropbox.com/s/dgtwr8dbfquwgwd/CloudInit_Whitepaper.pdf?dl=0)

## Démarrage

Les fichiers de **/etc/cloud/cloud.cfg.d** sont exécutés

## Commandes

`cloud-init query` 
- `platform` => **hetzner**
- `instance_id` => 2323232
- `local_hostname` => **dev**
- `vendordata` donne des informations sur l'hébergeur  
  contenu de **/var/lib/cloud/instance/vendor-data.txt**
- `usedata` donne des informations fournies par l'utilistaeur
- `ds.meta_data` donne des informations sur la machine