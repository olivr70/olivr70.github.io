##
Github Pages permet de publier un site web statique à partir d'un repo Gihub. 
Le fonctionnement par défaut est de publier le site avec le moteur [Jekyll](https://docs.github.com/fr/pages/setting-up-a-github-pages-site-with-jekyll/about-github-pages-and-jekyll). Il est possible de configurer largement le site, et même le processus de génération (on peut même utiliser un autre moteur que Jekyll).

La [documentation de GitHub Pages](https://docs.github.com/fr/pages/getting-started-with-github-pages/about-github-pages) est très complète.

## Le langage de template Liquid

Les pages sont considérées comme des templates, dans lesquelles tous les segments au format [Liquid](https://jekyllrb.com/docs/liquid/) seront substitués

Exemple : pour générer dynamiquement un sommaire
```liquid
{% for page in site.pages %}
  {% if page.categories contains 'algorithme' %}
- x [{{page.title}}]({{page.url}})
  {% endif %}
{% endfor %}
```



## exécution locale de Jekyll

`bundle exec jekyll serve` lance le serveur local

### installation
- Création du fichier **Gemfile**
```
source 'https://rubygems.org'
gem 'github-pages', group: :jekyll_plugins
```
| `ruby --version` // ruby 2.X.
- `sudo apt-get install ruby2.5-dev` // même version, nécessaire pour commonmarker
- `gem install bundler`// installe [Bundler](https://bundler.io/)
- `sudo gem install commonmarker -v '0.17.13' --source 'https://rubygems.org/'`
- `bundle install`

Article très complet de GitHub : [Setting up your GitHub Pages site locally with Jekyll - GitHub Help](https://help.github.com/en/articles/setting-up-your-github-pages-site-locally-with-jekyll#step-4-build-your-local-jekyll-site)