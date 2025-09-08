#### Ajouter une AppImage dans la liste des applications

Créer un fichier `cryptomator.desktop` dans le répertoire `/home/guigui/.local/share/applications`

``` bash
[Desktop Entry]
Version=1.17.1
Type=Application
Name=Cryptomator
TryExec=/home/guigui/Applications/cryptomator.AppImage
Exec=/home/guigui/Applications/cryptomator.AppImage
Comment=Cryptomator
Icon=/home/guigui/Applications/cryptomator.png
Actions=Editor
Terminal=false
```

̀`update-desktop-database ~/.local/share/applications/` mettre à jour les applications.
`sudo dpkg -i package` installer un package deb.

`brave --app=https://www.youtube.com` ouvrir un url avec brave.

**[Domain Name System](https://fr.wikipedia.org/wiki/Domain%20Name%20System "https://fr.wikipedia.org/wiki/Domain Name System")** (ou DNS, **système de noms de domaine**)

arcMenu pour avoir le même menu que window.

Installation de windows 
email a@a.com
[atlas](https://docs.atlasos.net/getting-started/installation/) nettoie windows après une installation.
[[modules supplémentaires]]
### Virtual box

 Pour l'installation de virtual box, il est recommandé d'utiliser le terminal.

1. Activer VT dans le bios virtualization technologie.
A vérifier :

* `sudo rmmod kvm_intel` apparement 
* CTRL (DROITE) + c

