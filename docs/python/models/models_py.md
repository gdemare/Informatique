## Jeu de données

`from sklearn.model_selection import train_test_split`

*`X_train, X_test, y_train, y_test = train_test_split(X, y, test_size=0.2)` séparer le jeu de données en apprentissage et en test.

## Ajuster et prédire

* `model.fit(X_train, y_train)` ajuster le modèle.
* `model.predict(X_test)` prédire.
* `model.score(X, Y)`

## Métriques

`from sklearn.metric`

* `mean_squared_error(y_test, y_pred)` erreur quadratique moyenne (MSE).
* `r2_score(y_test, y_pred)` coefficient de corrélation.

## Exporter ou charger un modèle

`from joblib import dump`

* `dump(modele, 'modele.joblib')` enregistrer le modèle.
* `modele = load('modele.joblib')` charger le modèle.