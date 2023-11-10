### Les packages

* `install.packages("package")` installer un package.
* `library(package)` importer un package. 

### Manipuler les fichiers

* `basename("C:/some_dir/a.ext")` renvoyer le nom du fichier.
* `dirname("C:/some_dir/a.ext")` renvoyer le dossier.
* `list.file()` lister les fichiers et les répertoires.
* `setdiff(list.files(), list.dirs(recursive = FALSE, full.names = FALSE))` lister uniquement les fichiers.
* `setwd(dossier)` changer le dossier de travail.
* `getwd()` chemin du dossier de tavail.
* `source(fichier)` exécuter un script.


### Les meilleurs packages R

* `rmarkdown` R markdown.
* `tidyverse` intégre les packages les plus populaires pour la science de la donnée.

## Fonctions de base

* `print("Hello")` afficher un message.
* `cat("Hello\n")` afficher un message sans retour à ligne. Pour faire c'est dernier, il faut utiliser `\n`.
* `dput(variable)` afficher la variable à déclarer en code R.

## Environnement et variables

* `rm (list = ls())` supprimer les variables de l'environnement.
* `typeof(var)` renvoie le type de variable.

## Les vecteurs

### Créer un vecteur

* `c(2, 4, 6)` déclarer un vecteur.
* `2:6` séquence de 2 à 6 inclus.
* `seq(2, 3, by = 0.5)`
* `rep(1:2, times = 3 ou each = 3)` repéter la valeur alternée (1,2,1,2) ou à la suite (1,1,2,2).

* `date[nligne][ncol]` sélectioner une cellule.
* `data$colonne` sélectionner une colonne.
* `table[ligne, colonne]` sélectionner une ligne ou une colonne ou une cellule (laisser vide pour garder tous les champs).

### Créer une liste

```
list(
  Petal.Width = "width of the petal",
  Petal.Length = "length of the petal",
  Sepal.Width = NULL,
  Sepal.Length = NULL
)
```

## Les matrices

`matrix(vecteur, nrow = , ncol =)` transformer en matrice.

* `det(A)` déterminant.
* `dim(A)` dimension.
* `t(A)` transposer.
* `solve(A)` inverser une matrice.
* `A %*% B` mutiplication de matrices.
* `eigen(matrice)` valeurs propres (noyau).

### Manipuler les vecteurs 

* `sort(x)` ordonner.
* `rev(x)` renver l'ordre.
* `table(x)` tableau d'effectifs.
* `unique(x)` valeurs uniques.
* `c(vec1, vec2)` concaténer deux vecteurs.
* `paste(vec1, vec2, sep = " ")` fusionner (concater) deux chaines.

	* `collapse="separateur` concaténer les éléments de deux listes.

* `length(vec)` taille du vecteur.
* `sapply(aa, fonction)` appliquer une fonction à tous les éléments d'un vecteur.
* `factor(liste, levels = c("niv1, "niv2"))` créer une liste ordonée.

## Fonction

```
nomFonction <- function(x){
  instruction
}
```

### Try catch 

Try catch permet d'éviter que le programme plante lorsqu'il y a une erreur.

```
foo <- function( x, y ){
   tryCatch(
     expr = {
       return( x + y )
     },
     error = function(e){
       print(
         sprintf("An error occurred in foo at %s : %s",
                 Sys.time(),
                 e)
         )
     })
}
```

## Condition 

```
if ( test_expression1) {
  instruction
} else if ( test_expression2) {
  instruction
} else {
  instruction
}
```

* `assign(nom, valeur)` créer des variables avec une boucle.
* `get(nom)` appeler une variable.

Opérateur	| Définition
------------|-----
`==`		| égale
`%in%`		| appartient
`!`     	|

## Boucles

### For 

```
for(i in 1:nrow(g)){
	instruction
}
```

### While

### While - tant que c'est vrai

```
while(condition){
	instructions
}
```

## Manipuler les dates

Package : lubridate.
* `as_datetime()` convertir en date time.


* `as.Date('2017-10-12', format = )` convertir en date.

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

## Manipuler le texte

* `nchar()` compter le nbre de caractères.
* `str_sub(i, (text, start = debut, end = fin)` extraire une chaine de charactères.
* `gsub(schéma, remplacement, variable) ` remplacer un schéma par une nouvelle chaîne de caractères.
* `str_count(text, motif)` compter le nombre d'occurences (`stringr`).
* `gsub( pattern = "[.]", "_", "texte à change" )` remplacer un caractère.
* `strsplit(variable, symbole)` séparer une variable en fonction d'un symbole.
* `trim(texte)` supprimer les espaces (package `gdata`).
* `str_to_title(texte)` mettre les premiers caractères en majuscule (package `stringr`).
* `toupper(texte)` mettre les caractères en majuscule.

### Stringr

* `strsplit(texte)` supprime les espaces a la fin et au début et les espaces doubles.

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

```
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
