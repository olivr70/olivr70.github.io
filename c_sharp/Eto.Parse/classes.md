# [Eto.Parse](./index) Les classes de base

## Le Parser

- _AddError_ : si true, alors en cas d'échec, ce parser ajoute une erreur dans ParserArgs
  - Quand on donne un Name au Parser, alors AddError est mis à true, sauf s'il a été explicitement fixé par l'utilisateur
- _AddMatch_ : si true, alors en cas de succès, ce parser ajoute une entrée dans la MatchCollection de ParserArgs
  - Quand on donne un Name au Parser, alors AddMatch est mis à true, sauf s'il a été explicitement fixé par l'utilisateur

## L'itération sur les Parser
Pour itérer sur les parser, Eto.Parse utilise un Pattern récursif, avec accumulation de l'état dans un ...Args
- **ParserChain** : classe de base de tous les ...Args
  - _Parents_ : tous les Parser déjà examinés
  - _Push()_ et _Pop()_ : ajout et retrait d'un parent
- **ParserInitiliazeArgs** : utilisé pour l'initialisation des parser (en particulier pour les problèmes de LeftRecursion)
 - _Grammar_ : la grammaire
 - _Parent_ : le plus proche parent
 - _RecursionFixes_ : ???
- **ParserErrorArgs** :  
  - utilisé par _Parser.GetErrorMessage()_
  - _Detailed_ : true pour avoir les erreurs détaillées
- **ParseArgs** : 
  - _Root_ : une instance de [GrammarMatch](#grammarmatch))
  - _nodes_ : utilisé pour construire l'arbre des résultats (pile de MatchCollection)
    - utilise une SlimStack : suivant les cas, Pop ou PopKeep vont avoir pour effet de
      laisser des slots de la pile à null, ou avec une MatchCollection vide
    - _Push()_ : 
    - _PopSuccess()_ : fusionne la MatchCollection avec celle du parent
    - _PopMatch()_ : le Parser a matché, on ajoute le match à la MatchCollection parent
    - _PopFailed()_ : les matches sont oubliés
  - _errors_ : la liste des erreurs
    - _ErrorIndex_ : la position de la dernière erreur
    - _AddError(Parser)_ : joute l'erreur indiqué par le Parser
 
### Accéder au résultat d'une analyse

- **Match** : chaque item identifié dans le flux donne lieu à la création d'un Match
  - _Success_ : true si le Matche a réussi (si _Length_ >= 0)
  - _Empty_ : si c'est un Matche de longueur 0
  - _Index_ et _Length_ : l'emplacement (si négatif, c'est un échec)
  - _Text_ : le texte reconnu
  - _Line_ : le numéro de ligne du début du match (attention, recaculé à chaque fois avec StringScanner)
  - _Value_ : la valeur (obtenue par un appel à la méthode _GetValue() du Parser)
  - _Name_ : le nom du match
  - _Parser_ et _Scanner_ permettent de savoir qui a produit ce Match
  - _Matches_ : une MatchCollection associée à ce match, ce qui permet de créer un arbre
- **MatchCollection** : une liste de Match, avec des méthodes utilitaires
 - _Find(string,bool)_ : retourne les Match avec ce nom, de manière récursive si deep est true
 - _[string]_ : retourne le premier Match avec ce nom
- <a name="grammarmatch">**GrammarMatch**</a> : un match avec une liste d'erreur. C'est toujours l'instance Root
    - _Grammar_ : la grammaire
    - _Scanner_ : le texte scanné
    - _ErrorMessage_ : 

### Les Scanner
- **Scanner** : l'abstraction du texte à scanner
  - _Position_ : la position courante
  - _IsEof_ : true à la fin du texte
  - _Peek()_ : le caractère à la position courante
  - _ReadChar()_ : lit le caractère à la position courante et avance
  - _Advance(int)_ : avance de n caractères (ne fait rien et retourne -1 s'il n'y a pas 
  suffisament de caractères restant)
  - _ReadString(string, bool) : si le texte est présent à la position courante, avance de sa longueur
  - _Substring_() : retourne la sous-chaine correspondante dans le texte. Si Length va au delà de 
  la longueur, le résultat retourné à tronqué
- **StringScanner** : texte à scanner conservé dans une string

## Les Writer
Ils sont utilisés pour afficher la structure d'un Parser.

Deux writers sont implémentés : 
- DisplayWriter
- [CodeParseWriter](https://github.com/picoe/Eto.Parse/blob/master/Eto.Parse/Writers/CodeParserWriter.cs)

Les principales classes :
- IParserWriter : tout objet avec la méthode principale WriteParser()
- [ParserWriterArgs](https://github.com/picoe/Eto.Parse/blob/b15254c3a5ab70e697ac598bbf4e81013a02af29/Eto.Parse/ParserWriterArgs.cs#L9) : class de base des arguments de WriteParser()
  - maintiens une pile des Writer rencontrés, et le niveau
  - génère automatiquement des noms pour les Parser qui n'en portent pas


## Les classes utilitaires

- **SlimStack** : une pile qui ne libère pas l'espace alloué
 - _Pop()_ : affecte la valeur par défaut au segment alloué
 - _PopKeep()_ : retounr le haut de la pile, en laissant une référence dans la List sous-jacente
   - utilisé pour permettre la réutilisation des MatchCollection(), qui sont simplement Clear() au lieu d'être
     réallouées