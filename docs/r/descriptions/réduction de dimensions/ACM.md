`library(FactoMineR)`

`acm_res <- MCA(pop.3, graph = F)`

Retour : 

* `$eig` valeurs propres.
* `$var` variables.
* `$ind` individus.

`facto_summarize(acm_res, element = "var", axes = 1:2)` résumé de l'AFC.

## Représentation graphique

`library(factoextra)`

* `fviz_eig(acm_res)` histogramme des valeurs propres
* `fviz_mca(acm_res, repel = TRUE, c(1,2))`