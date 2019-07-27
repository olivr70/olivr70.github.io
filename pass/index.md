## Pass (password manager)

### Pass et Gpg

#### Setup

Dans _.bashrc_, ajout de :

`export GPG_TTY=$(tty)`

#### Utilisation

`gpg -k` - affiche la liste des clés gpg

Copier une clé privée vers une autre machine

- `gpg --list-secret-keys`
- `gpg --export --armor ID_DE_CLE > ~/cle-publique.asc`
-
- `gpg --export-secret-keys --armor --output ~/cle-privee.asc`
- `scp *.asc MACHINE:~`
- `ssh MACHINE`
- `gpg --import ~/cle-publique.asc`
- `gpg --import ~/cle-privee.asc`

### Création du premier repo

\$ `pass init <CLE GPG>` (ex : adresse mail)

\$ `pass git init`

\$ `pass git remote add origin git:_______`

### Création de clones

\$ `git clone git:______ .password-store`

\$ `git push origin master`

\$ `git pull origin master`
