`afc_res = CA(table(var1,var2), graph = F)`

Retours : 

* `res.afc$eig` valeurs propres.
* `$row` profil lignes.
* `$col` profil colonnes.

## Représentations graphiques

`library(factoextra)`

* `fviz_eig(res.afc)` diagramme des valeurs propres.
* `fviz_ca(res.afc, repel = T)` représentation de l'afc.