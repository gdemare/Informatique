## Créer un dataframe

* `data.frame(col1 = vect1, col2 = vect2)` créer un dataframe.
* `data.frame(col1 = type, col2 = type)` créer un dataframe vide.

### Libellés des colonnes

Packages `Hmisc`, `labelled`

* `var_label(dt)` renvoie les labels (ou attribuer un label). Prend comme valeur une `list(nom_col = "label")`.
* `remove_var_label(dt)` supprimer les labels.

## Importer les données

* `read_sas(fichier)` lire des tables SAS (package `haven`).
* `read.csv(ficher, sep = separateur)` lire une table CSV.
* `read.table(fichier)` importer un fichier avec des espaces comme séparateur.

## Excel 

Pour manipuler les fichiers excel, il est préférable d'utiliser `library(openxlsx)` qui est la bibliothèque la plus complète.

* `read.xlsx(fichier, colNames = TRUE, sheet = )` lire un fichier excel.
* `readWorkbook(bbq, sheet = "Supplies")` lire un fichier excel.
* `wb <- createWorkbook()` créer un classeur.
* `saveWorkbook(wb, "file.xlsx")` enregistrer un classeur. Paramètres :

	* `overwrite = TRUE` écraser la version existente.

* `addWorksheet(wb = wb, sheetName = "feuill")` ajouter une feuille.
* `writeData(wb = wb, sheet = "feuill", x = df, )` écrire un dataframe. Paramètres :

	* `headerStyle = headerStyle` style des entetes (voir style)
	* `borders = "n"`

#### Style 

`createStyle()`

* `fontColour = "#006100"` couleur de la police.
* `bgFill = "#C6EFCE"` fond.
* `textDecoration = "Bold"` gras.

#### Formater le classeur

* `setColWidths(wb = wb, sheet = "feuil", cols = 1:4, widths = "auto")` largeur des colonnes.

## Exporter un data
 
* `write.csv(donnée, file = "fichier.csv" )` enregistrer au format csv.

	* `sep = separateur` séparateur.
	* `row.names = T` nom des lignes.
	* `col.names = T` nom des colonnes.

* `write.table(tableau, file = "clipboard", sep = "\t")` copier dans le presse papier.

### Information dataframe et nom des lignes eet des colonnes

* `colnames(data)` nom des colonnes.
* `rownames(data)` nom des colonnes.
* `column_to_rownames(var = "Accession")` mettre une colonne en nom de lignes et supprime la colonne.
* `rownames_to_column()` transformer l'index en colonne.
* `rowid_to_column()` transformer le numéro des lignes en colonne.
* `nrow(data)` renvoie le nbre de lignes.
* `ncol(data)` renvoie le nbre de colonnes.
* `dim(data)` renvoie la taille du data.
* `glimpse(dataset)` description du jeu de données.

## Décrire un jeu de données

* `str(dt)` décrire un jeu de données.

## Manipuler les données avec dplyr

Package : `dplyr`, `tidyr`. `résultat1 %>% résultat2` : rediriger le résultat

* `pull(data, colonne)` transformer une sortie en vecteur.


Les fonctions avec dplyr

```
max_by <- function(data, var, by) {
  data %>%
    group_by({{ by }}) %>%
    summarise(maximum = max({{ var }}, na.rm = TRUE))
}
```

## Filtrer

* `filter(condition)` filtrer.
* `slice(numligne)` garder les lignes.
* `sample_frac(dt, 0.5, replace = TRUE)` sélectionne aléatoirement une fraction d'observations.
* `sample_n(nligne, replace = TRUE)` sélectionne aléatoirement n observations.
* `slice(10:15)` sélectionne les lignes selon leur position.
* `top_n(nlignes, variable)` sélectionne et ordonne les n premières observations (ou groupes si les données sont groupées) ( `desc()` = decroissant ).
* `is.na(data)` renvoie les lignes avec des valeurs manquantes (`myDataframe[is.na(dt)] = 0` pour les remplacer).
* `complete.cases(donnees)` renvoie les lignes avec des valeurs manquantes.

## Selectionner

* `select(colonne1, colonne2)` selecionner des colonnes (`-one of(col)` pour enlever une colonne). Soit avec les numéros, soit avec les noms.
  
	* `contains('texte')` sélectionner des colonnes avec le texte dans le nom.
	
* `select_if(is.numeric)` selectionner en fonction d'une condition.

	* `matches(expr_regu)` sélectionner en fonction d'une expression régulière

* `distinct()` supprimer les doublons (renvoi les valeurs uniques pour une variable).

	* `.keep_all = TRUE` garder tous les champs.

* `arrange(var1, var2)` trier en ordre décroisssant `desc(var)`.

Fonction 				| Définition
------------------------|---
`starts_with(debut)`	| les variables commançant par...
`ends_with(fin)`		| les variables finissant par...
`contains(chaine)`		| contenant la chaine.

## Réorganiser les données

Package `tidyr`

* `pivot_longer(cols, names_to = "name", values_to = "value")` transformer plusieurs colonnes en une seule variable.
* `pivot_wider(names_from = "name", values_from = "value")` transformer plusieurs variables en une seule colonne.

```
# La variable treatment (avec les modalités A, B, C ...) est transformée en colonne (A, B, C D). La valeur est la somme des decrease. Chaque ligne correspond à une valeur de rowpos.
OrchardSprays %>% 
  select(rowpos, treatment, decrease) %>%
  pivot_wider(names_from = treatment, values_from = decrease)
```

## Construire de nouvelles variables

* `mutate(nom = formule)` appliquer une fonction et ajouter une colonne.
* `transmute(nom = formule)` construitre une ou plusieurs variables en supprimant les colonnes.

!!! note
	Pour modifier uniquement certaines lignes, il est possible d'utiliser  `ifelse(condition, valeur_vrai, valeur_vaux)` 

Fonction		| Description
----------------|-----------
`n` 			| Nombre de lignes.
`n_distinct` 	| nombre de lignes distinctes.
`lead`			| Copier avec des valeurs décalées à gauche.
`lag` 			| Copier avec des valeurs décalées à droite.
`dense_rank` 	| Ordonner sans sauts de rangs.
`min_rank` 		| Ordonner avec sauts de rangs.
`percent_rank`	| Rangs de (min rank) entre [0, 1].
`row_number`	| Ordonne en affectant aux liens la première position.
`ntile` 		| Divise en n groupes.
`between` 		| Les valeurs sont-elles entre a et b.
`cum_dist` 		| Distribution cumulée
`cumall` 		| Cumul tant que vrai.
`cumany` 		| Cumul dès que vrai.
`cummean` 		| Moyenne glissante.
`cumsum` 		| Somme cumulée.
`cummax` 		| Maximum cumulé.
`cummin` 		| Minimum cumulé.
`cumprod` 		| Produit cumulé.
`pmax` 			| Maximum par élément.
`pmin` 			| Minimum par élément.

### Faire une opération sur toutes les variables ou les lignes

Fonction 		| Défintion
----------------|-------------
`rowSums()`		| Somme
`colMeans()`	| Moyenne (`colMeans(is.na(donnees))` utile pour connaitre le pourcentage de valeurs manquantes).

* `apply(dt, axis = 1/2, fonction)` appliquer une opération à toutes les colonnes ou les lignes.

## Grouper des données

`data %>% group_by(columns) %>% summarise( indicateur)`

Grouper les données :

* `group_by(var)` grouper les observations par la var (toujours suivi de `summarise`).
* `ungroup(iris)` dégrouper le jeu de données.

Calculer des indicateurs par groupe :

* `summarise(nom = formule)` appliquer une fonction.
* `summarise_each(funs(fonction))` appliquer une fonction à chaque variable.
* `count(variable, wt = valeur)` Dénombre le nombre d'observations de chaque valeur d'une variable.

Fonction 		| Défintion
----------------|---
`first` 		| Première valeur d'un vecteur
`last` 			| Dernière valeur d'un vecteur
`inth` 			| Nième valeur d'un vecteur
`n` 			| Nb de valeurs
`n_distinct`	| Nb de valeurs distinctes
`min`			| minimum
`max`			| maximum
`mean` 			| Moyenne
`median` 		| Médiane
`sd` 			| Ecart-type

### Les jointures

`A %>% jointure(B, <by = c("var1" = "var2")> )`

* `inner_join(data)` A et B
* `left_join(data)` A (+ A et B)
* `right_join(data)` B (+ A et B)
* `semi_join(data)` A et pas B.
* `anti_join(data)` B et pas A.
* `full_join(data)` A ou B. Option :

	* `by = c("col1" = "col2")` préciser la jointure.

## Fusions lignes et colonnes

* `bind_cols(nom = valeur)` ajoutez à y comme nouvelles colonnes.
* `bind_rows(df2)` fusionner deux dataframes au niveau des lignes (ajout au niveau des colonnes avec un nom identique).
* `dt[nrow(dt) + 1,] = vecteur` ajouter une ligne sous forme de vecteur.

## Opérateurs ensemblistes

* `intersect(y, z)` observations appartenant à y et z.
* `setdiff(y, z)` observations appartenant à y et pas à z.
* `union(y, z)` observations appartenant à y et z ou l'un des 2.

## Discrétiser des variables

* `discretize(var, categories = nbre groupe, label = )` discrétiser une variable (package : `arules`).

	* `method = "frequency"` méthode.
	* `categories = nbre` nombre de classes.

* `cut2(var, breaks, minmax=T)` découper en classe en fonction du verteur borne`(val1;[` (package Hmisc).
* `smbinning(df = data, y = "var", x = "var_quanti")` discrétiser de facon optimale les varibles du data pour un score. (packages : smbinning); y doit être de type integer.

	* `$cuts` bornes.
 
## Autres fonctions

* `model.matrix(var1)` dichotomiser un data (tableau disjonctif).
* `na.exclude(data)` supprimer les lignes avec au moins une valeur manquante.
* `case_when(condition1 ~ val1, condition2 ~ val2,...)` fonction équivalente au CASE WHEN en sql.
* `scale(fromage, center = T, scale = T)` centrer et réduire les données.
* `Sys.sleep(seconde)` attendre un nombre de seconde avant la suite de l'exécution.
* `grepl( symbole, variable)` tester si le symbole est contenu dans la variable.
