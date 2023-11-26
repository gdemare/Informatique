`set.seed(123)` contrôler l'aléatoire.

## Indicateurs statistiques 

* `cor(vecteur1, vecteur2)` coefficient de corrélation.
* `mean(vecteur)` moyenne.
* `sd(vecteur)` écart-type.

## Loi de probabilité

Library : `stats`

### Loi normale

* `rnorm(nb, mean = 0, sd = 1)` générer nb nombres aléatoires suivant une loi normale.
* `dnom( vecteur, moyenne, ecart type)`  renvoie la densité de probabilité.
* `pnorm( quantile, moyenne, ecart type)` renvoie la probabilité inférieure à la valeur (fonction de répartition).

### Loi de Student

* `qt( alpha, df = degrès_liberté)` valeur f(x) = P(X<x).

### Khi-2

* `pchisq(quantile, degrés de liberté)` renvoie la probabilité inférieure à la valeur (fonction de répartition).
