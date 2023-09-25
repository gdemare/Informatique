Package : rpart, rpart.plot, ipred.
```
library(rpart)
library(rpart.plot)
library(ipred)
```

Construire l'arbre
```
cart = rpart( data = data, 
              Cible ~ . ,
              parms=list(split="gini"),
              cp=0)
```
Option : 
* `methode = class/anova` variable à expliquer de type qualitative/quantitative.
* `minsplit = nbre` nombre de branches minimum.
* `minbucket = 1/3*minsplit` par défaut.
* `control = rpart.control(minsplit=5,cp=0)` sans contrainte sur la qualité et avec au moins 5 obsevations par feuille.


for stumps : rpart.control(maxdepth=1,cp=-1,minsplit=0)
Information sur l'arbre
```
summary(cart)
``` 
l’erreur xerror calculée par validation croisée (R constitut 10 échantillions).
xerror erreur de la validation croisée.
error erreur de la 

# Qualité de l'arbre 

```
printcp(cart)
plotcp(cart)
```

|Indicateur|Définition|
|---|---|
| Root node error	| erreur à la racine. | 
| CP | coefficient de complexité. |	
| nsplit | nombre de branches |
| rel error | taux erreur de jeu d'apprentissage |
| xerror | taux erreur de la validation croisée (R constitut 10 échantillions) |
| xstd | écart type des erreurs |

feuille qui minimise l'erreur et le coefficent 

# Élaguer l'arbre

```
prunedcart9f = prune(cart,cp=0.0155441)
```

# Afficher l'arbre de décision
```
prp(cart,type=2,extra=1,split.box.col="lightgray")
rpart.plot(cart)
 ```
