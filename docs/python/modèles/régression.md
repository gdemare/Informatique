### Avec sklearn

`import sklearn.linear_model`

1. Déclarer le modèle.
2. Ajuster le modèle `modele.fit(x,y)`

Les types de régressions :

* `LinearRegression()` régression linéaire.
* `LogisticRegression()` régression logistique.

Paramètres : 

* `C=100`

Retourne :

* `logreg.coef_[0]` coefficient (ou poids) pour chaque variable.
* `logreg.intercept_` ordonnée à l'origine.

### Avec le module stats

`model_res = stats.linregress(x, y)`

`model_res.slope` coefficient directeur.
`model_res.intercepts` ordonné à l'origine.
`model_res.rvalue`    
