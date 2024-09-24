```
from sklearn.cluster import AgglomerativeClustering

cah = AgglomerativeClustering(n_clusters = None, distance_threshold=4)
y_pred = cah.fit_predict(X])
```

Il faut préciser soit le nbre de clusters soit la distance minimale.
paramètres :
* `linkage="war"` type de distance entre deux clusters.


## Dendrogramme

`from scipy.cluster.hierarchy`

```
z = linkage(acp.iloc[:, :-2], method="ward")
dendrogram(Z, truncate_mode="lastp", labels= acp.index, orientation='left')
pl.xscale('symlog')
```
