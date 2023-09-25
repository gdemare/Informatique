## Loi normale

`import scipy.stats`

`norm(valeur)` renvoie la valeur de la loi normale. Paramètres : 
    * `loc=0` moyenne.
    * `scale=1` écart type.
* `pdf(x)` renvoie la probabilité pour un x.
* `sf(densité)` fonction de survie renvoie la valeur de la loi dont l'intégrale est égale à la densité (`isf` fonction inverse).
* `cdf(x)` renvoie la densité en fonction de la valeur. L'aire de la courbe en dessous de la valeur.
