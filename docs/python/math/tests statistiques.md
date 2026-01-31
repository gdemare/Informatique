## Une distribution

## Un échantillon et une valeur théorique

## Paramètre de plusieurs échantillons

## Deux distributions

* `scipy.stats.wilcoxon(X1, X2)` test de Wilcoxon.
* `scipy.stats.ttest_rel(X1, X2)` test de Student pour des échantillons apparéiés (hypothèse : la différence suit une loi normale).
* `scipy.stats.ttest_1samp(X, meanpop)` test de Student pour comparer une moyenne théorique avec celle d'un échantillion.
* `scipy.stats.shapiro(X)` test de Shapiro, normalité.
* `scipy.stats.wilcoxon(x, y=None)` test de Wilcoxon (différence de médiane avec une valeur théorique ou un autre échantillon).
* `spicy.stats.f_oneway(X1, X2,...)` ANOVA.   

Sortie :

*  `.pvalue`

### Graphique

* `stats.probplot(data)` qqplot (`pylab.show()` pour afficher le graphique). 
* `statannotations` bibliothèque pour afficher les p-valeurs sur un boxplot.

## Corrélation

`statsmodels.stats.multitests` corriger les p-valeurs.
