
- `brave --app=https://www.youtube.com` ouvrir un url avec brave.
## Installer ubuntu en dual boot en partageant des fichiers avec Windows

1. WindowsDésactiver la sécurité dans le Bios.
2. Installer Windows.
3. Avec le logiciel gestionnaire de disques, créer une partition :
  * pour les fichiers partagés, formater en nts.
  * pour Ubuntu (au moins 50 Go), sans formatage.
4. Lancer l'installation d'Ubuntu avec Dual Boot.
5. Modifier l'ordre des programmes de boot en mettant, la partition efi en premier.
6. Installer les packages les plus `sudo apt-get install ubuntu-restricted-extras`
## Rclone, les clouds (OneDrive - 31, Google Drive - 18, Dropbox - 13)

[rclone](https://rclone.org/downloads/)

1. Créer un dossier ou sera copier les fichiers.
2. Configurer Rclone `rclone config`
3. New remote > `n`
4. Nom du remote (OneDrive, Dropbox)

Configuration pour OneDrive :

5. Laisser vide client_id et client_secret
6. Pas de configuration avancée
7. Entrer et se logger
8. Selection 1 pour personel.
9. yes pour confirmer.
10. `q` pour quitter
11. dans le dossier, exécuter : `rclone --vfs-cache-mode writes mount OneDrive: ~/Onedrive &`
12. Créer un script `rclone --vfs-cache-mode writes mount OneDrive: ~/Onedrive & notify-send "Onedrive Connected" "Microsoft successfully mounted"`
## Ajouter un dépôt

1. Ouvrir `Logiciels et mises à jour`
2. Autres logiciels et Ajouter, le lien vers le dépôt.

Il est possible de le faire directement en ajouter une ligne au fichier : 
`/etc/apt/sources.list`
## Ajouter le programme pour personnaliser gnome

### gnome-shell-extension-manager

!!! note
	Le programme s'appelle Extensions.

Extensions à ajouter :

* Clipboard Indicator, pour avoir l'historique des copiés.
* Caffeine, désactiver la mise en veille automatique.
* Emoji Selector sélectionner les émoji.
* Vitals surveiller l'activité des 
* Emoji copy pour avoir les emoji accessibles facilement.
* tiling shell paramètrer les zones de chaque écran.
* search light
* arcMenu pour avoir le même menu que Windows. 
* dashpanel
* bluetooth battery meter ajouter la batterie restante aux appariels bluetooth

## Flathub

[Flathub](https://flathub.org/) logithèque avec les applications en appimage. Un exemple d'installation par le terminal `flatpak install flathub org.gnome.Music`.

* Cryptomator, logiciel de cryptage spécialisé pour le cloud.
* Github, pour gérer les fichiers github.
* Gapless, lecteur musique chiant car il sépare les albums par années.
* Apparamment une des meilleurs options consiste à utiliser Music Player Daemon un lecteur de musique en ligne de commande avec une interface. Interface cool
* Shortwave, radios en ligne.
* Musicpod lecteur de musique.

### Media Player Deamon

1. Installer `sudo apt install mpd mpc` 
2. Configurer les fichiers et le dossier de la bibliothèque :

```
music_directory     "~/Musique"
playlist_directory  "~/.config/mpd/playlists"
db_file             "~/.config/mpd/database"
log_file            "~/.config/mpd/log"
pid_file            "~/.config/mpd/pid"
state_file          "~/.config/mpd/state"
sticker_file        "~/.config/mpd/sticker.sql"

bind_to_address     "127.0.0.1"
port                "6600"

audio_output {
    type            "pulse"
    name            "PulseAudio"
}
```

``` bash 
mkdir -p ~/.config/mpd/playlists
touch ~/.config/mpd/{database,log,pid,state,sticker.sql}
```

## Logiciel par défaut

* `gnome-text-editor` éditeur de texte.

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
- `update-desktop-database ~/.local/share/applications/` mettre à jour les applications.
`sudo dpkg -i package` installer un package deb.


**[Domain Name System](https://fr.wikipedia.org/wiki/Domain%20Name%20System "https://fr.wikipedia.org/wiki/Domain Name System")** (ou DNS, **système de noms de domaine**)
### Virtual box

 Pour l'installation de virtual box, il est recommandé d'utiliser le terminal.

1. Activer VT dans le bios virtualization technologie.
A vérifier :

* `sudo rmmod kvm_intel` apparemment 
* CTRL (DROITE) + c