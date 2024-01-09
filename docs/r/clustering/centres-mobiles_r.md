```
kmeans_result = kmeans(X, centers = 3)
```

Paramètres :

* `nstart = nbre` répéter n fois le k-means et conserve le groupe. Renvoie le meilleur regroupement.

Sortie :

* `$cluster` classe.
* `$centers`	A matrix of cluster centres.
* `$withinss` The total sum of squares.
* `$tot.withinss` Total within-cluster sum of squares, i.e. sum(withinss).
* `betweenss` the between-cluster sum of squares, i.e. totss-tot.withinss.
* `$size` The number of points in each cluster.
