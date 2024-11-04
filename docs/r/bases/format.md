Les types de données sont sans `as`.

Fonction               | Type
-----------------------|---
`as.character()`       | caractère
`as.integer()`         | nombre entier
`as.double()`          | décimal
`as.Date(character())` | date 
`as.vector()`          | en vecteur
`as.logical()`         | en booléen

`as("T", "logical")` changer le type d'une variable.

!!! note
    `is.numeric(x)` pour savoir si la valeur est du bon type.

Les variables des dataframe sont par defaut en Factor.

* `pull(nom ou numero)` convertir une colonne en vecteur (package `dplyr`).
* `unlist(list)` transformer une liste en vecteur.
* `droplevels(facteur)` supprimer les facteurs.

### Formater les nombres

* `signif(x,3)` nbre de chiffres significatifs.
* `round(x,0)` arrondir la valeur.
* `prettyNum(nb)` convertir une valeur numérique en texte.

    * `scientific = F` ne pas afficher de puissances.
