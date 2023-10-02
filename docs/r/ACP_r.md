```
resacp = prcomp(data, scale = TRUE) # scale centre et réduit
## résumé des axes
acpInfo = summary(resacp)

## valeurs propres
acpInfo$sdev #ecart type pour chaque axe. Les valeurs propres sont calculées a partir de la variance.
acpInfo$importance # % de variance cumulée
```

## Représentation graphique

`autoplot(res_acp, loadings = TRUE, loadings.colour = 'blue',loadings.label = TRUE, loadings.label.size = 3)` afficher les variables et les individus.


----------------------------

L'installation des packages n'a pas fonctionné Ubunut 10-2023

### Représenter l'ACP

`fviz_eig(reacp)` afficher le diagramme en barre des valeurs propres.

Filtrer les données et choisir les axes à représenter :
* `axes = c(1,2)` choix des axes.
* `select.ind = list(cos2 = 0.6)/select.var` selectionnner les individus/variables représentés.

Afficher les individus.
```
fviz_pca_ind(resacp,
             #pointsize = 'cos2', col.ind = "cos2", gradient.cols = c("#00AFBB", "#E7B800", "#FC4E07"), # afficher la qualité de représentation des individus (cos2)
             repel = TRUE  , label = "none", # les labels des individus
             habillage=  condition, addEllipses=TRUE, ellipse.type = "confidence" # afficher les élipses
             )
```
Afficher les variables
```
fviz_pca_var(res.pca,
             col.var = "contrib", gradient.cols = c("#00AFBB", "#E7B800", "#FC4E07"),
             repel = TRUE
             )
```
Afficher les individus et les variables ensemble
```
fviz_pca_biplot(res.pca, repel = TRUE, col.var = "#2E9FDF", col.ind = "#696969")
```

#### Old

Packages : FactoMineR

```
res.acp = PCA(pop, graph = F)
res.acp$eig # valeur propres

res.acp$var # variables
res.acp$ind # individus
```

