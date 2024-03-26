## Calcul des paramètres pharmacocinétiques

`library(PKNCA)`

https://billdenney.github.io/pknca/news/index.html

!!! note
    La bibliothèque a été pensée pour intégrer de nouveaux indicateurs qui n'auraient pas été pensé par les auteurs.

Données minimum : concentration, dose, and time.

* zeros (0) below the limit of quantification.
* NA valeur manquante.

* `PKNCAconc()` pour les fécès et l'urine.
* `PKNCAdose()` pour les quantités administrées.
* `PKNCAdata(dt.concentration, dt.dose)` fusionner les tables doses et concentration.

### Les unités

`library(units)`

* `valid_udunits()` lister les unités valides.
* `valid_udunits_prefixes()` lister les ordres de grandeurs.
* `units(val_1) <- "km/s"` ou `set_units(x, unit[1], mode = "standard")` attribuer une unité ET convertir dans une autre unité.
* `deparse_unit(valeur)` récupérer l'unité.
* `mixed_units(df$valeurs, df$unite)` créer une vecteur avec des unités différentes (Attention, elles s'affichent pas dans les sorties des dataframes).
* `drop_units(x)` supprimer l'unité.

`library(purrr)`

Ajouter une unité aux colonnes à partir d'un vecteur avec les unités.

``` R
dt[,num_col] %>% map2_dfc(units, ~set_units(.x, .y, mode = "standard"))
```
 
!!! note
    Si deux jeux de données avec des unités différentes, elles sont converties durant la fusion.

### Rempsyc

Package avec de nombreuses fonctions pour 

!!! note 
    Il est normalement utiliser pour la Convenience functions for psychology.

https://rempsyc.remi-theriault.com/
