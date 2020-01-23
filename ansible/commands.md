## ansible (alias `a`)

- `ansible --version` pour savoir  
la version, le chemin de l'exécutable, 

## ansible-config (alias `ac`)

- `ansible-config dump --only-changed -v`  
Affiche les variables ansible qui sont différentes des valeurs par défaut


## ansible-inventory (alias `ai`)

- `ansible-inventory`
  - `-i <path>` - emplacement de l'inventaire (dossier ou fichier)
  - `--list` ou ``--graph`

## ansible-doc

`ansible-doc -t inventory -l` fait la liste des plugins *inventory* installés. 
On peut demander : become, cache, 


## ansible-vault (alias `av`)

Utilitaire utilisé pour crypter les secrets de la configuration.

Pour éviter de passer le mot de passe à chaque appel, et de les mettre
dans les fichiers de configurations :
- on ajoute une entrée *hetzner/vault* avec `pass`
- on crée un script *~/scripts/ansible/vault_pass.sh* qui affiche le mot
de passe en invoquant `pass`  
Ce fichier peut être passé avec l'option en ligne de commande 
`-vault-password-file` or `-vault-id`
- on ajoute dans ~/.ansible.cfg une entrée 
``` ini
[default]
vault_password_file   = ~/scripts/ansible/vault_pass.sh
```

## ansible-playbook (alias `ap`)

- `ansible-playbook <book>`
  - `--list-tasks`
  - `--list-tags`