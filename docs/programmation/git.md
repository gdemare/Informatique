
__Forge__ espace d’archivage de code

Les principales forges sont :

* Github, pour les projets open sources.
* Gitlab, pour les projets internes.

* `git clone url_répertoire` cloner un projet
* `git status` afficher les changements
* `git remote -v` retrouver l’URL du dépôt distant
* `git add fichier` ajouter un fichier à l'index.
* `git commit -m "message"` pousser les changements dans le dépôt.
    
    * `message` Décrire le pourquoi plutôt que le comment dans le texte court

* `git pull origin master` récupérer les changements sur le dépôt distant.
* `.gitignore` fichier qui contient les informations sur les ficheirs sensibles à ne pas publier (par exemple, ne pas versionner les sorties).

Publier un changement

* `git commit -m "description"` pousser un changement.
* `git push` publier la nouvelle version.

Installation un package  

 

L'installation est possible dans le dossier : 

 home 

Du projet 

De l'équipe 

Importe run package du site Bioconductor : getBiocPackage("package") 

 

Module développé par Servier : listModule(); importModule("moduel") 

 

Pour créer un nouveau projet il est recommandé d'utiliser packrat ou Renv 

 

Convention de nommage 

 

Pour les fichiers : 

Préfixe des fichiers avec des nombres s'ils sont appelés chronologiquement. 

Pour les fichiers ne contenant qu'une seule fonction : le nom fichier = celui de la fonction  

Pour les variables et les fonctions avec des mots explicites : 

En anglais. 

En minuscule.  

avec des mots séparés par _ 

Pour les variables : des noms. 

Pour les fonctions : des verbes. 

 
Structurer le script R 

Séparer le code et les rendre plus facilement lisibles : # load data ------------------------- ou # ============================= 

Charger tous les packages au début du script. 

Maximum 80 caractères par ligne. 

Pour le texte utilisé " à la place de ' 

Pour les fonctions sans argument = sans () 

Rmd first : Quand le developpement commence par la documentation - Rtask (thinkr.fr) (a lire) 

Versioned via git 

Documented via rmarkdown 

Tester via test that 

 
Éviter setwd() 

Utiliser des chemins relatif avec la fonction here() du package here 

Usethis::proj_sitrep() permet de vérifier que tous est installer correctement. 


Comment nommer les choses explicitement : What They Forgot to Teach You About R - 5  How to name files (rstats.wtf) 

Environnement reproductible https://thinkr.fr/dockeriser-application-shiny/ 


Historiser les versions  

 

Sauvegarder et gérer les différentes versions (permet notamment de revenir en arrière en cas de pb). 

Garder une trace de l'historique des modifications 

Permet un travail collaboratif en permettant de savoir qui a fait les modfi et pourquoi. Fusionner le travail de plusieurs personnes sans perdre de l'information 

 

A utiliser dans le cas de développement de package R 

Transformer un dossier en projet git synchronisé sur Github ou Gitlab - Rtask (thinkr.fr) 

 

Configurer un repertoire git dnans le server Team Foundation Server (TFS) 

1 porjet git par application 

 

Pour créer un projet : TF400813: The user 'FR1\DI63_OR' is not authorized to access this resource. - Microsoft Team Foundation Server (grs.net) 

 

En ligne de commande :  

Git clone ion/PROJECT_NAME)/_git/repository_name 

Pousser sur un rep existant : 

Git remote add origin hrepository_name 

Mandataire : 

Git config --global https.proxy http://10.31.1.91:8080 

Git config --global http.proxy http://10.31.1.91:8080 

Git config --global --get-regexp http.* 

 Oour Rexplo : 

Servier Shiny Server (grs.net)shonyServer accessible a tout le monde 

sr-rstudio.fr1.grs.net:444/tst/shiny/login shiny proxy 



Git push -u origin --all 

 

Créer un projet Rstudio versionné avec git  

New projet > Version Control Porjet   … mettre l'url 

 

Dans le terminal Rstudio  entrer : 




Bonnes pratiques  

Commit regulirement quite à devoir faire des retours  

s'assurer de travailler sur la dernière verison  git pull ou fetch 

Laisser une explciation descriptive pour chaque commit 

 

Revoir les changements avant d'ecrire un commentaire 

Utiliser les braches pour travailler a plusieurs qui concerne des fonctionnalités différentes. 

Partager des shared patterns 

 

R batch utiliser CronR pour la programmation de batch 

High Performance Cluster HPC 

Soumetter un job (a voir) 

 

Importer un fichier avec le bouton Upload dasn R studio/export/ Connections 

 

### 

 


 

Cloturer son compte Rshyna par dia au moment de quitter servier 

 

 

### AXE  

Texte de remplacement généré par une machine :
$ quarto 
Oash 
 

 

Nom de l'application 

Réfèrent info contact 

Personne a contact en cas de pb 

Le but de l'app 

 

Golem pour structurer le pacakge. 

Rmarkdown  

Testthat et shinytest pour automatiser les tests. 

 

Renv gestionnaire de dépendances 

### Fonctions ETL 

 

Pour les parties ELT avec R,  


Déclarer la structure du jeu de données finale  
