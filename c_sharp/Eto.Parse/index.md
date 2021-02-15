# Eto.Parse

* [Repository](https://github.com/picoe/Eto.Parse)
* [Documentation](https://www.fuget.org/packages/Eto.Parse/1.5.0/lib/netstandard2.0/Eto.Parse.dll)
* [openHub summary](https://www.openhub.net/p/EtoParse)
* [Forum](https://groups.google.com/g/eto-parse) (plus actif, peut de conversations)


## Création d'une grammaire

**Eto.Parse** offre plusieurs possibilités pour créer une grammaire :
- une [API Fluent](./fluent.md)
  - [Documentation](https://www.fuget.org/packages/Eto.Parse/1.5.0/lib/netstandard2.0/Eto.Parse.dll)
  - exemple [parser JSON](https://github.com/picoe/Eto.Parse/blob/master/Eto.Parse.Samples/Json/JsonGrammar.cs)
- un parser  


### Les Writer
Ils sont utilisés pour afficher la structure d'un Parser.

Deux writers sont implémentés : 
- DisplayWriter
- [CodeParseWriter](https://github.com/picoe/Eto.Parse/blob/master/Eto.Parse/Writers/CodeParserWriter.cs)

Les principales classes :
- IParserWriter : tout objet avec la méthode principale WriteParser()
- [ParserWriterArgs](https://github.com/picoe/Eto.Parse/blob/b15254c3a5ab70e697ac598bbf4e81013a02af29/Eto.Parse/ParserWriterArgs.cs#L9) : class de base des arguments de WriteParser()
  - maintiens une pile des Writer rencontrés, et le niveau
  - génère automatiquement des noms pour les Parser qui n'en portent pas
-   