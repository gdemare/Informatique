## Calculer la matrice des distances.

```
distance = dist(data, method = "euclidean")
```
Tableau des options des distances :

| Distance | R |
|---|---|
| eculidienne | `euclidean` |

## CAH

```
cah = hclust(distance, method="ward.D2")
```

Tableau des méthodes :

| Méthode | R |
|---|---|
| Ward | `ward.D2` |

## Afficher le dendrogramme

```
fviz_dend(cah, k=3)
```
Options :
* `k = nbre` nombre de classes.
