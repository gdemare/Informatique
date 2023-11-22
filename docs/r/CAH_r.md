La classification ascendante hiéarchique se fait en deux étapes :

1. Calcul de la matrice des distances.
2. Application de l'algorithme de classification.

## CAH

```
cah = hclust(distance, method="ward.D2")
```

Tableau des méthodes :

Méthode     | R
------------|---
Ward        | `ward.D2`

`$height` valeur du criètre d'agglomération.

## Afficher le dendrogramme

* `plot(cah)`
* `fviz_dend(cah)` afficher avec Options :

    * `k = nbre` nombre de classes à conserver.
