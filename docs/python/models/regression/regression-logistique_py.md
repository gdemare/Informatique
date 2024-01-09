```
logreg = sklearn.linear_model.LogisticRegression(C=100)
logreg.fit(X, Y)
logreg.score(X, Y)
```

* `logreg.coef_[0]` coefficient pour chaque variable.
* `logreg.intercept_` ordonnée à l'origine.
