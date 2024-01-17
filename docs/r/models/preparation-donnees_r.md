## Préparer les données 

`library(rsample)`

```
split <- initial_split(dataset, 0.8)
train_dataset <- training(split)
test_dataset <- testing(split)
```

## Collération et colinéarité

`library(caret)`

* `findCorrelation()`  renvoie les indices des colonnes avec une correlation élevée càd l'indice des variables à supprimer.
* `findLinearCombos()` renvoie les indices des colonnes avec impliquée dans une colinéarité càd l'indice des variables à supprimer.