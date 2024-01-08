`fviz_nbclust(X_stand, FUNcluster = kmeans, method = "wss")`

Déterminer le nombre de classes optimal.
La fonction calcul la matrice des distances (par défaut `euclidean`).
Paramètres :

* `method = ` :
  
	* `silhouette` variance inter classe (for average silhouette width).
 	* `wss` variance intra groupe (total within sum of square).
  	* `gap_stat`.

* `FUNcluster = ` :

  	* `hcut` CAH.
  	* `kmeans` moyenne mobiles.
  	* lara, fanny, hcut
	
