---
Tags: [Obsidian, Markdown]
---
- [ ] Les informations sur les capacités particulières de [[PKM/Outils de PKM/OBSIDIAN/index]] pour le formatage. Voir [[LANGAGES/markdown/Markdown|Markdown]] pour le formatage de base.
# Liens
- Deux syntaxes
	- classique : `[TITRE DU LIEN](url)`
	- Wikilink : `[[NOM de la page]]`
		- On peut préciser un nom de lien `[chemin|titre]`
- Lien vers un titre dans une page en ajoutant `#`
- Possibilité de créer une ancre et lier vers un paragraphe (***spécifique à Obsidian***)
	- Création de l'ancre : en ajoutant `^NOM` à la fin 
		- Example d'ancre ^ANCRE
	- Lien vers l'ancre en ajoutant `#^NOM` dans le lien
		- Exemple de lien : [[Formatage sur Obsidian#^ANCRE]]
# Callouts

Une série de lignes commençant par `>` sont regroupées dans un bloc
> Un bloc mis en évidence
> peut se dérouler sur plusieurs lignes

Si la première ligne du bloc est `[!TYPE]` alors le bloc est typé, et mis en évidence avec une icône et des couleurs spécifiques. Voir [Callouts - Obsidian Help](https://help.obsidian.md/Editing+and+formatting/Callouts).

On peut mettre  : 
- **note**
- **abstract**, summary, tldr
- **info**
- **todo**
- **tip**, hint, important
- **success**, check, done
- **question**, help, faq
- **warning**, caution, attention
- **failure**, fail, missing
- **danger**, error
- **bug**
- **example**
- **quote**,cite

## Quelques exemples
>[!abstract]
>Mon premier abstract

> [!quote]
> Ma première citation
 
# Blocs 
Le triple BACKQUOTE marque un début de bloc. On peut préciser le formatage à appliquer si c'est un langage informatique : Ex : `md` pour _Markdown_

```md
| First name | Last name |
| ---------- | --------- |
| Max        | Planck    |
| Marie      | Curie     |
```
# Tables
utiliser `:--` pour les alignements

| Colonne 1 | Colonne 2 | Colonne 3 |
| :-- | :--: | --: |
| Valeur 1 | Valeur 2 | Valeur 3 |


| First name | Last name |
| ---------- | --------- |
| Max        | Planck    |
| Marie      | Curie     |

# Graphes (Mermaid)
Un bloc [[Mermaid]] est introduit comme un bloc de code
```md
```mermaid
\```
```
```
```

# Emojis
Les code d'emojis nécessitent le plugin [Emoji Short Codes](obsidian://show-plugin?id=emoji-shortcodes) (tous les codes sur [emojipedia.org](https://emojipedia.org))

S'il est installé, un menu apparait **quand on saisit un code d'emoji**.  
>[!info]
> Une option permet soit de fixer le comportement
> - remplacement immédiat du code d'emoji par le caractère correspondant. Exemple : 😄
> - comme dans Github Pages, de garder le code d'emoji dans le source et de le remplacer à l'affichage. Exemple : :smile:  

# Intégrer du HTML
les tags HTML sont directement supportés

Cette capacité est notamment utilisée pour intégrer des vidéos

<iframe width="280" height="160" src="https://www.youtube.com/embed/YJzLC-AAWHw" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" allowfullscreen></iframe>

On peut aussi intégrer des pages web dans une IFRAME. On peut utiliser un outil comme [Générateur d'IFrame | Créez du code iframe à intégrer dans n'importe quel site Web (aspose.app)](https://products.aspose.app/html/fr/iframe-generator) pour créer un code HTML conforme.
>[!warning] Obsidian ne préserve pas les cookies. Du coup la page affichée contient souvent la question aux nouveaux arrivants sur le site

Exemple sur Légifrance
<iframe src="https://www.legifrance.gouv.fr/juri/id/JURITEXT000047483071" name="myIFrame" scrolling="auto" width="80%" height="500px" style="border: solid #000000;"></iframe>