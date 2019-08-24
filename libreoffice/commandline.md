Libreoffice commande linge

### Lancement

Tous les arguments : [Command-line arguments in LibreOffice | dniM ruoY nepO](https://dnimruoynepo.blogspot.com/2016/12/command-line-arguments-in-libreoffice.html)

### conversion de fichier

#### en ligne de commande

Attention : uniquement si aucune autre instance de Libreoffice n'est démarré
```soffice -env:UserInstallation=file:///tmp/tempprofile --headless --convert-to <TargetFileExtension>:<NameOfFilter> FileName ```
soffice
- `-env:`UserInstallation=file:///tmp/tempprofile - nécessaire pour permettre un fonctionnement
  même si LibreOffice est déjà démarré par ailleurs
- `--headless` - devenu inutile
- `--convert-to `
  -  **extension>** 
  -  **<extension**:**filter** 
-  **FileName** - chemin vers le fichier à convertir

Les formats !
- `csv`
- `html`
- `pdf`
- `txt`

#### depuis Node

avec le module npm [libreoffice-conver](https://www.npmjs.com/package/libreoffice-convert)
