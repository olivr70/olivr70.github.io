

### Doc
[FAQ](https://wiki.hetzner.de/index.php/CloudServer/en)

### [hcloud](https://github.com/hetznercloud/cli)

#### contexte

Pour initialiser le contexte, on ajoute le token avec `hcloud contexte create <name>`.
C'est une commande interactive qui demande la saisie du token Hetzner
Cette solution est beaucoup plus sûre que d'utiliser la variable **HCLOUD_TOKEN**

- `hcloud context active` ou `hcloud context list`- affiche le contexte courant

#### image
- `hcloud server create-image --description "dev" --name "dev" dev`



#### serveurs
- `hcloud server list` - liste des serveurs
- `hcloud server ssh -u olivr70 dev` - connexion en ssh

Création 
- `hcloud server create`
  - `--type` **cx11**
  - `--name` {MY_NAME}

#### informations
- `hcloud image list` - liste des images disponibles
- `hcloud server-type list`  
  **cx11** plus petite des machines virtuelles

