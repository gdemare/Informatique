## Préparer les données 

`library(rsample)`

```
split <- initial_split(dataset, 0.8)
dt_train <- training(split)
dt_test <- testing(split)
```
## Prédire

`pred <- predict(object = model, newdata = test)` effectuer les prédictions. Paramètres :
	
* `type =` renvoyer la probabilité :
* `response` retourner la probabilité d'appartenance à la classe (pour la classification)

| Méthode                      | Type                 |
| ---------------------------- | -------------------- |
| Arbre de décision            | `\`                  |
| Régression logistique        | `type = "response"`  |
| Forêt aléatoire              | `type = "prob")[,2]` |
| Boosting                     | `type = "prob")[,2]` |
| Classificateur naïve baysien | `)$posterior[,2]`    |
## Descente de gradient

La descente de gradient permet de trouver le minimum d'une fonction 

```
fct_cout <- function(x_obs, y_obs, params){
  a <- params[1]
  b <- params[2]
  return(sum( (fct_mod_lineaire(params, x_obs) - y_obs)**2 ))
}

optim(par = c(a = 3, b = 12), fn = fct_cout, method = "CG", x = x, y = yobs)
```

* `optim(par = c(-5,5), fn = fonction, method = "BFGS")` minimiser une fonction. 

R				| Méthode
----------------|----------
`Nelder-Mead`	|
`CG`			| Gradient conjugué.
`BFGS`			| Méthode de Newton. 
`L-BFGS-B`		| BFGS avec des contraintes sur les valeurs à trouver.
`SANN`			| Recuit simulé.
`Brent`			|
Sortie :
### Regression 

* `postResample(pred, reel)` renvoie le $R^2$.
### Classification 

#### Matrice de confusion

* `prop.table(table(eval$cible, eval$pred.class))` matrice de confusion en fréquence (ou `confusionMatrix()` de `library(caret)`).
* `roc.plot(classe , proba)` courbe Receiving Operator Characteristic (ROC) `library(verification)` (ou `roc()` de `library(pROC)`).
* `auc = performance(pred,"auc")@y.values[[1]]` Area Under the Curve (AUC).
#### Courbe de Lift

* `$par` valeurs trouvées des paramètres qui minimise la fonction.
* `$value` valeurs minimums.
* `$convergence` renvoie si l'algorithme a réussi à converger (`0` oui, `1` non le maximum d'itération a été atteint).
* `$counts` renvoie le nombre d'appel à la fonction et à la dérivé.
