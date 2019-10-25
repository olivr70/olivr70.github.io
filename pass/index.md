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

## [pass](https://www.passwordstore.org/)

Voir le [man](https://git.zx2c4.com/password-store/about/) ou [code source](https://git.zx2c4.com/password-store/tree/src/password-store.sh)

### config
- **PASSWORD_STORE_DIR** si on veut stocker les mdp ailleurs que dans `~/.password-store`
- **PASSWORD_STORE_GPG_OPTS** options pour l'invocation de GPG

### Création du premier repo

\$ `pass init <CLE GPG>` (ex : adresse mail)

\$ `pass git init`

\$ `pass git remote add origin git:_______`

### mise à jour

\$ `pass git status`
\$ `pass git pull origin`
\$ `pass git push origin master`

### utilisation du repos sans 'pass'

On peut voir un mot de passe avec `gpg --decrypt ~.password-store/dir1/mdp/root.pgp`

### Création de clones

\$ `git clone git:______ .password-store`

\$ `git push origin master`

\$ `git pull origin master`
