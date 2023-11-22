```
library(randomForest)
```

## Construire le modèle

```
rf = randomForest(cible ~ ., data=train)
```
!!! note
	La variable à prédir doit être un facteur `as.factor()`

Option :

 * `na.action = na.roughfix/na.omit` remplace les valeurs manquantes par la médiane.
 * `ytest =v ar_explique , xtest = vars_explicatives` prédire les valeurs.
 * `nodesize = 5` nombre de noeuds minimum.
 * `importance = T` évaluer l'importance des variables.
 * `proximity = TRUE`
 * `ntree = 500` nombre d'arbres à construire. 
 * `mtry = 3` nombre de variables candidates.
 * `replace = T`
 * `keep.forest = T` garder la forêt en mémoire.

## Taux d'erreur

```
plot(rf$err.rate[1:rf$ntree,1],type='l', xlab="nombre d'itérations",ylab='erreur')
lines(rf$test$err.rate[1:rf$ntree,1],type='l',lwd=2,col='red')
```

## Importances des variables

```
rf.imp <- importance(rf,type=1)[order(importance(rf,type=1), decreasing=TRUE),]
rf.imp
varImpPlot(rf)
```
