`library(nnet)`

```
nnet(data= , cible~variables, size=nb_couche, maxit=nb)
```
Paramètres :
* `size=nb` nombre de couches cachées.
* `maxit=nb` nombre d'itérations maximum.

Option :

* `weights = poids` 

Valeur :

* `$wts` poids des neurones.
* `$value` value of fitting criterion plus weight decay term.
* `$fitted.values` the fitted values for the training data.
* `$residuals` résidus du jeu d'apprenissage.the residuals for the training data.
* `$convergence` nombre d'itérations.

## Prédiction 

`predict(modele, newdata=test, type=)`
`type=` :
* `class` renvoie la probabilité d'appartenance pour chaque classe
* `raw` renvoie la modalité la plus probable.
