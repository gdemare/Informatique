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

Méthode                       | Type
------------------------------|---
Arbre de décision             | `\`
Régression logistique         | `type = "response"`
Forêt aléatoire               | `type = "prob")[,2]`
Boosting                      | `type = "prob")[,2]`
Classificateur naïve baysien  | `)$posterior[,2]`
