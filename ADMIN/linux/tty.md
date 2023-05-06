
## [stty](http://manpages.ubuntu.com/manpages/trusty/man1/stty.1.html)
Permet de configurer le terminal

Principalement utilise pour modifier (ou voir) les racourcis claviers

`stty -a` affiche toutes les options

`stty -<option>` désactive une option et `stty <option>` l'active. On peut
vérifier avec `ssty -a`

Pour les racourcis claviers standards :
- **Ctrl+C** - Interrupt - SIG KILL
- **Ctrl+S** - STOP
- **Ctrl+Q** - START
- **Ctrl+Z** - suspend
- **Ctrl+U** - erase current line