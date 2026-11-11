__Forge__ espace d’archivage de code

Les principales forges sont :

* Github, pour les projets open sources.
* Gitlab, pour les projets internes.

Les commandes : 

* `git clone url_répertoire` cloner un projet
* `git status` afficher les changements,  vérifier l'état de mise a jour des fichiers.
* `git remote -v` retrouver l’URL du dépôt distant
* `git add fichier1 fichier2` ajouter un fichier à l'index, ajouter les fichiers modifiés au prochain push.
* `git commit -m "message"` pousser les changements dans le dépôt.
    
    * `message` Décrire le pourquoi plutôt que le comment dans le texte court

* `git remote -v` 
* `git pull origin master` récupérer les changements sur le dépôt distant.
* `.gitignore` fichier qui contient les informations sur les fichiers sensibles à ne pas publier (par exemple, ne pas versionner les sorties).

Exemple  d'utilisation :

``` bash
git commit -m "description"`
git push
```

### Cloner un répertoire 

Déclarer son nom d'utilisateur et son email :

- `git config --global user.name 'caparmongas'`
- `git config --global user.email '******@mail.com'` 
-  `git config --global user.email '4768+*****@users.noreply.github.com'` pour garder l'email privé dans les informations sur le commit.
- `git clone https://codeberg.org/répertoire/.git` copier un dossier en local.

Installation un package  

L'installation est possible dans le dossier : 

 home 

Du projet / De l'équipe 
Pour créer un nouveau projet il est recommandé d'utiliser packrat ou Renv 

Convention de nommage 

Pour les fichiers : 

- Préfixe des fichiers avec des nombres s'ils sont appelés chronologiquement. 
- Pour les fichiers ne contenant qu'une seule fonction : le nom fichier = celui de la fonction  
- Pour les variables et les fonctions avec des mots explicites en anglais et en minuscule.
- avec des mots séparés par _ 
- Pour les variables : des noms.
- Pour les fonctions : des verbes. 

### Structurer le script R 

Séparer le code et les rendre plus facilement lisibles : 

``` r
# load data ------------------------- ou # ============================= 
```

- Charger tous les packages au début du script. 
- Maximum 80 caractères par ligne.
- Pour le texte utilisé " à la place de ' 
- Pour les fonctions sans argument = sans () 
- Rmd first : Quand le developpement commence par la documentation - Rtask (thinkr.fr) (a lire) 
- Versioned via git 
- Documented via rmarkdown 
- Tester via test that 
- Éviter setwd() 
- Utiliser des chemins relatif avec la fonction here() du package here 
- Usethis::proj_sitrep() permet de vérifier que tous est installer correctement. 
- Comment nommer les choses explicitement : What They Forgot to Teach You About R - 5  How to name files (rstats.wtf) 
- Environnement reproductible https://thinkr.fr/dockeriser-application-shiny/ 

Historiser les versions pour :

- Sauvegarder et gérer les différentes versions (permet notamment de revenir en arrière en cas de pb). 
- Garder une trace de l'historique des modifications 
- Permet un travail collaboratif en permettant de savoir qui a fait les modfi et pourquoi. Fusionner le travail de plusieurs personnes sans perdre de l'information 

### A utiliser dans le cas de développement de package R 

Transformer un dossier en projet git synchronisé sur Github ou Gitlab - Rtask (thinkr.fr) 

Configurer un repertoire git dnans le server Team Foundation Server (TFS) 

1 projet git par application 

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
Laisser une explication descriptive pour chaque commit 

 

Revoir les changements avant d’écrire un commentaire 
Utiliser les branches pour travailler a plusieurs qui concerne des fonctionnalités différentes. 
Partager des shared patterns 

 

R batch utiliser CronR pour la programmation de batch 

High Performance Cluster HPC 

Soumetter un job (a voir) 

 
Importer un fichier avec le bouton Upload dans R studio/export/ Connections 


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
