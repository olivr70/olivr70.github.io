## installation

Résumé de l'article [How to Sync Microsoft OneDrive with Linux - Make Tech Easier](https://www.maketecheasier.com/sync-onedrive-linux/)

Commencer par
- `sudo apt install libcurl4-openssl-dev git`
- `sudo apt install libsqlite3-dev`
puis (18.04 et suivant)
- `sudo snap install --classic dmd && sudo snap install --classic dub`

puis
- `git clone https://github.com/abraunegg/`
- et compiler  

```
cd onedrive
./configure
make
sudo make install
```

**Essai le 27 janvier** = :error: installation OK, mais la connexion avec OAuth est infructueuse 
(page blanche sur le site de Microfost : impossible d'obtenir l'URL de connexion)