## Une distribution

## Un échantillon et une valeur théorique

## Paramètre de plusieurs échantillons

## Deux distributions

* `scipy.stats.wilcoxon(X1, X2)` test de Wilcoxon.
* `scipy.stats.ttest_rel(X1, X2)` test de Student pour des échantillons apparéiés (hypothèse : la différence suit une loi normale).
* `scipy.stats.ttest_1samp(X, meanpop)` test de Student pour comparer une moyenne théorique avec celle d'un échantillion.
* `scipy.stats.shapiro(X)` test de Shapiro, normalité.

Sortie :

*  `.pvalue`

### Graphique
wilcoxon
* `stats.probplot(data)` qqplot (`pylab.show()` pour afficher le graphique). 

## Corrélation

`statsmodels`
