# [Eto.Parse](DEV/c_sharp/Eto.Parse/index.md) - API Fluent



## Principales clases

### Les différents Parser

- <a name="iinverseparser"></a>**IInverserParser** : Tout parser avec une propriété _bool Inverse_. 
  - Implémenté par : CharTerminal, SurrogatePairTerminal, LookAheadParser
  - l'opérateur _operator !_ et la méthode d'extension _Inverse()_ sont définis pour ces Parser 
- <a name="iseparateedparser"></a>**ISeparatedParser** : Tout parser avec une propriété _Separator_.
  - Implémenté par : SequenceParser, RepeatParser
  - la méthode d'extension _SeparateBy()_ est utilisable pour ces parsers. Elle permet de modifier 
  la propriété _Separator_
- **ListParser** : Tout parser avec une liste de sous-parsers (Children)
  - Dérivé par : AlternativeParser, SequenceParser
  - implémente Find, InnerReplace, Contains
  - _Add()_ permet d'ajouter un ou plusieurs Parser

### Les terminaux
Les terminaux standards sont accessibles comme des propriétés de la classe **Terminals**, qui déclare en particulier
de nombreux CharTerminal : 
- **Digit** : `DecimalDigitNumber (Nd)`
- **HexDigit**, (DecimalDigitNumber ou /A-Fa-f/)
- **Letter**, (Char.IsLetter(), soit toutes les catégories de lettres Unicode : LowercaseLetter, UppercaseLetter, TitlecaseLetter, ModifierLetter, OtherLetter)
- **LetterOrDigit**, 
- **WhiteSpace** ([Char.IsWhitespace](https://docs.microsoft.com/fr-fr/dotnet/api/system.char.iswhitespace)), 
- **SingleLineWhitespace**, Whitespace, sauf **CR** (`\r`) et **LF** (`\n`)
- **Punctuation** (Char.IsPunctuation()), 
- **ControlCodes** (Char.IsControl()), 
- **Printable** (inverse de ControlCodes)
- **Symbol** (Char.IsSymbol())
- **CharRangeTerminal** : créé avec `Terminals.Range()`

Les classes de terminaux sont :
- **AnyCharTerminal** : accepte tout caractère
- **BeginParser** et **EndParser** : matche 0 caractère, au début (position du scanner à 0) et à la fin du Scanner (Eof() à true)
- **EolTerminal** : reconnait CR/LF, LF et CR seuls
- **LiteralTerminal**  : reconnait une chaine constante, 
  - _CaseSensitive_ initialisé par défaut à celui de la grammaire, mais peut être forcé 
  - Ex  : ```new LiteralTerminal { Value = "null", Name = "null", CaseSensitive = false };```
- **StringParser**
  - Ex: ```new StringParser { AllowEscapeCharacters = true, Name = "string" };```
- **NumberParser** : reconnait un nombre
  - _AllowExponent_ indique si on accepte la notation avec Exx
  - _AllowSign_ si on accepte les nombre signés
  - _AllowDecimal_ si on accepte les nombres réels
  - _DecimalSeparator_ (`.` par défaut)
  - _ValueType_ (**decimal** par défaut) le type de nombre attendu, qui doit avoir une méthode static `Parse(string, NumberFormat) ` (comme tous les types numériques standard de .Net)
  - _Culture_ le CultureInfo utilisé (**CultureInfo.CurrentCulture** par défaut)
- **BooleanTerminal** : 
  - Les propriétés _TrueValues_ et _FalseValues_ sont exposées. Par défaut reconnait `true`/`false`, `yes`/`no`, `on`/`off` et `1`/`0`
  - _CaseSensitive_ initialisé par défaut à celui de la grammaire, mais peut être forcé 
- **RepeatCharTerminal** : reconnait une liste de RepeatCharItem (soit une fonction de test Func<char,bool>)
  - Ex  : ```new RepeatCharTerminal(new RepeatCharItem(char.IsWhiteSpace), ','```

### Les groupes (ou non terminaux)

- **UntilParser** : Capture un segment jusqu'à l'occurence d'un motif de fin (un Parser)
  - _Inner_ est le Parser qui marque la fin
  - _Minimum_ et _Maximum_ limitent le nombre de caractères entre la position courante et le motif
  - _Capture_ : si true, le motif de fin est inclus dans le texte capturé
  - _Skip_ : si true, tous les caractères jusqu'à la fin du motif de fin sont ignorés
- **SequenceParser** : pour capturer, doit trouver tous les items
  - _Add()_ ajout un ou plusieurs parsers à la séquence
- **ExceptParser** : une variante du parser Inner qui ne matche pas dans certains cas
  - la méthode d'extension _Except()_ permet de créer un nouveau ExceptParser
  - _Except_ le parser qui reconnait les exceptions à ne pas reconnaitre
- **AlternativeParser** : 
- **LookAheadParser** : Match sans avancer si son InnerParser matche
  - C'est un [IInverseParser](#iinverseparser) : si `Inserve = true`, alors il matche si Inner ne matche pas
  - La méthode d'extension _Not()_ permet de transformer tout Parser en LookAheadParser inversé
  - La méthode d'extension _NotCaptured()_ permet de transformer tout Parser en LookAheadParser
  - La méthode d'extension _FollowedBy()_ retourne une Séquence this et un LookAheadParser
  - La méthode d'extension _NotFollowedBy()_ retourne une Séquence this un LookAheadParser inversé
