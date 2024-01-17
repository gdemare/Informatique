## Préparer les données 

`library(rsample)`

```
split <- initial_split(dataset, 0.8)
dt_train <- training(split)
dt_test <- testing(split)
```

## Collération et colinéarité

`library(caret)`

* `nearZeroVar(mdrrDescr, saveMetrics= TRUE)` afficher les colonnes avec une variance nulle.
* `findCorrelation(data)` afficher les groupes de variables corrélées.
* `findLinearCombos(data)` afficher les combinaisons linéaires.
