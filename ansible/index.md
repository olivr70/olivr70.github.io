
# Ansible

Pour des informations sur les [commandes de Ansible](./commands)

Pour les [détails sur Jinja2](./jinja2), utilisé pour toutes les expressions

Pour l'utilisation de [HCloud avec Ansible](./ansible_and_hcloud)

## Docs

[Getting Started — Ansible Documentation](https://docs.ansible.com/ansible/latest/user_guide/intro_getting_started.html#)


## Vocabulaire
- *host* : un serveur
- *group* : un ensemble de serveur  
un même serveur peut appartenir à plusieurs groupes
- *role* : un ensemble d'options qui peut être attribué à un serveur ou à un groupe

## configuration et priorité

Ansible dispose de très nombreuses options (la liste dans [Ansible Configuration Settings — Ansible Documentation](https://docs.ansible.com/ansible/latest/reference_appendices/config.html#ansible-configuration-settings))

De manière générale, la valeur d'une option dans ANSIBLE est déterminée dans l'odre de priorité suivant :
- variable
  - une variable peut être définie à de très nombreux endroits, et il existe également  
  des règles de priorité (voir [Using Variables — Ansible Documentation](https://docs.ansible.com/ansible/latest/user_guide/playbooks_variables.html#ansible-variable-precedence))
  - quelques exemples, dans l'ordre de priorité
    - peut être fixé avec l'option `-e` (ex : `-e 'myvar=10'`)
    - le module [*set_fact*](https://docs.ansible.com/ansible/latest/modules/set_fact_module.html#set-fact-module)
      - il permet de créer dynamiquement des variables associées à un host
    - le module *include_vars*
    - les variables dans *group_vars/all* et *group_vars/*
    - les variables dans *host_vars/all* et *host_vars/*
    - le fichier inventory
- playbook
- option de ligne de commande
- configuration (*ansible.cfg* et variables d'environnement)  
  - les variables d'environnement ont la forme **ANSIBLE_XXXX** ou XXX est le nom de l'option
premier trouvé dans *$ANSIBLE_CFG*, *./ansible.cfg*, *~/ansible.cfg* puis */etc/ansible/ansible.cfg*
  - le fichier ansible.cfg ([doc](https://docs.ansible.com/ansible/latest/reference_appendices/config.html#ansible-configuration-settings))

:warning: Le fichier ansible.cfg doit être protégé, car sinon tout utilisateur pourrait ensuite créer ses propre playbooks et les faire exécuter par ansible

## python
Ansible est écrit en Python et exécute des scripts Python sur les machines 
administrées. Il fonctionne avec Python 2.6+ et Python 3.5+.

La recherche de l'interpréteur Python est gouvernée par la variable 
`ansible_python_interpreter`. Elle vaut : <path> ou `auto_legacy` par défaut

Elle peut être fixée dans *ansible.cfg/[defaults]/interpreter_python* ou 
directement dans le fichier d'inventaire.

## les [Roles](https://docs.ansible.com/ansible/latest/user_guide/playbooks_reuse_roles.html)

Chaque rôle un dossier, avec une structure spécifique. On doit trouver au 
moins *./tasks/main.yml*, *./handlers/main.yml*,*./fils/main.yml*,
*./templates/main.yml*,*./vars/main.yml*.

les rôles sont recherchés dans :
- le sous-dossier *./role* à partir du playbook
- dans */etc/ansible/roles* (config `roles_path` dans *ansible.cfg*) 

un rôle appelé "common" permet de partager tous les réglages de base sur 
les machines de la plateforme

On attribue un rôle à un groupe ou un host dans l'inventaire. On peut 
même utiliser un rôle depuis un autre rôle avec "./meta/main.yml*

## les inventaires

### les inventaires statiques

Soit dans :
- */etc/ansible/hosts* (fichier .ini, avec une section par groupe,
 et des noms de machines)
- soit dans le dossier d'un playbook

### les inventaires dynamiques - hcloud

Voir [Working with dynamic inventory](https://docs.ansible.com/ansible/latest/user_guide/intro_dynamic_inventory.html#intro-dynamic-inventory)

- Il faut installer [hcloud-python](https://pypi.org/project/hcloud/) avec `pip install hcloud`
- Le plugin doit être activé dans *ansible.cfg/[inventory]/enable_plugins*  
ex  :  
``` ini
[inventory]
enable_plugins = hcloud
```
- Il faut ensuite ajouter un fichier */etc/ansible/hcloud.yaml* qui contient  
la configuration (en particulier le token) (voir  
[hcloud – Ansible dynamic inventory plugin for the Hetzner Cloud](https://docs.ansible.com/ansible/latest/plugins/inventory/hcloud.html))

Dans le fichier de configuration, on peut ensuite configurer les groupes
que l'on veut

## les facts

Le module [setup](https://docs.ansible.com/ansible/latest/modules/setup_module.html) 
obtient des informations sur la machine. Il est automatiquement appelé 
avant d'exécuter un playbook.

On peut visualiser les informations obtenues avec `ansible -m setup` :
- `ansible -m setup filter=ansible_*_mb`  
Information sur la mémoire
- `ansible -m setup gather_subset=hardware`  
Peut être `all`,`hardware`, `network`, `all`, `min`


