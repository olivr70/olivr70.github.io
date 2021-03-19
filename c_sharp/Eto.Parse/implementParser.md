# [Eto.Parser](./index) : Implémenter son propre Parser

On sous-classe : 
- **Parser** pour un parser simple
- **UnaryParser** pour un parser avec un seul enfant
- **ListParser** si notre parser à une série d'enfants (ex : **AlternativeParser**)

On peut ajouter :
- **ISeparatedParser**
- **IInverseParser**

Il faut réécrire au minimum : 
- le constructeur de copie (qui reçoit un ParserCloneArgs) et _Clone()_
  - pour construire une copie d'un parser, il faut faire appel à _args.Clone()_, qui gère l'existence
    d'éventuels cycles
- _InnerParse()_ : 
  - retourner le nombre de caractères consommés (ou -1 en cas d'échec)
  - en cas d'échec, il faut laisse le scanner à la même position
     - éventuellement en forçant la position du Scanner avec `args.Scanner.Position = pos;`

Si on a une ou plusieurs propriétés de type Parser, il faut réécrire 
- _GetChildren()_ : pour lister nos Parser dans la liste
  `return new [] { Except }.Where(r => r != null).Concat(base.GetChildren());` 
- _InnerReplace_ : pour faire le Replace dans nos Parser
    `base.InnerReplace(args); Except = args.Replace(Except);`

On peut redéfinir : 
- _InnerInitialize()_ : en appelant `base.InnerInitialize()` à la fin
  - soit pour initialiser CaseSensitive : `caseSensitive = CaseSensitive ?? args.Grammar.CaseSensitive;`
- _GetErrorMessage()_ :
  - pour générer un message d'erreur plus détaillé quand il est demandé
- _GetValue()_ : calcule la valeur correspondante au texte
  - L'implémentation par défaut renvoie le texte reconnu
  - On peut lancer une ArgumentException s'il y a un problème de syntaxe
  - ex : StringParser : remplace les caractères d'échappement