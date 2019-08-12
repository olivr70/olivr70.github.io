##

### exécution locale

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