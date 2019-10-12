
## Etat

`buildah images` -> list des images
`buildah containers` -> liste des containers

## Création d'une image

### à partir d'un Dockerfile

`buildah bud -f Dockerfile -t fedora-httpd .`

### Utilisation avec Gihub Package Registry

#### 1 création d'un token
Voir [Creating a personal access token for the command line - GitHub Help](https://help.github.com/en/articles/creating-a-personal-access-token-for-the-command-line)

Pour se connecter avec **docker** : 
- `docker login docker.pkg.github.com -u olivr70 -p $(pass github/tokens/docker)`

