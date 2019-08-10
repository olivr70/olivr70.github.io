### Description

Voir [postpack hook has no access to the generated .tgz for inspection - 💡 ideas - npm forum](https://npm.community/t/postpack-hook-has-no-access-to-the-generated-tgz-for-inspection/9025)

### Analyse

pack.js

- export pack()

  - pack\_() pour chaque argument en ligne de commande

    - crée un fichier `${name}-${mani.version}.tgz`
    - invoque soit

      - `packFromDirectory()`

        - `prepareDirectory()`
          - invoque "prepare"
        - invoque "prepack"
        - crée un archive temporaire
        - fait la liste des fichiers à ajouter avec [packlist](https://www.npmjs.com/package/npm-packlist)
        - génère l'archive temporaire

        - calcule `getcontents()`
        - copie l'archive temporaire à l'emplacement souhaité
        - invoque "postpack"

      - packFromPackage()
        - extrait l'archive depuis npmjs (avec [pacote.tarball.toFile](https://www.npmjs.com/package/pacote#pacotetarballtofilespec-dest-opts))
        - n'invoque **aucun hook**
