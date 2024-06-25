## Rmarkdown

Option pour `{R}` :

* `echo=FALSE` masque le code.
* `include = FALSE` masque les graphiques et le code.
* `message = FALSE` masque les résultats du code.

## Les tableaux

### Flextable

`library(flextable)` Exporter des tableaux et les dataframes dans des rapports hmtl et word.

* `flextable(dt)` transformer en flextable.
* `as_flextable(list)` convertir un data.

####  gt 

`libary(gt)`

[gtsummary](https://www.danieldsjoberg.com/gtsummary/) permet de ganger du temps dans certaines mise en forme. 

Comparaison des différents packages pour le faire des tableaux https://hughjonesd.github.io/huxtable/design-principles.html par le créateur de huxtable.

[gtExtras](https://jthomasmock.github.io/gtExtras/index.html) pour ajouter des graphiques ou des images dans le tableau.

### knitr - markdown

`library(knitr)`

* `knitr::kable(data)` afficher un tableau en markdown. Paramètres :

	* `caption="Example dosing data extracted from theophylline data set"` ajouter un titre.
