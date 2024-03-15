## Les packages

* `install.packages("package")` installer un package.
* `library(package)` importer un package. 
* `if(!require("tidyverse")) install.packages("tidyverse")` installer un package uniquement s'il n'est pas installé.

### Les meilleurs packages R

* `rmarkdown` R markdown.
* `tidyverse` intègre les packages les plus populaires pour la science de la donnée.

	* `dplyr` et `tidyr` manipuler les données.
	* `forecasts` convertir en date.
	* `golemn` créer un package et sa documentation de façon automatisée.

* `testthat` tester.

## Les fichiers

* `r"(dossier1\dossier 2\)"` déclarer un chemin.
* `basename("C:/some_dir/a.ext")` renvoyer le nom du fichier.
* `dirname("C:/some_dir/a.ext")` renvoyer le dossier.
* `dir.create(dossier)` créer un dossier.
* `unlink(chemin_dossier, recursive = TRUE)` supprimer un dossier et ses fichiers.
* `list.files()` lister les fichiers et les répertoires.
* `list.dirs()` lister les dossiers.
* `file.exists(fichier)` tester l'existence d'un fichier.
* `setdiff(list.files(), list.dirs(recursive = FALSE, full.names = FALSE))` lister uniquement les fichiers.
* `setwd(dossier)` changer le dossier de travail.
* `getwd()` chemin du dossier de tavail.
* `source(fichier)` exécuter un script.
* `tools::file_ext(chemin_fichier)` renvoyer l'extension du fichier.

### RData

* `save(obj1, obj2, file = "mes_objets.RData")` sauvegarder en RData.
* `load(fichier.RData)` charger un RData.

### Excel

Pour manipuler les fichiers excel, il est préférable d'utiliser `library(openxlsx)` qui est la bibliothèque la plus complète.

* `readWorkbook(wb ou , sheet = "Supplies")` lire un fichier excel ou un wb.
* `wb <- createWorkbook()` créer un classeur.
* `saveWorkbook(wb, "file.xlsx")` enregistrer un classeur. Paramètres :

	* `overwrite = TRUE` écraser la version existente.

* `addWorksheet(wb = wb, sheetName = "feuill")` ajouter une feuille.
* `getSheetNames(wb ou fichier)` nom des feuilles.
* `writeData(wb = wb, sheet = "feuill", x = df)` écrire un dataframe. Paramètres :

	* `headerStyle = headerStyle` style des entêtes (voir style).
	* `borders = "n"` .
	* `startCol = nb`  et `colNames = nb` début où commencer à remplir. 

#### Style 

`createStyle()`

* `fontColour = "#006100"` couleur de la police.
* `bgFill = "#C6EFCE"` fond.
* `textDecoration = "Bold"` gras.

#### Formater le classeur

* `setColWidths(wb = wb, sheet = "feuil", cols = 1:4, widths = "auto")` largeur des colonnes.

### Json 

`library(jsonlite)`

* `toJSON(liste)` convertir une liste en Json.
* `writeLines(json_data, "REACDATA_t.json")` créer un fichier en Json (attention, il faut le convertir avant).
* `fromJSON("REACDATA_t.json")` importer un Json.

### Images

`library(jpeg)` et `library(png)`

* `readJPEG(image.jpeg)` image JPEG.
* `readPNG(image.png)` image PNG.

## Fonctions de base

* `print("Hello")` afficher un message.
* `cat("Hello\n")` afficher un message sans retour à ligne. Pour un retour à la ligne `\n` et pour remplacer le texte précédent `\r`.
* `dput(variable)` afficher la variable à déclarer en code R.
* `suppressWarnings(code)` supprimer les warnings.
* `suppressMessages(code)` supprimer les messages.
* `Sys.sleep(seconde)` attendre un nombre de seconde avant la suite de l'exécution.

## Environnement

* `rm (list = ls())` supprimer les variables de l'environnement.

## Variables

Déclarer des variables :

* `var <- valeur` ou `var = valeur` déclarer une variable ou modifier la valeur. 
* `var <<- valeur` forcer l'association (utile pour modifier une variable dans la fonction).

* `typeof(var)` renvoyer le type de variable.
* `exists("variable")` teste l'existence d'une variable.
* `missing('variable')` vérifier si l'arguement existe.

### Attribut

!!! note
    Les attributs sont les métadonnées associées à un objet.

* `attr(iris, "perso") <- valeur` ajouter un attribut à objet.
* `attributes(dt_conc)` renvoie les attribue d'un objet. 

## Vecteurs

* `c(2, 4, 6)` déclarer un vecteur.
* `2:6` séquence de 2 à 6 inclus.
* `seq(2, 3, by = 0.5)` créer une séquence de 2 à 3.
* `rep(1:2, times = 3 ou each = 3)` repéter la valeur soit en alterné (1,2,1,2) ou à la suite (1,1,2,2).

* `date[nligne][ncol]` sélectioner une cellule.
* `data$colonne` sélectionner une colonne.
* `table[ligne, colonne]` sélectionner une ligne ou une colonne ou une cellule (laisser vide pour garder tous les champs).

### Manipuler les vecteurs 

* `sort(x)` ordonner.
* `rev(x)` renver l'ordre.
* `table(x)` tableau d'effectifs.
* `add_margins(table)` ajouter des totaux au tableaux.
* `unique(x)` valeurs uniques.
* `c(vec1, vec2)` concaténer deux vecteurs.
* `paste(vec1, vec2, sep = " ")` fusionner (concater) deux chaines.

	* `collapse = "separateur` concaténer les éléments de deux listes.

* `length(vec)` taille du vecteur.
* `sapply(aa, fonction)` appliquer une fonction à tous les éléments d'un vecteur.
* `factor(liste, levels = c("niv1, "niv2"))` créer une liste ordonée.
* `setdiff(vec1, vec2)` element du vecteur 1 non présent dans vec2.
* `intersect(vec1, vec2)` intersection de deux vecteurs.

### Listes

``` r
list(
  nom1 = c(1,2),
  nom2 = "texte"
)
```

## Matrices

* `matrix(vecteur, nrow = , ncol =)` transformer en matrice.
* `class.ind(vec)` créer une marice binaire à partir d'un vecteur avec les numéro des colonnes.

* `det(A)` déterminant.
* `dim(A)` dimension.
* `t(A)` transposer.
* `solve(A)` inverser une matrice.
* `A %*% B` mutiplication de matrices.
* `eigen(matrice)` valeurs propres (noyau).
* `dist(matrice, method  = "euclidean")` calculer la matrice des distances.

  * `manhattan`
  * `maximum`

* `scale(matrice)` centrer et réduire une matrice par colonne.

## Fonction

``` r
nomFonction <- function(x){
  instruction
}
```

### Les erreurs

* `try(log("ABC"), TRUE)` masque le message si une erreur se produit.
* `tryCatch(log("ABC"), error = function(e) {print("error")})` afficher un message quand la fonction produit une erreur.

## Condition 

```r
if (test_expression1) {
  instruction
} else if (test_expression2) {
  instruction
} else {
  instruction
}
```

`if(condition) do (instruction)` ou `if(condition) instruction`.

* `assign(nom, valeur)` créer des variables avec une boucle.
* `get(nom)` appeler une variable.
* `grepl(symbole, variable)` tester si le symbole est contenu dans la variable.

Opérateur	| Définition
------------|-----
`==`		| égale
`%in%`		| appartient
`!`     	| négation

## Boucles

!!! note
	cat permet de faire suivre le % d'une boucle `cat("\rÉtape", num_script, "/", for_nb_scripts, '-', script)`.

### For 

``` r
for(i in 1:nrow(g)){
	instruction
}
```

### While

### While - tant que c'est vrai

``` r
while(condition){
	instructions
}
```

## Les dates

Package : lubridate.

* `as_datetime()` convertir en date time.
* `as.Date('2017-10-12', format =)` convertir en date.

Définition	| R 	| Exemple
------------|-------|-------------
Année 		| `%Y`	| 2001
Année 		| `%y`	| 01
Mois 		| `%m`	| 09
Jour 		| `%d`	| 11
Heure 		| `%H`	| 12
Minute 		| `%M`	| 15
Seconde 	| `%S`	| 06

* `time_length(interval(date1, date2), type)` calculer un âge.
* `date + ajout` calculer une date
* `years(nbre)` année.
* `months(nbre)` mois.
* `days(3)` jour.
* `weekdays(nbre)` jour de la semaine.
* `hours(heure)` heure.
* `format(datetime, format = '')` format d'affichage d'une date et de l'heure.

## Le texte

* `nchar()` compter le nbre de caractères.
* `str_length(vecteur)` nombre de lettres de chaque élément.
* `str_sub(i, (text, start = debut, end = fin)` extraire une chaine de charactères.
* `grepl(expression_reguliere, chaine_a_verifier)` renvoie vrai si l'expression est détectée.
* `gsub(pattern = schéma, remplacement, variable_à_changer) ` remplacer un schéma ou un caractère par une nouvelle chaîne de caractères.
* `grepl("exemple", texte)` renvoie un booléen si la sous chaine est présente.
* `str_count(text, motif)` compter le nombre d'occurences (`stringr`).
* `strsplit(variable, symbole)` séparer une variable en fonction d'un symbole.
* `trim(texte)` supprimer les espaces (package `gdata`).
* `str_to_title(texte)` mettre les premiers caractères en majuscule (package `stringr`).
* `toupper(texte)` mettre les caractères en majuscule.

### Stringr

* `strsplit(texte)` supprimer les espaces à la fin et au début et les espaces doubles.

### Expressions régulières

Library `stringr`

* `str_view_all(vecteur, exp_re)` rechercher une expression régulière.
* `str_extract(texte, exp_re)` extraire un texte.
* `str_locate(texte, exp_re)` récupérer la postion de début et de fin.

Symbole	| Définition
--------|-----------------
`*`		| une ou plusieurs fois
`.` 	| jocker

## Connecter R à une bdd

Bibliothèque `library(DBI)`

* `dbListTables(connection)` Liste des tables.

### Connecteur

Connecteur	| Library	| Fonction
------------|-----------|---
MySQL 		| `RMySQL`	| `MySQL()`

### Créer une connexion.

```r 
dbConnect(MySQL(), paramètre)
on.exit(dbDisconnect(con))
```

Paramètres : 

* `dbname = "smur"`
* `host = "10.60.11.4"`
* `port = 3306`
* `user = "statistique"`
* `password = "statistique"`

* `requete = sqlInterpolate(connection, "SELECT * FROM acte WHERE acte_code = ?id", id = acteId)` créer et controler les variables utilisées dans la requete.
* `dbGetQuery(connection, requete)` exécuter la requete.

## R markdown 

* `echo = FALSE` masquer la sortie.
* `include = FALSE` masquer le code.

## Aléatoire

* `runif(nb, min, max)` générer un plusieurs nombres aléatoires entre deux bornes.
