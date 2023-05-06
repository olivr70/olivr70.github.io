
## exemples

Pour... | Faire...
-  | -
Afficher seulement les directories | `ls -d */`
Afficher seulement les directories (1 par ligne) | `ls -d1 */`

## couleurs

### voir
Pour voir les couleurs : `dircolors`

Egalement un script `show-ls-colors.sh`

### modifier

Voir [Configuring LS_COLORS](http://www.bigsoft.co.uk/blog/2008/04/11/configuring-ls_colors) te la documentation [man DIR_COLORS](http://manpages.ubuntu.com/manpages/xenial/en/man5/dir_colors.5.html)

Le fichier de configuration contient des commandes :
- `TERM` (une ou plusieurs, avec des patterns) pour indiquer à quel terminal le fichier est applicable 
- `COLOR` *tty* *all* ou *none*
- `EIGHTBIT` *0* ou *1*
et une liste de codes ANSI à appliquer pour les catégories ou pour une extension

Pour générer un exemple de fichier, `dircolors -p > ~/.dir_colors`

Pour éditer, VIM dispose d'une aide syntaxique pour éditer les fichiers ".dircolors"

La configuration des couleurs est lue dans les fichiers suivants (le premier trouvé) :
- *$HOME/.dir_colors.$TERM*
- *$HOME/.dir_colors*
- *$HOME/.dircolors.$TERM*
- *$HOME/.dircolors*
- */etc/DIR_COLORS.$TERM*
- */etc/DIR_COLORS*
