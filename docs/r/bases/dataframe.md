## Créer un dataframe

* `data.frame(col1 = vect1, col2 = vect2)` créer un dataframe.
* Créer un dataframe vide :

	* `data.frame(matrix(ncol = length(col_names), nrow = 0))`
 	* `data.frame(col1 = type, col2 = type)` 

* `as.data.frame(lapply(donnees, type.convert))` réidentifier le type de variables d'un dataframe.
* `expand.grid(col1 = vec1, col2 = vec2)` renvoie un dataframe avec la combinaison des vecteurs.

Transformer une liste en dataframe :

``` R
data.frame(
    niveau = rep(seq(length(liste)), lengths(liste)),
    debut = matrix(unlist(liste))
  ) 
```

* `transpose(df)` tranformer un dt en liste de lignes (`library(purrr)`).

### Renommer les colonnes

* `setNames(c('pos_row','pos_col'))` ajouter un nom de colonnes.
* `rename(new_nom = old_nom)` ou `c(new_nom = old_nom)` renommer une colonne.
* `rename_with(~paste(., "0"), .cols = everything())` renommer les colonnes (`.cols` préciser les colonnes à renommer). 
* `rename(!!!setNames(col_units$old_name, col_units$new_name))` renommer les colonnes à partir d'un dataframe.
* `dplyr::rename_with(~ unlist(dt_TK_labels), all_of(names(dt_TK_labels)))` renommer a partir d'une liste.

!!! example
	Renommer la colonne uniquement is elle existe `rename_with( ~ "nv nom", .cols = any_of("col1"))`

#### Libellés des colonnes

Packages `library(labelled)`

* `var_label(dt) <- labels` ajouter un label aux colonnes.
* `var_label(dt)` renvoie les labels (ou attribuer un label). Prend comme valeur une `list(nom_col = "label")`.
* `remove_var_label(dt)` supprimer les labels.
* `colnames(df_labelled) <- var_label(df_labelled)` renommer les colonnes avec les labels.
## Importer et exporter

### Importer

* `read_sas(fichier)` lire des tables SAS (package `haven`).
* `read.csv(ficher, sep = separateur)` lire une table CSV.
* `read.table(fichier)` importer un fichier avec des espaces comme séparateur.
* `read.xlsx(fichier, colNames = TRUE, sheet = nom/num)` lire un fichier excel (workbook = wb) `library(openxlsx)`. Paramètres :

	* `startRow = 2` numéro de la ligne où commencer la lecture. 
### Exporter
 
* `write.csv(donnée, file = "fichier.csv" )` enregistrer au format csv.

	* `sep = separateur` séparateur.
	* `row.names = T` nom des lignes.
	* `col.names = T` nom des colonnes.

* `write.table(tableau, file = "clipboard", sep = "\t")` copier dans le presse papier.
### Information sur un df

`library(tibble)`

* `nrow(data)` renvoie le nbre de lignes.
* `ncol(data)` renvoie le nbre de colonnes.
* `dim(data)` renvoie la taille du data.
* `glimpse(dataset)` description du jeu de données.
* `str(dt)` décrire un jeu de données.
#### Noms des lignes et des colonnes

* `colnames(data)` nom des colonnes.
* `rownames(data)` nom des colonnes.
* `column_to_rownames(var = "Accession")` mettre une colonne en nom de lignes et supprimer la colonne.
* `rownames_to_column()` transformer l'index en colonne et supprimer le nom des lignes.
* `rowid_to_column()` transformer le numéro des lignes en colonne.

## Manipuler les données avec dplyr

Package : `dplyr`, `tidyr`. `résultat1 %>% résultat2` : rediriger le résultat

* `pull(data, colonne)` transformer une sortie en vecteur.

### Fonctions dplyr

Pour créer des fonctions dplyr `{{colonne}}`.
``` r
max_by <- function(data, var, is_true) {
  data %>%
	filter(is_true) %>%
    mutate({{var}} := {{var}} + 1)
}
```

* `enquo(col1)` récupérer le nom de la colonne (penser à la convertir en caractère `rlang::as_label()`).

!!! note
	Pensez à utiliser `tryCatch({...}, error = function(e) {})` lorsque que un paramètre n'est pas nécessairement un nom de colonne dplyr.

Sélecteur de colonnes :

* `across(.cols, .fns, ..., .names = NULL, .unpack = FALSE)` sélectionner des colonnes avec vecteurs textes.
* `if_any(.cols, .fns, ..., .names = NULL)`
* `if_all(.cols, .fns, ..., .names = NULL)`

!!! note
	Pour créer une fonction qui s'applique à un vecteur il peut être utile d'utiliser `map`.

### Filtrer

* `filter(condition)` filtrer les données avec une condition (alternative `subset(df, condition)`, pour filter en fonction des noms de lignes `row.names(r$df_pk) %in% filter`).
* `slice(numligne)` garder les lignes.
* `slice_min(col)` ou `slice_max(col)` sélectionner les lignes avec les valeurs min ou max pour la colonne.
* `sample_frac(dt, 0.5, replace = TRUE)` sélectionne aléatoirement une fraction d'observations.
* `sample_n(nligne, replace = TRUE)` sélectionne aléatoirement n observations.
* `slice(10:15)` sélectionne les lignes selon leur position.
* `top_n(nlignes, variable)` sélectionne et ordonne les n premières observations (ou groupes si les données sont groupées) (`desc()` = décroissant).
* `is.na(data)` renvoie les lignes avec des valeurs manquantes (`myDataframe[is.na(dt)] = 0` pour les remplacer).
* `complete.cases(data)` renvoie les lignes avec des valeurs manquantes.
* `case_when(condition1 ~ val1, condition2 ~ val2,..., .default = val)` fonction équivalente au CASE WHEN en SQL.

### Sélectionner
* `select(colonne1, colonne2)` selecionner des colonnes (`-one_of(col)` pour enlever une colonne). Soit avec les numéros, soit avec les noms.

En fonction de la position :

* `everything()` toutes les colonnes restantes.
* `all_of(vecteur)` les colonnes avec le nom de la colonne dans le vecteur.
* `one_of(vecteur)` les colonnes avec le nom de la colonne dans le vecteur. Fonctionne même si la colonne n'existe pas.
* `any_of(vecteur)` les colonnes dont le nom de la colonne n'est pas dans le vecteur.
* `last_col()` la dernière colonne.
* `group_cols()` les colonnes utilisées pour grouper les données.
* `num_range()` la position
* `where(function(){})` les colonnes qui retournent vraies.

!!! example 
	`select(col13, everything())` déplacer la colonne 13 à la position 1.

En fonction du nom des colonnes :

* `distinct()` supprimer les doublons (renvoie les valeurs uniques pour une variable).

	* `.keep_all = TRUE` garder tous les champs.

* `arrange(var1, var2)` trier en ordre décroisssant `desc(var)`.

 * `.by_group = TRUE` trier par groupe.

* `dt[["col1]]` sélectionner une colonne avec son nom en caractère en dehors de dplyr.
* `relocate(col, .before = /.after = )` changer la position d'une colonne.
	* `last_col()` a la dernière colonne.   

!!! note
	Pour trier une colonne, il faut `factor(x, levels = c("el1", "el2"))`.

Fonction 						| Définition
--------------------------------|---
`starts_with(c("deb1", "deb2"))`| commence par.
`ends_with(fin)`				| finit par.
`contains(chaine)`				| contient la chaine.
`matches(expr_regu)` 			| correspond à l'expression régulière.

!!! note 
 	Utile notamment pour renommer les colonnes `rename_with(~fonction(.), .cols = expression)`.
 
### Réorganiser les données

Package `tidyr`

* `pivot_longer(cols = col_a_trans, names_to = "nv_nom", values_to = "value")` transformer plusieurs colonnes en une seule variable (pas besoin de préciser les colonnes que l'on souhaite garder).
	* `values_fill = 0` valeur utilisée pour les NA. 
* `pivot_wider(names_from = "name", values_from = "value")` transformer les modalités en colonnes.

	* `id_cols = cols` préciser les colonnes à conserver en id de lignes.
	* `values_fill = val` remplacer les valeurs manquantes.

``` r
# La variable treatment (avec les modalités A, B, C ...) est transformée en colonne (A, B, C, D). La valeur est la somme des decrease. Chaque ligne correspond à une valeur de rowpos.
OrchardSprays %>% 
  select(rowpos, treatment, decrease) %>%
  pivot_wider(names_from = treatment, values_from = decrease)
```

Sélectionner les colonnes : 

* `everything()` toutes les colonnes restantes.

### Créer de nouvelles variables

* `mutate(nom = formule)` appliquer une fonction et ajouter une colonne (il est possible d'appliquer à toutes les variables avec `sapply` voir ci dessous et, de sélectionner une variable par son nom avec `!!sym("col1")`).
* `mutate_all(~as.character(.x))` appliquer la fonction à toutes les colonnes.
* `mutate_if(~fct_test(.x), function(x){drop_units(x)})` ou `mutate_if(is.numeric, round, digits = 2)`appliquer une fonction aux colonnes avec Vrai.
* `mutate_at(vars(all_of(tr_pk$PPTESTCD)), ~ifelse(end == Inf, T, .))` appliquer une fonction a des colonnes particulières.

!!! note
	Pour ajouter une colonne qui n'existe pas `mpg = ifelse("mpg" %in% names(.), mpg, NA))`.

Options :

* `.before = Value` ou  `.after=` préciser où insérer la colonne.
* `.keep ="none"` ne garder aucune colonne.

!!! note 
	Pour utiliser le nom d'une variable stockée dans une variable caractère `mutate(!!variable_text := ifelse(condition, !!sym(variable), NA))`.

!!! note
	Pour modifier uniquement certaines lignes, il est possible d'utiliser  `ifelse(condition, valeur_vrai, valeur_vaux)`.

!!! note 
	Pour appliquer une fonction a toutes les variables il faut utiliser `sapply`.

| Fonction                  | Description                                                                   |
| ------------------------- | ----------------------------------------------------------------------------- |
| `n()`                     | Nombre de lignes.                                                             |
| `n_distinct()`            | Nombre de lignes distinctes.                                                  |
| `lead()`                  | Récupérer la valeur de la ligne d'avant.                                      |
| `lag(col, default = 0/1)` | Récupérer la valeur de la colonne/ligne d'après .                             |
| `dense_rank()`            | Ordonner sans sauts de rangs.                                                 |
| `min_rank()`              | Ordonner avec sauts de rangs.                                                 |
| `percent_rank()`          | Rangs de (min rank) entre [0, 1].                                             |
| `row_number()`            | Ordonner ou numéroter les lignes en affectant aux liens la première position. |
| `ntile()`                 | Diviser en n groupes.                                                         |
| `between()`               | Les valeurs sont-elles entre a et b.                                          |
| `cum_dist()`              | Distribution cumulée                                                          |
| `cumall()`                | Cumul tant que vrai.                                                          |
| `cumany()`                | Cumul dès que vrai.                                                           |
| `cummean()`               | Moyenne glissante.                                                            |
| `cumsum()`                | Somme cumulée.                                                                |
| `cummax()`                | Maximum cumulé.                                                               |
| `cummin()`                | Minimum cumulé.                                                               |
| `cumprod()`               | Produit cumulé.                                                               |
| `pmax()`                  | Maximum par élément.                                                          |
| `pmin()`                  | Minimum par élément.                                                          |
| `last()`                  | Garder la dernière valeur.                                                    |
| `first()`                 | Garder la première valeur.                                                    |
| `nth(col, n)`             | Garder la n-ième valeur.                                                      |
| `cur_group_id()`          | Id pour chaque groupe (`group_by`).                                           |
 
!!! note
	Pour les sommes cumulées, il faut utiliser `group_by` puis `mutate`.

 !!! note 
 	`row_number()` renvoie aussi le numéro de chaque ligne.
 
### Remplacer une valeur

* `if_else(condition, true = , false = , missing = )` si alors avec la possibilité de traiter les valeurs manquantes.
* `replace(colonne, which(col == 'Vrai'), new_value)` remplacer des valeurs en fonction d'une condition.

!!! example 
	`which(col == 'Vrai')[n]` pour remplacer la première valeur ayant la condition vraie.
### Apply en lignes et colonnes

Fonction 		| Définition
----------------|-------------
`rowSums()`		| Somme
`colMeans()`	| Moyenne (`colMeans(is.na(data))` utile pour connaitre le pourcentage de valeurs manquantes).

* `sapply(dt, axis = 1/2, fonction)` appliquer une opération à toutes les colonnes ou les lignes.

## Grouper les données

`data %>% group_by(columns) %>% summarise(indicateur)`

Grouper les données :

* `group_by(var)` grouper les observations par la var (toujours suivi de `summarise`).
* `ungroup(iris)` dégrouper le jeu de données.
* `group_split()` séparer le jeu de données en plusieurs (précédé d'un `group_by`).
* Appliquer des fonctions chaque groupe :

``` r
group_map(function(x, row_id) {
    x %>% transmute(
      var1 = a + b,
      var2 = c/2)
}
```
Calculer des indicateurs par groupe :

* `group_vars()` print the names of grouping variables.
* `tally(sort = T)` tableau des effectifs.
* `summarise(nom = formule)` appliquer une fonction.
* `summarise_all(fonction)` appliquer une fonction à chaque variable.
* `count(variable, wt = valeur)` dénombrer le nombre d'observations de chaque valeur d'une variable.

Fonction 		| Défintion
----------------|---
`min`			| Minimum
`max`			| Maximum
`mean` 			| Moyenne
`median` 		| Médiane
`sd` 			| Ecart-type

!!! note
	`group_by()` peut s'utiliser avec `mutate()` pour appliquer une fonction à chaque groupe, `slice(n)` pour garder les n premières lignes de chaque groupe.

### Les jointures

`A %>% jointure(B)`

* `inner_join(data)` A et B
* `left_join(data)` A (+ A et B)
* `right_join(data)` B (+ A et B)
* `semi_join(data)` B et pas A.
* `anti_join(data)` A et pas B.
* `full_join(data)` A ou B.

Option :

* `by = c("col1" = "col2")` préciser la jointure.
* `keep = T` garder les colonnes qui ont servi de jointure.

!!! note
	Pour comparer deux dataframes, on peut utiliser `anti_join()`. Les lignes différentes seront renvoyées.

### Fusions lignes et colonnes

* `bind_cols(nom = valeur)` ajouter à y comme nouvelles colonnes.
* `add_column(data, column,...)` ajouter de nouvelles colonnes (`tibble`).
* `add_row(x = 4, y = 0)` ajouter une ligne.
* `merge_v(j = ~ niv1, target = c("niv1", "niv2"))` fusionner en colonne.
* `bind_rows(df2)` fusionner deux dataframes au niveau des lignes (ajout au niveau des colonnes avec un nom identique).
* `dt[nrow(dt) + 1,] = vecteur` ajouter une ligne sous forme de vecteur.

## Opérateurs ensemblistes

* `intersect(y, z)` observations appartenant à y et z.
* `setdiff(y, z)` observations appartenant à y et pas à z.
* `union(y, z)` observations appartenant à y et z ou l'un des 2.
