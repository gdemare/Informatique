`set.seed(123)` contrôler l'aléatoire.

## Indicateurs statistiques 

* `cor(vecteur1, vecteur2)` coefficient de corrélation.
* `mean(vecteur)` moyenne.
* `sd(vecteur)` écart-type.
## Loi de probabilité

`library(stats)`

### Loi uniforme

* `runif(n, min, max)` renvoie n nombres aléatoires d'une loi continue uniforme.

### Loi normale

* `rnorm(nb, mean = 0, sd = 1)` générer plusieurs nombres aléatoires suivant une loi normale.
* `dnom(vecteur, moyenne, ecart_type)`  renvoie la densité de probabilité.
* `pnorm(quantile, moyenne, ecart_type)` renvoie la probabilité inférieure à la valeur (fonction de répartition).
### Loi de Student

* `qt(alpha, df = degrès_liberté)` valeur $f(x) = P(X \lt x)$.
### Khi-2

* `pchisq(quantile, degrés_liberté)` renvoie la probabilité inférieure à la valeur (fonction de répartition).
## Les tests

* `shapiro.test(x)` Shapiro-Wilk pour la normalité.
* `bartlett.test()` test de Bartlett.
* `chisq.test(table(x,y))` test d'association du Khi2.
* `ks.test(x, y)` test de Kolmogorov-Smirnov.
### Graphiques
`library("ggstatsplot")`
* `ggbetweenstats(df, group, value)` faire un graphique et le test.

### Indicateur
*  `DescTools::Gini(table_contigence)` coefficient de Gini (0 égalité parfaite et 1 inégalité parfaite).
