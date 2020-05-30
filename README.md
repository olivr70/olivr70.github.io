# Github pages for Olivier CHEVET

Ces pages contiennent principalement de la documentation utile sur les outils que j'utilise

- [Dev tools](/dev-tools)
- [Ansible](/ansible)

- Languages
  - [Bash](./bash)
    - [History](/bash/history)
  - [Markdown](/markdown)
  - [PowerShell](/powershell)
  - [SPARQL](/sparql)
- [Git](./git)
- [Linux](/linux)
  - [Commandes diverses](/linux/general)
  - [apt](/linux/apt)
  - [cron](/linux/cron)
  - [Docker](/docker)
  - [Maintenance](/linux/maintenance)
  - Stockage
    - [File system](/linux/filesystem)
    - [LVM](/linux/lvm)
  - Initialisation
    - [cron](/linux/cron)
    - [init.d](/linux/init_d)
    - [runit](/linux/runit)
    - [systemd](/linux/systemd)
    - [cloud-init](/linux/cloud-init)
  - [Network](/linux/network)
  - [Pass](/pass)
  - [Performance](/linux/perf)
  - [Ssh](/ssh)
  - [User](/linux/user)
  - [Terminator](/linux/terminator)
  - [Vim](/vim)
- Hosting
  - [Dropbox](/linux/dropbox)
  - [GitHub Pages](/github-pages)
  - [Hetzner - hcloud](./hosting/hetzner)
  - [NGINX](/nginx)
    - [SSL](/nginx/ssl)
  - [Node.js](/node)
    - [Modules](/node/modules)
- [Formats](/formats)
  - [Unicode](/formats/unicode)
Développement
- [SSL](/css)

et aussi
- [LibreOffice](/libreoffice)


Menu
{% for page in site.pages %}
  {% if page.categories contains 'fruit' %}
- x [{{page.title}}]({{page.url}})
  {% endif %}
{% endfor %}


Et aussi les notes sur plusieurs tâches réalisées (ou en cours)

- [Tasks](./tasks)
