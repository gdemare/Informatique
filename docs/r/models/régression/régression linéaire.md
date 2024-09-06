`model <- lm(Y~., data = dt)` créer une régression linéaire.

Retourne : 

* `$coefficients` les coefficients pour chaque variable.

`summary(mod)` résumé détaillé du modèle.

Retourne :

* Std. Error (Std. Error) :  écart type de l'estimation du coefficient.
* Test de significativité pour savoir si le coefficent est il égale à 0. 
* R-squared ou $R^2$ coefficient de détermination.

## Vérifier la validité

`plot(model)` affiche quatre graphiques sur les résidus : 

* residuals vs fitted : vérifier l'homoscédasticité et de mettre en valeur la non linéarité de la relation, par exemple avec des formes en U ou en V.
* q-q residuals : vérifier si les résidus suivent une distribution normale.
* scale location : vérifier l'homoscédasticité.
* residuals vs leverage : identifier les observation qui ont une influence disproportionnée sur le modèle.
