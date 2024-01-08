La classification ascendante hiéarchique se fait en deux étapes :

1. Calcul de la matrice des distances.
2. Application de l'algorithme de classification.

## CAH

```
cah = hclust(mat_distance, method = "complete")
```

Tableau des méthodes :

Méthode     | R
------------|---
Ward        | `ward.D2`
            | `centroid` 
            | `average` 
            
`$height` valeur du criètre d'agglomération.

## Afficher le dendrogramme

* `plot(cah)` dendrogramme.
* `fviz_dend(cah)` `library(factoextra)` Options :

    * `k = nbre` nombre de classes à conserver.
    * `h = nbre` nombre d'individus par groupe.

### Elaguer l'arbre

`cutree(cah, k = 3)` élaguer l'arbre.
