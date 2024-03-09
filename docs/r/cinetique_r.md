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
* `set_units(1, umol/L)` ajouter une unité à des valeurs.

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
