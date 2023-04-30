Le [Highliter](obsidian://show-plugin?id=highlightr-plugin)
# Fonctionnement
Insère des balises HTML `<mark class="hltr-yellow">en jaune</mark>`

> [!warning] On perd le formatage purement Markdown
> si le plugin n'est pas installé, on ne voit rien. Si on édite le markdown sur une autre plateforme, on ne verra rien (mais on aura quand même le markup)
> Le code source Markdown devient illisible

Exemple : surligner <mark class="hltr-yellow">en jaune</mark>

# Limites
- Peut-on mélanger le surlignage ? Non, car Obsidian empêche d'avoir une sélection  qui passe une limite de balise HTML. 
  Ex : Essayer avec : <mark class="hltr-orange">du<mark class="hltr-yellow"> jaune et du</mark> vert</mark>