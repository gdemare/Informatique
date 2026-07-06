
Pour [OpenCore Legacy Patcher](https://github.com/dortania/OpenCore-Legacy-Patcher/) pour permettre au ancien mac d'être mis à jour.

- `sudo spctl --master-disable`  afficher l'option pour installer des applications issues de n'importe où.
- Virer la pastille de notif sur Paramètres des màj :
  1. `defaults write com.apple.systempreferences AttentionPrefBundleIDs 0`
  2. `killall Dock` redémarrer le dock.

### Raccourci

- Maj + Commande + 5 capture d'écran (ou spotlight).
- `cmd + espace` spotlight.
- `cmd + crlt + Q` pour verrouiller sa session.
- `Cmd + c` puis `=alt + Cmd + v` déplacer un fichier.

### Logiciel

MacOs Monterey - 12.7.6

- Maccy(https://github.com/p0deje/Maccy), application presse papier.
- iWork maximum 13.0 pour MacOS Monterey. La dernière version compatible avec Monterey est la 1.0.0.
- R Studio ne fonctionne pas. La dernière version de la branche 4.4.X (2024.04 Chocolate Cosmos) qui prend en charge MacOS 12 est compatible jusqu'a R 4.4.3.
- [Homebrew](https://brew.sh/) pour l'installation des packages comme libredwg.
