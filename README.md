# Github pages for Olivier CHEVET

Ces pages contiennent principalement de la documentation utile sur les outils que j'utilise

- [Dev tools](/dev-tools)

- [Bash](./bash)
  - [History](/bash/history)
- [Linux](/linux)
  - [Commandes diverses](/linux/general)
  - [Dropbox](/linux/dropbox)
  - [Maintenance](/linux/maintenance)
  - Stockage
    - [File system](/linux/filesystem)
    - [LVM](/linux/lvm)
  - Initialisation
    - [cron](/linux/cron)
    - [init.d](/linux/init_d)
    - [runit](/linux/runit)
    - [systemd](/linux/systemd)
  - [Network](/linux/network)
  - [Performance](/linux/perf)
  - [Dropbox](/linux/dropbox)
  - [User](/linux/user)
- [Markdown](/markdown)
- [Nginx](/nginx)
  - [SSL](/nginx/ssl)
- [Node.js](/node)
  - [Modules](/node/modules)
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
