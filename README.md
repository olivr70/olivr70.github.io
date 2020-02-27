# Github pages for Olivier CHEVET

Ces pages contiennent principalement de la documentation utile sur les outils que j'utilise

- [Dev tools](/dev-tools)
- [Markdown](/markdown)
- [Ansible](/ansible)

- [Bash](./bash)
  - [History](/bash/history)
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
  - [Hetzner - hcloud](./hosting/hetzner)
  - [Nginx](/nginx)
    - [SSL](/nginx/ssl)
  - [Node.js](/node)
    - [Modules](/node/modules)
- [Formats](/formats)
  - [Unicode](/formats/unicode)
Développement
- [SSL](/css)
- [Markdown](/markdown)

et aussi
- [Dropbox](/linux/dropbox)
- [GitHub Pages](/github-pages)
- [LibreOffice](/libreoffice)
- [NGINX](/nginx)
- [PowerShell](/powershel)


Menu
{% for page in site.pages %}
  {% if page.categories contains 'fruit' %}
- x [{{page.title}}]({{page.url}})
  {% endif %}
{% endfor %}


Et aussi les notes sur plusieurs tâches réalisées (ou en cours)

- [Tasks](./tasks)
