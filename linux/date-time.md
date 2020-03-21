

## [date](http://manpages.ubuntu.com/manpages/bionic/man1/date.1.html)

- `date` affiche la date courante
- `date -r <path>` affiche la date de modification du fichier path
  - `-I` au format ISO 8601
    - `-Ihours`, `-Iseconds`... pour la précision
  - `-R` au forrmat mail ()
- `date +FMT` affiche la date dans le format indiqué
  - `%y` et `%Y` pour l'année sur 2 ou 4 digits
  - ``