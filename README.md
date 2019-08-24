# Github pages for Olivier CHEVET

Ces pages contiennent principalement de la documentation utile sur les outils que j'utilise

- [Dev tools](/dev-tools)

- [Bash](./bash)
  - [History](/bash/history)
- [Linux](/linux)
  - [Commandes diverses](/linux/general)
  - [Maintenance](/linux/maintenance)
  - [File system](/linux/filesystem)
  - [Network](/linux/network)
  - [Performance](/linux/perf)
- [Node.js](/node)
- [Pass](/pass)
- [Ssh](/ssh)
- [Vim](/vim)

et aussi
- [GitHub Pages](/github-pages)
- [LibreOffice](/libreoffice)

Menu
{% for page in site.pages %}
  {% if page.categories contains 'fruit' %}
- x [{{page.title}}]({{page.url}})
  {% endif %}
{% endfor %}


Et aussi les notes sur plusieurs tâches réalisées (ou en cours)

- [Tasks](./tasks)
