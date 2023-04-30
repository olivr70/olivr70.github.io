>[!warning]
>- La syntaxe Mermaid est sensible à la casse
>- Obsidian ne support pas les extensions interactives (`click href`)
## entête
On commence le bloc par triple quote `mermaid`
sur la seconde ligne, on indique `graph LR` ou `graph TD`

## Les éléments de base
### La forme des noeuds
Le libellé des noeuds peut être précisé entre crochets ou parenthèses :
- `A[Bloc rectangulaire]` avec crochets
	- `A[Bloc parallèlogrames]` avec crochets/slash
	- `C[(bloc database)]` avec crochet/parenthèse
- `B(Bloc arrondi)` avec parenthèses
	- `D([bloc ovale])` avec parenthèse/crochet
	- `E((bloc rond))` avec double parenthèses
- `F{bloc diamant}` avec des accolades
	- `G{{bloc hexagone}}` avec des double accolades
```mermaid
graph LR
A1[Bloc rectangulaire] --> A2
A2[(bloc database)] --> A3 
A3[/parallèlogramme/] --> Fin
B1(Bloc arrondi) --> B2
B2([bloc ovale]) --> B3
B3((rond)) --> Fin
C1{diamant} --> C2
C2{{hexagone}} --> Fin
```
### types de liens
```mermaid
graph LR
A[simple] ---|"---"| Z[C'est la fin]
B[directionnel] -->|"-->"| Z
C[bidirectionnel] <-->|"<-->"| Z
D[Epais] ===|"==="| Z
E[avec bullet] --o|"--o"| Z
F[avec croix] --x|"--x"| Z

```



### liens nommés
En mettant `-- NOM` devant le lien (ex `-- mange -->`)
```mermaid
graph LR
Lion -- mange --> Antilope
```
### Longueur des liens
Le nombre de tirets permet d'influer sur la longueur des liens
```mermaid
graph LR
A -->|"-->"| B
C --->|"--->"| D
E =====>|"=====>"| F
```
## sequenceDiagram
```mermaid
sequenceDiagram
A ->> +B: Hello
A ->> +B: Hello !
B ->> +A: Hi !
```

## graph
```mermaid
graph LR
A[Antoine]
B[Olivier]
C[Maud]
A --> B
A --> C
C --> B
```
