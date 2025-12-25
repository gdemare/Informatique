
## Logiciels

Disponible sur le Window Store :

* Brave, navigateur internet basé sur Chrome avec un bloqueur de pub intégré.
* Discord
* Firefox.
* Visual Studio Code à remplacer par [VSCodium](https://vscodium.com/) .
* VLC, lecteur media.

Logiciels Windows :

* [Adguard](https://adguard.com/en/download.html), bloqueur de pubs indispensables.
* [Cryptomator](https://cryptomator.org/downloads/), pour chiffrer ses données numériques sur les cloud.
* [Calibre](https://calibre-ebook.com/download), gérer sa bibliothèque numérique.
* [Deluge](https://deluge-torrent.org/), gestionnaire de torrents.
* [Keeweb](https://keeweb.info/), gestionnaire de mots de passe pour Keep.
* [Mail spring](https://github.com/Foundry376/Mailspring), boite mail local.
* [Mp3tag]() modifier les informations des fichiers de musique.
* [Noi](https://github.com/lencx/noi) ui pour les chats et consor.
* [Nora](https://github.com/Sandakan/Nora) lecteur musique au top.
* [UpdateHub](https://github.com/NexovaDev/UpdateHub) vérifier les mises à jours des logiciels.
### Le relatif

Sur le store :

* Simplenote.
* [Anki](https://apps.ankiweb.net/), cartes pour l'apprentissage par répétition.
* [Deemix](https://deemix.app/gui) - [Reddit Deemix](https://www.reddit.com/r/deemix/), télécharger des musiques depuis deezer.
* [FreeFileSync](https://freefilesync.org/download.php), synchroniser des répertoires et des fichiers.
* [Fluent reader](https://github.com/yang991178/fluent-reader/releases), aggrégateur de flux rss.
* [Harmonoid Music](https://harmonoid.com/), lecteur audio avec une interface agréable.
* [Google drive](https://www.google.com/drive/download/)
* [Miktex (latex)](https://miktex.org/) latex.
* [pCloud](https://www.pcloud.com/fr/download-free-online-cloud-file-storage.html)
* [pandoc](https://pandoc.org/) convertir des fichiers en word, markdown, html.
* Zotero, références bibliographiques.
* [eden emulator](https://eden-emu.dev/download) Emulateur de switch  
[SpotX](https://github.com/SpotX-Official/SpotX), bloqueur de pub sur la version desktop de spotify.
## Installation

Versions de Windows modifiés :

- [Windows Arium](https://www.ykn.fr/pages/arium/) est une version modifié de Windows qui contient des logiciels supplémentaires et qui désactive des fonctionnalités et programmes qui compromettent la vie privée et ralentissent l'OS.
### Depuis un iso officiel

Pour limiter le nombre d'applications préinstallées, il choisir Anglais international (English world). Il est également possible de personnaliser son installation avec le logiciel de création de clés bootables Rufus.

Pour passer l'étape de connexion à compte Microsoft utilisé l'email a@a.com.

Logiciel à installer ultérieurement pour nettoyer Windows :

- [atlas](https://docs.atlasos.net/getting-started/installation/) nettoie Windows après une installation.
- [optimizer](https://github.com/hellzerg/optimizer) logiciel qui permet de désactiver certaines fonctionnalités de suivis et des logiciels espions de Windows.
### Utilitaire de création de clés bootables

- Rufus est un petit utilitaire qui permet de bloquer l'installation de logiciels normalement pré installé et de créer un compte Microsoft pour pouvoir installer l'OS.
- [ventoy](https://www.ventoy.net/en/index.html) outils qui transforme une clé USB en clé bootable. Une fois la clé formatée il suffit de copier l'iso.
### Dell

F2 au démarrage pour ouvrir le bios.
Option (Alt)
## Fonctionnalités et personnalisation
### Ajouter un raccourci au menu démarrer

Copier le raccourci dans le dossier :

* `C:\Users\Guigui\AppData\Roaming\Microsoft\Windows\Start Menu\Programs`
* `C:\ProgramData\Microsoft\Windows\Start Menu\Programs`
### Réglage de la date et de l'heure

- `net start w32time` parfois il faut forcer le démarrage de w32 qui gère l'heure.
- `w32tm /config /syncfromflags:manual /manualpeerlist:"0.pool.ntp.org 1.pool.ntp.org 2.pool.ntp.org 3.pool.ntp.org` modifier le serveur de synchronisation de la date/heure avec [NPT Pool Project](https://www.ntppool.org/fr/use.html).  
### Utiles

* `window + v` activer l'historique du presse papier.
* `Panneau de configuration\Matériel et audio\Options d’alimentation\Paramètres système` bloquer la mise en veille lorsque le capot est fermé.
* Réinstaller Onedrive : Aller dans `C:/Windows/WinSxS` et rechercher "onedrive" et exécuter le programme .exe
### CMD

* `cd dossier` naviguer dans les dossiers (retour `..`).
* `dir` lister les fichiers et les dossiers.
* `set var=valeur` créer une variable.
* variable de base `%cd%` chemin actuel.
### Installer Ubuntu

Le programme est disponible sur le Microsoft Store.
Pour l'installer WSL (Ubuntu), il faut :

- désactiver le VT dans les paramètres BIOS (F12 sur Dell) (à vérfier).
- `Turn Windows features on or off` puis activer l'option `Windows subsystems for Linux` et `VirtualMachinePlatform`.

