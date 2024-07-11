## Tester un fonction

`library(testthat)`

* `expect_equal()`

## Exécuter uniquement si le script n'est pas appelé

* `interactive()` renvoie TRUE si le script est exécuter directement (par opposition à un appel).

## Golem

`library(golem)`

La philosophie de Golem est de créer et organiser un programme sous la forme d'un package en appelant des fonctions :
Golem est un package qui structure et gère le développement de package R.

Méthodes alternatives pour appeler un module en lui fournissant un paramètre : `callModule(mod_bars_echarts_server, "bars_echarts_ui_1")`.

### Déclarer les modules

Les modules doivent être déclarés dans `golem::add_module(name = "example")` permet de créer trois fichiers :

* `R/mod_example.R` avec deux fonctions `mod_example_ui` et `mod_example_server`.

### Trois scripts le dossier 

1. `01_start.R` renseigner les informations sur le projet.
2. `02_dev.R` pour ajouter un module, faire les tests.
3. `03_deploy.R` déployer l'application.
4. `run_dev.R` permet de lancer l'applicatin shiny. Il faut exécuter le script complet.

### 02_dev.R

* `@import package` dans le module et `usethis::use_package("library")` ajouter des dépendances.
* `golem::add_module(name = "example", param1 = val1, param2 = val2)` créer un module càd le fichier qui correspond au module dans le dossier R.
* `browser_button()` ajouter un bouton pour debbug (a voir).
* `add_fct("helpers", with_test = TRUE)` ajouter une fonction.

`app_ui.R`

`golem_add_external_ressources()` ajouter des fichiers extérieurs.

Les fichiers extéiruers sont créer dans inst/app/www

`add_js_file("nom")` créer un script js.

### 03_deploy 

Instruction avec le déployement.

### run_dev.R

## Documentation

`library(pkgdown)`

* `usethis::use_pkgdown()`.
* `pkgdown::build_site()` générer la documentation dans le dossier docs.

Permet de créer : 

* un fichier New qui contient les nouveautés des versions.
* des articles. Les articles sont écris en markdown et convertis automatiquement en html.



devtools_history.R

1. `check` pour vérifier détermine s'il y a d'erreurs et dans warning dans le package.
2. `Build Source Package`pour générer un tar.
3. `Install` pour ajouter ou maj du package COMPILE dans son environnement.

* `@param x description` liste des paramètres 
* `@import magrittr` importer un package (une library par ligne).
* `@importFrom package fonction` importer une fonction.
* `@export` permet à la fonction d'être disponible en dehors du package.

### Flemme de l'ajouter correctement

install.packages("devtools")
install.packages("roxygen2")

Fichier :

* `NAMESPACE` décrit les exports.
* `DESCRIPTION` contient une description du package, les dépendances et les métadonnées (nom, version, auteurs).

`browser()` mettre une pause à l'exécution.

fct_ fonction
var_ variable (une valeur)
vrai_ booléen
dt_ dataframe
dic_dictionnaire
list_ liste

