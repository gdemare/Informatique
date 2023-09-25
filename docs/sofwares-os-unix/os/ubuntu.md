## Installer ubuntu en dual boot en partageant des fichiers avec Windows

1. Désactiver la sécurité dans le Bios.
2. Installer Windows.
3. Avec le logiciel gestionnaire de disques, créer une partition :
  * pour les fichiers partagés, formater en nts.
  * pour Ubuntu (au moins 50 Go), sans formatage.
4. Lancer l'installation d'Ubuntu avec Dual Boot.
5. Modifier l'ordre des programmes de boot en mettant, la partition efi en premier.
6. Installer les packages les plus `sudo apt-get install ubuntu-restricted-extras`

## Logiciels

Disponibles dans la logitèque Ubuntu :

* Brave, navigateur internet sans pub.
* Dessin de Romain F T, logiciel de dessins très simple.
* Mailspring, client email.
* Visual code
* Vlc, lecteur multi média.

Disponible sur le site internet de l'entreprise :

* Crytpomator
* [dropbox](https://www.dropbox.com/install-linux)

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

Extensions a ajouter :

* Clipboard Indicator, pour avoir l'historique des copiés.

## Flathub

[Flathub](https://flathub.org/) logithèque avec les applications en appimage. Un exemple d'installation par le terminal `flatpak install flathub org.gnome.Music`.

* Cryptomator, logiciel de cryptage spécialisé pour le cloud.
* Github, pour gérer les fichiers github.
* Raisonnance, lecteur musique (attention jolie mais pas optimiser au 2023-09-20).
* Shortwave, radios en ligne.

## Logiciel par défaut

* `gnome-text-editor` éditeur de texte.
