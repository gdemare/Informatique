# Windows

## Installation

Pour limiter le nombre d'applications pré-installées, il choisir Anglais internationnal (English world). Il est également possible de personnaliser son installation avec le logiciel
de création de clés bootables Rufus.

Pour passer l'étape de connexion à compte Microsoft 

##### Utilitaire de création de clés bootables

Rufus est un petit utilitaire qui permet de bloquer l'installation de logiciels normalement préinstallé et de créer un compte microsoft pour pouvoir installer l'OS.

[ventoy](https://www.ventoy.net/en/index.html) outils qui transforme une clé USB en clé bootable. Une fois la clé formatée il suffit de copier l'iso.
##### Windows purifié

Windows Arium est une version modifié de Windows qui contient des logiciels supplémentaires et qui désactive des fonctionnalités et programmes qui compromettent la vie privée et ralantissent l'OS.

[optimizer](https://github.com/hellzerg/optimizer) logiciel qui permet de désactiver certaines fonctionnalités de suivis et des logiciels espions de Windows.

## Ajouter un raccourci au menu démarrer

Copier le raccourci dans le dossier :

* `C:\Users\Guigui\AppData\Roaming\Microsoft\Windows\Start Menu\Programs`
* `C:\ProgramData\Microsoft\Windows\Start Menu\Programs`
## Utiles

* `window + v` activer l'historique du presse papier.
* `Panneau de configuration\Matériel et audio\Options d’alimentation\Paramètres système` bloquer la mise en veille lorsque le capot est fermé.
* Réinstaller Onedrive : Aller dans `C:/Windows/WinSxS` et rechercher "onedrive" et exécuter le programme .exe

### CMD

* `cd dossier` naviguer dans les dossiers (retour `..`).
* `dir` lister les fichiers et les dossiers.
* `set var=valeur` créer une variable.
* variable de base `%cd%` chemin actuel.

## Ubuntu

Le programme est disponible sur le Microsoft Store.
Pour l'installer WSL (ubuntu), il faut :

- désactiver le VT dans les paramètres BIOS (F12 sur Dell) (à vérfier).
- `Turn Windows features on or off` puis activer l'option `Windows subsystems for Linux` et `VirtualMachinePlatform`.

`/mnt/c/Users/Guigui/Downloads`

---
# Ubuntu
## Installer ubuntu en dual boot en partageant des fichiers avec Windows

1. Désactiver la sécurité dans le Bios.
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

## Flathub

[Flathub](https://flathub.org/) logithèque avec les applications en appimage. Un exemple d'installation par le terminal `flatpak install flathub org.gnome.Music`.

* Cryptomator, logiciel de cryptage spécialisé pour le cloud.
* Github, pour gérer les fichiers github.
* Gapless, lecteur musique
* Shortwave, radios en ligne.
* 
## Logiciel par défaut

* `gnome-text-editor` éditeur de texte.
