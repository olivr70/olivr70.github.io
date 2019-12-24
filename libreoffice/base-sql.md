Libreoffice Base permet de créer des requêtes en SQL.

LibreOffice 6 utilise HSQL 1.8.0.10 pour les documents .odb (très très vieille version, jamais mise à jours )

Voir [Frequently asked questions - Base — The Document Foundation Wiki](https://wiki.documentfoundation.org/Faq/Base/HSQLFunctions)

## Pour une base associée à un fichier externe (Calc ou autre)

Voir [SQL functions for file based database drivers](http://www.openoffice.org/dba/specifications/file_based_functions.html)

### opérateurs de comparaison
- `=` ex : `WHERE "JIRS" = 'oui'`
- `!=` ex : `WHERE "ETAT" != 'clos'`

### opérateurs 

### principales fonctions

#### pour les chaines
- `UCASE(s)` et `LCASE(s)` pour les conversions de casse
- `LENGTH(s)` pour la longueur
- `LOCATE(t,s)` pour obtenir la position de *t* dans *s*
- `RTRIM(s)` et `LTRIM(s)` pour le nettoyage
- `CONCAT(s1,s2)` et `INSERT()` pour la concaténation
- `LEFT(s)`, `RIGHT(s)` et `SUBSTRING(s,p,l)` pour les extractions  
Les positions commencent à 1
- `SPACE(n)` et `REPEAT(s,n)`

#### pour les dates
- `YEAR()`, `MONTH()`, `DAYOFMONTH()` pour les composantes de la date
- `DAYOFYEAR()` et `DAYOFWEEK()` autres informations sur la date
- `WEEK(___, 1)` pour le numéro de la semaine (à partir du lundi)
- `CURDATE()`

## Pour une base .ODB embarquée (HSQL 1.8)
#### Information système
ATTENTION : ne marche que si on crée une base avec le moteur HSQL embarqué

- `SELECT * FROM "INFORMATION_SCHEMA"."SYSTEM_TABLES"`  
Affiche toutes les tables système
- `SELECT * FROM "INFORMATION_SCHEMA"."SYSTEM_PROPERTIES"`