* `model.matrix(var1)` dichotomiser un data (tableau disjonctif).
* `na.exclude(data)` supprimer les lignes avec au moins une valeur manquante.
* `scale(fromage, center = T, scale = T)` centrer et réduire les données.

## Validation croisé

`library(rsample)`

``` r
split <- initial_split(dataset, 0.8)
dt_train <- training(split)
dt_test <- testing(split)
```

## Collération et colinéarité

`library(caret)`

* `nearZeroVar(mdrrDescr, saveMetrics= TRUE)` afficher les colonnes avec une variance nulle.
* `findCorrelation(data)` afficher les groupes de variables corrélées.
* `findLinearCombos(data)` afficher les combinaisons linéaires.

## Discrétiser

* `discretize(var, categories = nbre groupe, label = )` discrétiser une variable (package : `arules`).

	* `method = "frequency"` méthode.
	* `categories = nbre` nombre de classes.

* `cut2(var, breaks, minmax=T)` découper en classe en fonction du verteur borne`(val1;[` (package Hmisc).
* `smbinning(df = data, y = "var", x = "var_quanti")` discrétiser de facon optimale les varibles du data pour un score. (`library(smbinning)`); y doit être de type integer.

	* `$cuts` bornes.