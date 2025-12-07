`commande <-paramètre> valeur`

## Manipuler la console et les fichiers

Touche 	 | Action
---------|---
Crtl + r | rechercher une commande tapée avec quelques lettres
Crtl + l | effacer le contenu de la console
Crtl + d | envoie le message EOF (End Of Files) 
Crtl + u | supprimer tout ce qui se situe à gauche du curseur
Crtl + w | supprimer le premier mot à gauche du curseur
Crtl + y | coller le texte supprimer avec les commandes précédentes
## La structure des dossiers et fichiers

* `pwd` afficher le dossier actuel.
* `which` connaître l'emplacement d'une commande.
* `ls` lister les fichiers et dossiers.
  
  Paramètres:
  
  * `a` afficher tous fichiers et les dossiers cachés.
  * `F` indique le type d'élément
  * `l` liste détaillée.
  * `h` afficher la tailler en Ko, Mo, Go...
  * `t` trier par date de modification.
  * `1` liste un fichier par ligne.
  * `d` lister uniquement les dossiers.
  * `R` récursive.

* `cd chemin` changer de dossier.
* `du chemin` taille occupée par les dossiers. Paramètres : 

  * `h` la taille pour les humains.
  * `a` afficher la taille des dossiers et des fichiers.
  * `s` avoir juste le grand total.
  
## Manipuler les fichiers

* `cat fichier` afficher tout le fichier. Paramétres:

	* `n` afficher le numéro des lignes.
	
* `less fichier` afficher un fichier page par page.

Raccourci	| Action
------------|---
Espace 		| affiche la suite du fichier.
Entrée 		| affiche la ligne suivante.
d 			| affiche onze lignes suivante (moitié de l'écran).
b 			| retounre en arrière d'un écran.
y 			| retourne en arrière d'une ligne.
u 			| retourne en arrière de onze lignes.
q 			| arrête la lecture de fichier.

* `head fichier` afficher le début du fichier.
Paramètres :	
	* `n nbre` afficher le nombre de lignes.
	
* `tail fichier` afficher la fin du fichier. Paramètres :

	* `n nbre` afficher le nombre de lignes.
	* `f` suivre la fin du fichier (utile pour les fichiers qui "bouge"» (PS : pour arrêter, taper "ctrl+c").
	
* `touch fichier <fichier2>` créer un fichier.
* `mkdir dossier <dossier2>` créer un dossier. Paramètres :

	* `p` créer des dossiers intermédiaire.
	
* `cp fichier copie` copier un fichier ("CoPy").
* `find -name *.md | xargs cp -t dossier/` copier les fichiers ave cune structures communes. Paramètres :

	* `R` copier des dossiers.

* `mv fichier copie` déplacer un fichier et/ou le renommer.
* `rm fichier fichier2` supprimer des fichiers et des dossiers ("ReMove").
Paramètres :

	* `i` demander confirmation.
	* `f` forcer la suppression.
	* `v` verbose.
	* `r` supprimer un dossier et son contenu.
	
* `ln fichier1 fichier2` créer des liens entre les fichiers. Paramètre :	

	* `s` créer un lien symbolique (sans l'argument, Linux créer un lien physique).

* `rev 'text'` inverse l'ordre des lettres.

## Les utilisateurs et les droits

* `sudo comande` exécuter une commande en mode root(temporairement).
* `sudo su` devenir root indéfiniment.
* `adduser utilisateur` ajouter un utilisateur.
* `passwd utilisateur` changer le mot de passe.
* `deluser utilisateur` supprimer un compte mais ne pas son répertoire personnel. Paramètres :

	* `-remove-home` supprimer le dossier home de l'utilisateur.

* `addgroup groupe` créer un groupe.
* `usermod utilisateur` modifier un utilisateur. Paramètres :

	* `l` renommer l'utilisateur (NB : le nom de son répertoire ne sera pas changé).
	* `g` changer de groupe.
	* `G groupe1, groupe2 utilisateur` appartenir à plusieurs groupes (peu importe les groupes auxquels il appartenait).
	* `aG` même chose que -G mais concerve les groupes auxquels appartenaient l'uilisateur.

* `delgroup groupe` supprimer un groupe.
* `chown proprietaire fichier` changer le propriétaire d'un fichier. Paramètres :

	* `utilisateru:groupe` changer le groupe et le propriétaire et groupe d'un fichier.
	* `R` affecter récussivement les sous-dossiers.
   
* `chgrp groupe fichier` changer le groupe propriétaire d'un fichier.
* `chmod droit fichier` modifier les droits d'accés [propriétaire][groupe][autres] .
  
	* Méthode absolue : attribuer les droits en 3 chiffres via l'addition.
	* Méthode relative : attribuer les droits avec 9 lettres. 	

Action 	| Lettre	| Chiffre	
--------|-----------|---
read 	| r 		| 4
write 	| w 		| 2
execute | x 		| 1

Paramètres :

* `R` affecter résursivement.

* `su utilisateur` changer d'utilisateur.
	
## Installer des programes avec apt-get

!!! note
	On peut utiliser `apt` sans get ou cache notamment sur les chromebooks.

* `apt-get update` mettre à jour le cache des paquets.
* `apt-cache search paquet` rechercher un parquet.
* `apt-get install paquet` installer un paquet.
* `apt-get autoremove paquet` supprimer un paquet.
* `apt-get upgrade` mettre à jour tous les paquets.
*  `apt show paquet | grep install` vérifier si le package est installé.
*  `apt list --installed` lister les logicels installés.
*  `dpkg` logicel de gestion des paquets debian (.deb). Paramètres :
  
	* `-l` lister les packages installer.
 	* `-i package` installer un package.
  	* `-r package` désinstaller un package.	 	

#### Application snap

* `snap list` lister les applications snap installées.
* `snap install package` installer une application snap.
* `snap remove package` désinstaller une application snap.

## RTFM : lisez le manuel!
		
* `man commande` afficher le manuel d'une commande.
* `apropos «cequejesais»` affiche la liste de commande en rapport avec «cequejesais».
* `commande -h` affiche un résumé de la commande.
* `whatis commande` affiche un résumé trés leger de la commande.

## Rechercher des fichiers

* `locate fichier` rechercher rapidement dans la base de données.
* `updatebd` reconstruitre la base de données des fichiers du disque dur.
* `find ou quoi action` recherche approfondie.
  
	* ou : c'est le nom du dossier dans lequel la commande va faire la recherche.
	* quoi : c'est le fichier de recherche (date de création, nom, taille etc)
	* Que faire avec :
   
Paramètres :

	* `name "fichier"` rechercher exactement le nom d'un fichier.	
	* `size «+/-/ »«tailleavecunité»` recherche a partir de la taille du fichier. Les unités sont : K ; M ; G ;...
 
		* `atime «temps»` recherche à partir de la date de dernier accès.
		* `type «d/f» «nom»` rechercher uniquement des répertoires ou des fichiers ( "d"=directories / "f"=files ).
		* `print` afficher les résultats.
		* `delete`supprimer les fichier trouvés.
		* `exec «commande» {} \;` appeler un commande qui effectuera une action sur les fichiers trouvés.
		* `maxdepth «nbre»` effectuer une recherche en limitant le nombre de répertoire [1;oo].
 
## Extraire, trier et filtrer des données

* `grep texte fichier` affiche toute les lignes ou il y a «texte». Paramétres:

	* `i` ignore la casse (majuscules et minuscules).
	* `n` connaître les numéros des lignes.
	* `v` ignorer un mot.
	* `r` rechercher dans tous les fichiers et sous dossiers.

* `sort fichier` trier les lignes Paramétres :
  
	* `o` écrire le résultat dans un fichier.
	* `r` trier en ordre inverse.
	* `R` ordre aléatoire.
	* `n` trier les nombres en ordre croissant.
	
* `wc fichier` "word count" compter le nombre de lignes, de mots,...( nombre de l-gnes; nombre de caractéres; nombre d'octet ). Paramétres:

	* `l` compter le nombre de lignes.
	* `w` compter le nombre de mots.
	* `c` compter le nombre d'octets.
	* `m` compter le nombre de caractères.
	
* `uniq fichier <sortie>` détecter et supprimer les doublons. Attention ne fonctionne que sur un fichier trié. Paramétres:

	* `c` compter le nombre d'occurences.
	* `d` afficher uniquement les lignes en double.
   
* `cut intervalle fichier` couper une partie d'un fichier. L'intervalle se note "5-18". Paramétres:
  
	* `c` couper selon le nombre de caractéres de chaques lignes.
	* `d «délimiteur»` indique quel le délimiteur dans le fichier.
	* `f «champs»` indique le numéro du ou des champs à garder.

* `awk`
* `sed fichier` éditeur de flux (Stream EDitor). Paramètre :
  
	* `n '«nbre»p'` affiche la ligne «nbre»p du fichier.
 
* `sed -n "$(6,$((nbre+delta))p" document.info`
				
## Les flux de redirection

* `>` rediriger vers un nouveau fichier (si celui-ci existe déjà, il sera écrasé). Exemple: cut -d , -f 1 notes.cvs > eleves.txt
* `> /dev/null` rediririger le résultat dans le "trou noir" de Linux.
* `>>` rediriger à la fin d'un fichier.
* `2>, 2>>, 2>1&` rediriger les erreurs.
  
    * `2>` rediriger  les erreurs dans un fichier (s'il existe déjà il sera écraser ). exemple: cut -d , -f 1 fichier_inexistant.csv > eleves.txt 2> erreur.log .
    * `2>>` redirgiger les erreurs à la fin d'un fichier( s'il n'existe pas, il sera créé).
    * `2>1&` redirgier les erreurs au même endroit et de la même façon que la sorite standard.
    PS: 2>>&1 ne fonctionne pas, il faut >> sur le fichier ou le veut ecrire. Exemple: cut -d , -f 1 fichier_inexistant.csv >> eleves.txt 2>&1 .

* `<` lire depuis un fichier
* `<<` lire depuis le clavier progressivement.
* `|` chaîner les commandes, tout ce qui sort de la commande1 est immédiatement envoyé à la commande2.
* `du` permet d'obtenir la taille des sous-répertoires.

## Surveiller l'activité du système

* `w` qui fait quoi?
* `date` afficher la date et l'heure.
* `uptime` durée de fonctionnement de l'ordinateur.
* `tload` afficher la charge de l'ordinateur ie l'indice de l'activité de l'ordinateur. Pour quitter le graphe, faire Crlt + C.
PS : liste statique des processus.

	* PID : c'est le numéro d'identification du processus.Chaque processus a un numéro unique qui permet de l'identifier. Ce numéro nous sera utile plus tard lorsque nous voudrons arrêter le processus.
	* TTY : c'est le nom de la console depuis laquelle a été lancé le processus.
	* TIME : la durée d'exécution du processus. Plus exactement, cela correspond à la durée pendant laquelle le processus a occupé le processeur depuis son lancement.
	* CMD : le programme qui a généré ce processus. Si vous voyez plusieurs fois le même programme, c'est que celui-ci s'est dupliqué en plusieurs processus.
   
Paramétres:

	* `ef` lister tous les processus.
	* `ejh` afficher les processus en arbre.
	* `u [nomutilisateur]` lister les porcessus lancé par un utilisateur.
 
* `top` liste dynamique des processus.
  
	* `q` ferme top.
	* `h` affiche l'aide.

* `Crlt + C` arrêter un processus lancé en console.
* `kill [PID]` tuer un processus. Paramétres:

	* `9`  tuer un processus sans lui laisser de temps!!!!!

* `killall processus` tuer les processus avec le même nom.
* `halt` arrêter l'ordinateur.
* `reboot` redémarrer l'oridnateur. (pour en savoir + voir commande shutdown).

## Exécuter des programmes en arrière-plan
	
* `commande &` lancer un processus en arrière-plan.
* `nohub commande` détacher le processus de la console.
* `Ctrl + z` mettre en pause l'exécution d'un programme (Attention: le processus n'est pas détruit).
* `bg` [background] passer le processus en arrière-plan (ps: le processus doit être en pause).
* `jobs` connaître les processus qui tournent en arrière-plan (ps: le processus doit être en pause).
* `fg %num_processus` [foreground] reprendre un processus au premier plan (ps: le processus doit être en pause).
* `Crtl + c` arrête (détruit) un processus en cours en avant-plan.
* `screen` plusieurs consoles en une. (ps: porgramme non installer par défaut, il faut installer : screen). Pour la quitter, taper : Ctrl + d.

## Exécuter un programme à une heure différée
	  
* `date` régler l'heure.
* `at heure <jour>` exécuter une commande plus tard (l'heure doit être écrite : HH:MM et le jour : MM/JJ/AA). Ps: on rentre les commandes postérieurement. Pour quitter, taper : Ctrl + d.
* `atq` lister les «jobs» en attente.
* `atrm chiffre` supprimer les «jobs» en attentes.
* `;` enchaîner des commandes. Exemple: touch fichier.txt ; rm fichier.txt
* `sleep chiffre` faire une pause, par défaut, la pause est en seconde. Pour utiliser les autres unités, il faut rajouter après de le chiffre :
  
	* `-m` minutes.
	* `-h` heures.
	* `-d` jours.

* `pause` attendre que l'utilisateur face la touche Entré.
* `&&` enchaîner plusieurs commande uniquement si les instructions précédentes ce sont correctements exécutées. 
* `crontab` exécuter une commande régulièrement (ps: mettre nano comme éditeur de texte par défaut: echo "export EDITOR=nano" >> ~/.bashrc). Paramétres :

	* `-e` modifier la crontab.
	* `-l` afficher la crontab.
	* `-r` supprimer la crontab.
   
Utilisation générale (après crontab `e`). Shéma GÉNÉRAL : [minute(/60)] [heure(/24)] [jour du mois(/31)] [mois(/12)] [jour de la semaine(/6- dimanche=0)] «commande»
Les différentes notations (exemples) :

	* `nombre` exécuté lorsque le chanp vaut le nombre.
	* `*` exécuter tout le temps (toutes les valeurs bonnes).
	* `nombre1,nombre2,nombre3` exécuter lorsque le champs prend la valeur nombre1, nomb...
	* `nombre1-nombre2` exécuter pour les valeurs entre nombre1 à nombre2.
	* `*/nombre` exécuté tous les multiples de nombre.
 
!!! example
	```
	47 * * * * commande : toutes les heures à 47 minutes exactement.			
	0 0 * * 1 commande : tous les lundis à minuit.
	```
 
Les erreurs n'apparaissent pas, pour y remédier, il faut les rediriger vers un nouveau fichier.

## Archiver et compresser
	  
* `tar` assembler des fichiers dans une archive. Paramétres :
  
 	* `cvf «nomarchive.tar» «fichiers»` créer une archive tar (`c` créer une archive .tar; `v` afficher le détail des opérations; `f` assembler l'archive dans un fichier).
	* `tf «nomarchive.tar» «fichiers»` afficher le contenu de l'archive sans l'extraire. 
	* `xvf nomarchive.tar` extraire les fichiers de l'archive (`x` pour eXtract).
	* `zcvf` archiver et compresser en gzip (`z` compresser avec gzip).
	* `zxvf` désarchiver et décompresser en gzip.
	* `jcvf` archiver et compresser en bzip2.
	* `jxvf` désarchiver et décompresser en bzip2.
	* `ztf` afficher le contenu...
	* `jtf`

* `gunzip ficheir` décompresser un ficiher gz.
	
* `gzip «nomarchive»` compresser une archive (la plus courante). Paramétres:	

  	* `-v` affiche les détails de l'opération.
   
Commandes associées:

* `-zcat` lire un fichier compressé en gzip en entier.
* `-zmore` lire un fichier compressé en gzip ligne par ligne.
* `-zless` lire un fichier compressé en gzip page par page.

* `bzip2 archive` compresser une archive (la plus puissante).
Paramétres:

	* `-v` affiche les détails de l'opération.

* `unzip` décompresser un .zip (à  installer).
* `zip archive.zip dossier` compresser une archive en .zip (à installer).
Paramétres:

	* `-r` compresse le dossier ainsi que les fichiers contenus.
	* `-v` afficher les détails de l'opération.

* `unzip` décompresser des archives .zip.
* `unrar archive` décompresser un .rar. (ps: rar est un format propriétaire du coup le logiciel est payant pour compresser).
Paramétres :	

 	* `e` obligatoire pour décompresser.
	* `1` afficher le contenu.

## La connexion sécurisée à distance avec SSH

Obligatoire : Installer le paquet «openssh-server».

* `sudo /etc/init.d/ssh start` démarrer SSH.
* `sudo /etc/init.d/ssh stop` arrêter SSH.
* `ssh login@ip` remplacer «lon» et l'«ip» du client. Ps: pour simuler une connextion «ip»=localhost.
* `logout` deconnexio. Ps : on peut aussi utilisé Ctrl+d.

Pour plus de renseignements, voir «puTTY».

## Transférer des fichiers

* `wget «HTTP ou FTP»` téléchargement de fichiers. Paramétres :
  
	* `-c` reprendre un téléchargment arrêté.
	* `--background` lancer un téléchargement en tâche de fond.
   
* Crtl+c : arrêter le téléchargement en cours.
* `wget-log` indique l'avancement du téléchargement lancer en arrère plan.
* `scp fichier-origine copie-destination` copier des fichiers sur le réseau.

!!! note
	Chacun des élément peut s'écrire : login@ip:nom_fichier.

## Analyser le réseau et filtrer le trafic avec un pare-feu

* `host «Ip/nom d'hôte»` convertir une IP en nom d'hôte et inversement. 
* `whois` tout savoir sur un nom de domaine ( il faut installer le paquet).
* `ifconfig` liste des interfaces réseau.
* `ifconfig «nom de l'interface» «up/down»` activer (up) et désactiver (down) des interfaces.
* `netstat` statistiques sur le réseau. Paramères :

	* `i` statistiques des interfaces réseau.
	* `uta` lister toutes les connexions ouvertes ou ( `u` :afficher les connexions UDP ; `t` : afficher ls connexions TCD ; `a` afficher toutes les connexions quel que soit leur état ).	
	* `n` afficher le numéro des ports.
	* `lt` lister les connexions en état d'écoute.

* `iptables` consulter le iptables Rappel pour plus d'informations.

## Compiler un programme

Requis : avoir installer "build-essential"
	
1. Télécharger l'achive.
2. Décompresser.
3. Exécuter le fichier `./configure`, il vérifie si tous les dépendances sont remplies. En cas d'erreurs, il faut faire une recherche sur internet et installer les paquets manquants.
4. `make install` compiler les fichiers. Le programme est maintenant installer.
5. `make uninstall` désinstaller le programme, à exécuter dans le dossier ou la compilation à eu lieu.

!!! warning
	Il ne faut pas supprimer le dossier de "compilation".

* `bash fichier.sh` exécuter un programme sh.

## Autres programmes

### ImageMagick ( manipuler des images)

Paquet `imagemagick`

* `display image` afficher une image.
* `convert image <paramètre> nv_image` convertir une image. Paramètre :
  
	* `resize dimension` redimensionner un image. Pour forcer une redimension utiliser : «dimension»\! et «dimension» peut s'écrire en pourcentage. (`500x1050\!`).
	* `quality nbre` compresser une image à tant de pourcentage.

* `rotate degrè` touner une imgage de tant de degrés dans le sens des aiguilles d'une montre.
* `import nom_capture` capturer l'écran.
Paramètres :	
	* `window root` capturer tout l'écan.
	* `pause seconde` attendre un nombre spécifié de seconde. 
 
### eyeD3 ( tagger les fichiers mp3/flac)

`eyeD3 fichier/dossier` gérer les tags lier à des fichiers audio de formats flac ou mp3 .
Paramères :

* `-to-v2.4` convertir le tag du fichier en IDE v2.4 .
* `-remove-images` supprimer l'image du fichier.
* `-add-image= image` ajouter une image au fichier
* `a artiste` modifier/ajouter un artiste.
* `A album` modifier/ajouter un album.
* `t titre` modifier/ajouter un titre.
* `n numéro` modifier/ajouter le numéro de la piste.
* `N numéro` modifier/ajouter le n° total des pistes de l'album.
* `Y année` modifier/ajouter l'année.
* `p label` modifier/ajouter le label.
* `-i image` ajouter un icône.
		
### Commandes suplémentaires

* `cal` affiche le calendrier.
* `file commande` connaître le statut d'une commande ( interne/ externe).
* `invoke-rc.d kdm restart` redémarrer l'interface graphique (kubuntu).

## Android sur linux 

### Installer Anbox

```
sudo add-apt-get-repository ppa:morphis/andox-support
sudo apt-get update
sudo apt-get install anbox-modules-dkms
sudo mobprobe ashmen_linux
sudo mobprobe binder_linux
sudo apt-get install android-tools-adb android-tools-fastboot
```

### Installer une application

`adb install application.apk`

### Installer le Play Store

Requis : `wget lzip unizip squahfs-tools`. L'url github : `https://github.com/geeks-r-us/anbox-playstore-installer/`

* `wget https://raw.githubusercontent.com/geeks-r-us/anbox-playstore-installer/master/install-playstore.sh`.
* Autoriser les droits des settings > Apps > Google services.