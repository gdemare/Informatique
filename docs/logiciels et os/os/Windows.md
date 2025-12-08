## Installation

Pour limiter le nombre d'applications pré-installées, il choisir Anglais international (English world). Il est également possible de personnaliser son installation avec le logiciel
de création de clés bootables Rufus.

Pour passer l'étape de connexion à compte Microsoft 
##### Utilitaire de création de clés bootables

Rufus est un petit utilitaire qui permet de bloquer l'installation de logiciels normalement pré installé et de créer un compte Microsoft pour pouvoir installer l'OS.

[ventoy](https://www.ventoy.net/en/index.html) outils qui transforme une clé USB en clé bootable. Une fois la clé formatée il suffit de copier l'iso.
##### Windows purifié

[Windows Arium](https://www.ykn.fr/pages/arium/) est une version modifié de Windows qui contient des logiciels supplémentaires et qui désactive des fonctionnalités et programmes qui compromettent la vie privée et ralantissent l'OS.

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

Installation de windows 
email :
- a@a.com
- [atlas](https://docs.atlasos.net/getting-started/installation/) nettoie windows après une installation.
- [[modules supplémentaires]]

### Dell

F2 au démarrage pour ouvrir le bios.
Option (Alt)

### Réglage de la date et de l'heure

- `net start w32time` parfois il faut forcer le démarrage de w32 qui gère l'heure.
- `w32tm /config /syncfromflags:manual /manualpeerlist:"0.pool.ntp.org 1.pool.ntp.org 2.pool.ntp.org 3.pool.ntp.org` modifier le serveur de synchronisation de la date/heure avec [NPT Pool Project](https://www.ntppool.org/fr/use.html).  