# Configuration d'OpenOffice

## le dossier de profil

On le passe à openOffice par la variable d'environnement **UserInstallation**
- une URL de type file:/// le chemin est considéré comme absolu
- ce chemin peut contenir des références à des macros
    - $USERNAME
    - $SYSUSERCONFIG (défaults to %APPDATA%)
    - $SYSUSERHOME (defaults to %USERPROFILE%\Documents)
    - $ORIGIN = chemin de bootstrap.ini
    - $OOO_BASE_DIR
    - ${_OS}
    - ${_ARCH}

les références à ces variables peuvent inclure une variable définie dans le fichier .ini.
Ex : `${$OOO_BASE_DIR/program/bootstrap.ini:UserInstallation}`

La valeur peut être fixée dans **bootstrap.ini/[Bootstrap]** 
Sa valeur par défaut est `$SYSUSERCONFIG/OpenOffice/4` ou `$SYSUSERCONFIG/LibreOffice/4`

## les fichiers de configuration

Ils se trouvent dans le répertoire **program** (qui contient les .exe)

### soffice.ini
Premier fichier de démarrage (il porte le nom de l'exe). Il doit définir URE_BOOTSTRAP
définit:
- **URE_BOOTSTRAP** : le chemin vers fundamental.ini Ex : `${ORIGIN}/fundamental.ini`

### fundamental.ini
Le fichier avec toutes les variables essentielles pour démarrer OpenOffice. Il est trouvé 
avec la variable `URE_BOOTSTRAP` qui se trouve dans *soffice.ini*.

De nombreuses variables sont définis par référence à d'autres fichiers ini :
- louno.ini
- bootstrap.ini:UserInstallation

### bootstrap.ini
définit **UserInstallation**

### setup.ini
définit :
- **ProductCode** : le GUID du produit dans la registry
- **FINDPRODUCT** : le sous chemin dans la registry (à partir de CURRENT_USER ou LOCAL_MACHINE).
  Ex (OpenOffice) : `Software\OpenOffice\OpenOffice\4.1.10\{3EEBF9B9-FBD1-4717-8FFC-57E28D441132}` 
  Ex (LibreOffice) : `Software\LibreOffice\Layers\LibreOffice\7.1`
- **INSTALLLOCATION** : Ex : `C:\Program Files (x86)\OpenOffice 4\`
- **UREINSTALLLOCATION** : ex : `C:\Program Files (x86)\OpenOffice 4\URE\\`

### version.ini
Définit les informations sur la version (nom du produit, version, liens pour update)