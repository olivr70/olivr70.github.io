# [Eto.Parse](DEV/c_sharp/Eto.Parse/index.md) Créer une grammaire Fluent

## Créer une classe
On créé une classe avec comme membres tous les parsers dont a besoin

## optionel : attacher des events à certains Parser

On ajoute une méthode AttachEvents() pour isoler les events. Les events ne sont déclenchés qu'en cas
de succès de la grammaire

Si la grammaire a la propriété _EnableMatchEvents_ à _true_ (c'est le cas par défaut),
alors si Match a réussi, une série d'événements sont déclenchés,
- d'abord un parcours qui déclenche les events _PreMatch_, sur l'arbre des Matchs. Le parcours est ascendant
- d'abord un parcours qui déclenche les events _Match_, sur l'arbre des Matchs. Le parcours est ascendant également
