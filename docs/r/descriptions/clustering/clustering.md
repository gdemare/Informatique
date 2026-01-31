## Nombre de groupes optimal

`library(factoextra)`

`fviz_nbclust(X_stand, FUNcluster = kmeans, method = "wss")`

Déterminer le nombre de classes optimal.
La fonction calcul la matrice des distances (par défaut `euclidean`).
Paramètres :

* `method =` liste des méthodes :
  
	* `silhouette` variance inter classe (for average silhouette width).
 	* `wss` variance intra groupe (total within sum of square).
  	* `gap_stat` .

* `FUNcluster =` :

  	* `hcut` CAH.
  	* `kmeans` moyenne mobiles.
  	* `lara, fanny, hcut`.
	
## Comparer des regroupements

* `table(kmeans_3, cah_3)` 
* `adjustedRandIndex(cah_3, kmeans_3)` indicateur de ressemble entre les groupes `library(mclust)`.