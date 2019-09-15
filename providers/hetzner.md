## ligne de commande

pour télécharger [hcloud](https://github.com/hetznercloud/cli/releases/tag/v1.13.0)

### pour se connecter

`hcloud context create <name>` -- demande l'API key du projet



### pour voir l'état de la plateforme

`hcloud image list` -- affiche les images et les snapshots de l'utilisateur
`hcloud server list` -- affiche les serveurs actifs


### Outils disponibles

- [cloudinit](https://cloudinit.readthedocs.io/en/latest/index.html) pour la configuration initiale d'un serveur
  - on peut passer le fichier avec `hcloud server create --user-data-from-file <PATH>`
- systemd pour le boot