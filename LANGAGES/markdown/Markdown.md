---
Tags: [Markdown]
---
Il n'existe pas de spécifications officielles, et il y a de nombreuses déclinaisons (`flavors`).
Le principal effort est [CommonMark](https://commonmark.org/)
Github a également défini une spécification [GitHub Flavored Markdown Spec](https://github.github.com/gfm/#what-is-github-flavored-markdown-)
# Markdown

Trucs et astuces pour Markdown

### images
L'inclusion d'une image se fait comme un lien, avec `!` (point d'exclamation) comme préfixe.
On peut fixer la largeur de l'image en ajoute un suffixe `|xxx` au nom du lien.

`![Engelbart|50](https://history-computer.com/ModernComputer/Basis/images/Engelbart.jpg)`
![Engelbart|50](https://history-computer.com/ModernComputer/Basis/images/Engelbart.jpg)

### liens
On peut mettre une URL sans les échappements (pour les espaces notamment) en mettant la cible du lien entre `<` et `>`
```md
[Lien](<http://domaine.fr/fichier avec espaces>)
```

### listes

#### items multilignes, ajouter 2 espaces à la fin de la première ligne

Example :
- item 1  
détails 1
- item 2

### Notes de bas de page
On peut soit inclure une note par une référence numérique sous la forme `[^1]`  [^1] ou sous la forme d'un nom `[^A]` [^A]. Une autre note[^2].
Le texte de la note apparait sur sa propre ligne. 
> [!warning] Les notes de bas de page qui ne sont pas visées n'apparaissent pas.

>[!warning] Les notes de bas de pages en mode lecture sont renumérotées. 
>Si on utilise des nombres pour référencer des notes, ce ne sont pas ces numéros qui seront affichés

>[!Tip] Mettre les liens en note de bas de page permet de s'assurer que même si on change le titre d'une note, la phrase conservera une forme correcte

On peut aussi créer une note directement dans le texte avec la syntaxe `^[texte de la note]`. Exemple ^[note de bas de page inline]

Pour un article sur l'usage des notes de bas de page [Quick Tip: Footnotes in Obsidian - Obsidian Rocks](https://obsidian.rocks/footnotes-in-obsidian/?utm_content=cmp-true)
	Le plugin [^4]   permet d'insérer des notes [^Citation]  

[^1]: Ma note de bas de page
[^A]: Ma note de page avec un nom
[^2]: Ma troisième note de bas de page (porte le numéro 2 dans le source)
[^4]: Ma nouvelle note
[^Citation]: Les cordonniers sont souvent les plus mal chaussés
[^99]: une note jamais visé dans le document


### Emoji
#Emoji

Exemples : [Complete list of github markdown emoji markup](https://gist.github.com/rxaviers/7360908)

| :bowtie: `:bowtie:` | :smile: `:smile:` | :laughing: `:laughing:` |