Les types de données sont sans `as`.

Fonction               | Type
-----------------------|---
`as.character()`       | caractère
`as.integer()`         | nombre entier
`as.double()`          | décimal
`as.Date(character())` | date 
`as.vector()`          | en vecteur

!!! note
  `is.numeric(x)` pour savoir si la valeur est du bon type.

Les variables des dataframe sont par defaut en Factor.

* `pull(nom ou numero)` convertir une colonne en vecteur (package `dplyr`).
* `unlist(list)` transformer une liste en vecteur.
