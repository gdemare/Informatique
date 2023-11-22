## Effectuer les prédictions

```
pred = predict(object = model, newdata = test )
```
Type :
	
* `response` retourner la probabilité d'appartenance à la classe.

## Évaluer le modèle 

```
pred.class = predict(object = model, newdata = test )
pred.proba = predict(object = model, newdata = test, type = "response" )
eval = appren %>% bind_cols(pred.class[,2], pred.proba[,2])
```

### Matrice de confusion

```
confusion = table(eval$cible, eval$pred.class)
confusion.proba = prop.table( table(eval$cible, eval$pred.class) )
```

### Courbe de Receiving Operator Characteristic (ROC)

Package : verification.

```
roc.plot(classe , proba)
```

#### Area Under the Curve (AUC)

```
auc = performance(pred,"auc")@y.values[[1]]; auc
```

### Courbe de Lift

Package : BCA

```
lift.chart( c("CCS.glm", "CCS.rpart"), data=CCSVal, targLevel="1", 
            trueResp=0.01,
            type="cumulative",
            sub="Validation")
```

Type : 

* `cumulative`
* `incremental` 
