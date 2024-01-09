## Méthode 1 : ACP

`acp_res <- prcomp(data)`

* `scale = TRUE` centré réduit. 

### Info sur les axes

`summary(acp_res)`

* `$sdev` écart type pour chaque axe. Les valeurs propres sont calculées a partir de la variance.
* `$importance` avec :

Ligne    | Description
---------|----
1        | Ecart type.
2        | % de variance par axe.
3        | % de variance cumulée.

### Représentations graphiques

`library(ggfortify)`

* `autoplot(acp_res)` afficher les variables et les individus.

    * `label = T` afficher le nom des individus.
    * `dt_acp, colour = 'col_group'` afficher des groupes d'individus (il suffit d'ajouter le jeu de données avec l'acp avec toutes les variables).
    * `frame = TRUE` ajouter des clusters (`frame.type = 'norm'` pour avoir des ellipses).
    * `loadings = TRUE, loadings.colour = 'blue', loadings.label = TRUE, loadings.label.size = 3` afficher les variables.

## Méthode 2 : ACP

`library(FactoMineR)` nécessite d'installer `chron`.

!!! note
    Fonctionne avec les deux méthodes.

`acp_res <- PCA(pop, graph = F)`

Paramètres :

* `scale.unit = TRUE` centré et réduire.
* `ncp = 5` nombre d'axes à garder.
* `indsup =` ajouter des individus sur la représentation.s

Retour :

* `$eig` valeur propres
* `$var` # variables
* `$ind` # individus

### Représentations graphiques

`plot(acp_res, choix = "var")` afficher  le résultat `"var"` pour les variables ou `"ind"` pour les individus.

### Regroupement sur les composantes principales

`res_hcpc <- HCPC(acp_res, graph = FALSE)`

Paramètres :

* `nb.clust = 3` nombre de groupes à garder.

Retour :

`$data.clust` data orignal avec une colonne groupe supplémentaire.
`$desc.var` variables qui décrivent les groupes.
`$desc.ind` individus les plus représentatifs.
`$desc.axes` axes qui décrivent le mieux chaque groupe.

#### Graphiques 

* `fviz_dend(res_hcpc)` afficher le dendrogramme.
* `fviz_cluster(res_hcpc)` afficher les groupes sur les axes.

## Représentations graphiques

`library(factoextra)`

### Valeurs propres

`fviz_eig(reacp)` afficher le diagramme en barre des valeurs propres.

### Graphiques

Filtrer les données et choisir les axes à représenter :

* `axes = c(1,2)` choix des axes.
* `select.ind = list(cos2 = 0.6)/select.var` selectionnner les individus/variables représentés.

#### Individus

```
fviz_pca_ind(resacp,
             #pointsize = 'cos2', col.ind = "cos2", gradient.cols = c("#00AFBB", "#E7B800", "#FC4E07"), # afficher la qualité de représentation des individus (cos2)
             repel = TRUE  , label = "none", # les labels des individus
             habillage=  condition, addEllipses=TRUE, ellipse.type = "confidence" # afficher les élipses
             )
```

#### Variables

```
fviz_pca_var(res.pca,
             col.var = "contrib", gradient.cols = c("#00AFBB", "#E7B800", "#FC4E07"),
             repel = TRUE
             )
```

#### Individus et variables

```
fviz_pca_biplot(res.pca, repel = TRUE, col.var = "#2E9FDF", col.ind = "#696969")
```