## Logiciels

Disponibles dans la logithèque Ubuntu :

* Brave, navigateur internet sans pub.
* Dessin de Romain F T, logiciel de dessins très simple.
* Flash info, lecteur de flux RSS.
* Flameshot, logiciel de capture d'écran complet.
- [Foliate](https://johnfactotum.github.io/foliate/) lecteur d'ebooks installable via Flathub.
- GIMP pour les photos et les images.
* gThumb visionneuse d'image
- Mission center équivalent au gestionnaire des tâche sur Windows.
* Vlc, lecteur multimédia.

Disponible uniquement depuis Github :

* [NOI](https://github.com/lencx/Noi) client desktop pour les modèles d'IA (chat GPT...).
* [SpotX-bash](https://github.com/SpotX-Official/SpotX-Bash), bloqueur de pub sur la version desktop de spotify.

[Flathub](https://flathub.org/) logithèque avec les applications en appimage. Un exemple d'installation par le terminal `flatpak install flathub org.gnome.Music`. 
Dispo sur Flathub :

* Github, pour gérer les fichiers Github.
* Gapless, lecteur musique chiant car il sépare les albums par années.
* Shortwave, radios en ligne.
* Musicpod lecteur de musique.

Lecteur musique : apparemment une des meilleurs options consiste à utiliser Music Player Daemon un lecteur de musique en ligne de commande avec une interface. Interface cool.

### Thunderbird

Exporter ses emails dans un fichier :

1. sélectionner le dossier (ou l'email)
2. outils > exporter
### Dualboot

###Problème Bluetooth 

[Pairing Bluetooth Devices in Dual Boot with Linux Ubuntu and Windows 10/11](https://gist.github.com/madkoding/f3cfd3742546d5c99131fd19ca267fd4) problèmes bluetooth. 

Récupérer la clé utilisée par Windows.

1. `/media/guigui/Disque-OS/Windows/System32/config` ouvrir la configuration de média.
2. `chntpw -e SYSTEM`
3. `cd \ControlSet001\Services\BTHPORT\Parameters\Keys` aller dans Keys.
4. `ls` lister les id disponibles.
5. `cd clé` exemple `cd 10f60a80c883` entrer dans le périphérique.
6. `ls` copier la clé2 (value name exemple `785ea2d4d93b`).
7. `hext clé2` (value name) traduire la clé en hexadécimale (supprimer les espaces ex : `1E BF 2F C0 4E 57 EA A3 D1 43 2C B9 78 2C 7C CC` -> `1EBF2FC04E57EAA3D1432CB9782C7CCC`). 

Aller dans :

1. `cd /var/lib/bluetooth/`
2. `ls` récupérer l'id (`10:F6:0A:80:C8:83`).
3. `cd id` rentrer dans le périphérique (`cd 10:F6:0A:80:C8:83`).
4. `cd id2̀ (`cd 78:5E:A2:D4:D9:3B`)
5. Modifier le fichier avec `nano info` : remplacer `Key=idHex` de la section `[LinkKey]` (par exemple `1EBF2FC04E57EAA3D1432CB9782C7CCC`).




- `brave --app=https://www.youtube.com` ouvrir un url avec brave.
- `brave-browser --new-window "https://ton-lien.com"` ouvrir un lien avec Brave.
## Installer Ubuntu en dual boot en partageant des fichiers avec Windows

1. Windows Désactiver la sécurité dans le Bios.
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

rsync -av --delete-after /home/guigui/Musique/MaMusique
mtp://TCL_TCL_50_NXTPAPER_5G_MJCIIR9D7P4T75KV/M%C3%A9moire%20interne%20partag%C3%A9e/Music/MaMusique/
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
* Removable Drive Menu affiche les périphériques branchés.
* Application Hotkey ajouter des raccourcies clavier.
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
Name=ChatGTP
Exec=brave-browser --new-window "https://ton-lien.com"
Comment=Cryptomator
Icon=/home/guigui/Applications/chat.png
```
- `update-desktop-database ~/.local/share/applications/` mettre à jour les applications.
`sudo dpkg -i package` installer un package deb.

**[Domain Name System](https://fr.wikipedia.org/wiki/Domain%20Name%20System "https://fr.wikipedia.org/wiki/Domain Name System")** (ou DNS, **système de noms de domaine**)

## Virtualisation

### Virtual box

 Pour l'installation de virtual box, il est recommandé d'utiliser le terminal.

1. Activer VT dans le bios virtualization technologie.
A vérifier :

* `sudo rmmod kvm_intel` apparemment 
* CTRL (DROITE) + c

PB avec l'accélérateur :
1. `sudo modprobe -r kvm_intel`
2. `/etc/modprobe.d/blacklist.conf`.
### Quickemu

 est un logiciel de virtualisation qui optimise les paramètres des vm en fonction des caractéristiques de l'ordinateur.
Tous les informations pour installer une vm sont sur [Quickemu github](https://github.com/quickemu-project/quickemu).

- `quickemu --vm macos-big-sur.conf --display spice` émuler un système d'exploitation.
### MacOS

Pour [OpenCore Legacy Patcher](https://github.com/dortania/OpenCore-Legacy-Patcher/) pour permettre au ancien mac d'être mis à jour.
### Mettre à jour les firmwares

- `fwupdmgr get-updates` vérifier la présence de màj.
- `sudo fwupdmgr update` télécharge et installe toutes les màj.