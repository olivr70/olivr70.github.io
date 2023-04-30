


## Incidence du contrôle de l'accès au dossiers protégés

### Configuration

Chercher "protection contre les virus et les menaces" puis
 "Protection contre les ransomware"

 - **Dossiers protégés** permet de voir et modifier la liste des dossiers dont l'accès est surveillé.
 - **Historique des blocs** permet de voir les blocs
  (Note : on peut aussi le voir dans le Event Viewer (eventvwr.exe)), *journaux des applications*/*Microfost*/*Windows*/*Windows Defender*/*operational**")
- **Autoriser une app...;** permet d'autoriser une app à approter des modifications aux dossiers protégés

#### Exemple de mention dans le EventViewer
```
L'apport de modification par C:\Program Files (x86)\OpenOffice 4\program\soffice.bin à %userprofile%\OneDrive\Documents a été bloqué par l'Accès contrôlé aux dossiers.
 	Heure de la détection : 2021-07-21T21:20:11.210Z
 	Utilisateur : LAPTOP-997C3L0T\ochev
 	Chemin d'accès : %userprofile%\OneDrive\Documents
 	Nom du processus : C:\Program Files (x86)\OpenOffice 4\program\soffice.bin
 	Version de la veille de sécurité : 1.343.1390.0
 	Version du moteur : 1.1.18300.4
 	Version du produit : 4.18.2106.6
```

