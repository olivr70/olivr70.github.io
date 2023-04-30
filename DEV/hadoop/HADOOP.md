Hadoop implémente un cluster orienté traitement de données.

Au coeur se trouve un système de stockage de données HDFS. Dans ce file
system on peut stocker des fichiers à plat, mais aussi des fichiers
de données structurées (RCFile, Parquet).

On peut ensuite créer des traitements qui seront automatiquement


De nombreux outils sont disponibles autour de Hadoop
- [Impala](http://impala.apache.org/overview.html) fournir un accès SQL  
aux données stockées dans Hadoop
- Sqoop est un langage de requête pour insérer des données depuis une base
SQL, et exporter des données vers une base SQL


Hadoop streaming permet de créer des traitements de données avec BASH  
(voir [MapReduce with Hadoop Streaming in bash - Part 1 :: Oracle Alchemist](http://www.oraclealchemist.com/news/tf-idf-hadoop-streaming-bash-part-1/)).
