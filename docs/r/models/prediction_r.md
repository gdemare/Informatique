## Préparer les données 

`library(rsample)`

```
split <- initial_split(dataset, 0.8)
train_dataset <- training(split)
test_dataset <- testing(split)
```

## Effectuer les prédictions

`pred <- predict(object = model, newdata = test)`

Type :
	
* `response` retourner la probabilité d'appartenance à la classe.

## Évaluer le modèle 

```
pred.class = predict(object = model, newdata = test )
pred.proba = predict(object = model, newdata = test, type = "response")
eval = appren %>% bind_cols(pred.class[,2], pred.proba[,2])
```

### Matrice de confusion

* `prop.table(table(eval$cible, eval$pred.class))` matrice de confusion en fréquence.
* `roc.plot(classe , proba)` courbe Receiving Operator Characteristic (ROC)`library(verification)`.
* `auc = performance(pred,"auc")@y.values[[1]]` Area Under the Curve (AUC).

### Courbe de Lift

`library(BCA)`

```
lift.chart( c("CCS.glm", "CCS.rpart"), data = CCSVal, targLevel = "1", 
            trueResp = 0.01,
            type = "cumulative",
            sub = "Validation")
```

* `type =`: 

    * `cumulative`
    * `incremental` 