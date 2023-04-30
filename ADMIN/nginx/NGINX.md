
### configuration

La config de base est dans **/etc/nginx/nginx.conf**. Elle inclut automatiquement :
- tous les fichiers ***.conf** du répertoire **./conf.d**
- tous les fichiers du répertoire **./sites-enabled**  
en général, il s'agit de liens symboliques vers un fichier dans **./sites-available**

Pour tester la configuration, `sudo nginx -t`.

### démarrage
nginx est en général installé comme un service de [systemd](systemd.md). On utilise donc : 
- `systemctl status nginx` pour connaitre son état
- `systemctl start/stop/reload/restart nginx`


### Utilisation avec Docker

[nginx | Docker Documentation](https://docs.docker.com/samples/library/nginx/#hosting-some-simple-static-content)

### Config

[Full Example Configuration | NGINX](https://www.nginx.com/resources/wiki/start/topics/examples/full/)