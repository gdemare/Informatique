## Package rpart

`library(rpart)`, `library(rpart.plot)`.

Construire l'arbre

``` R
cart = rpart( data = data, 
              Cible~.,
              parms = list(split = "gini"),
              cp = 0)
```

Option :

* `method = class/anova` variable à expliquer de type qualitative/quantitative.
* `parms = list(split = "gini")` critère à utiliser.
* `control = rpart.control()` pour controler les paramètres de l'arbre. Paramètres :

	* `minsplit = 5` nombre minimum d'observations dans chaque noeud.
	* `minbucket = 1` l'effectif minimal dans chaque noeud terminal.
 	* `maxdepth = 30` hauteur (profondeur) maximale de l'arbre.
	* `cp = 0` paramètre de pénalisation pour la complexité.
	* `mincriterion = 0.3` 1-p-valeur à partir de laquelle on souhaite arrêter.

`summary(cart)` information sur l'arbre.

Retourne :

* `minsplit = nbre` nombre de branches minimum.
* `minbucket = 1/3*minsplit` par défaut.
* `control = rpart.control(minsplit = 5,cp = 0)` sans contrainte sur la qualité et avec au moins 5 obsevations par feuille.

for stumps : `rpart.control(maxdepth = 1,cp = -1, minsplit = 0)`

## Information sur l'arbre

`summary(cart)` 

l’erreur xerror calculée par validation croisée (R constitut 10 échantillons).

* `xerror` erreur de la validation croisée.

## Qualité de l'arbre 

``` R
printcp(cart)
plotcp(cart)
```

Indicateur      | Définition
----------------|---
Root node error | erreur à la racine. 
CP              | coefficient de complexité.
nsplit          | nombre de branches
rel error       | taux erreur de jeu d'apprentissage
xerror          | taux erreur de la validation croisée (R constitut 10 échantillons)
xstd            | écart type des erreurs 

`prune(cart, cp = 0.0155441)` élaguer l'arbre.

### Graphiques

`library(rpart.plot)`

``` R
prunedcart9f = prune(cart, cp = 0.0155441)
```

* `rpart.plot(abre_complet)` afficher l'arbre (ou sinon `prp(abre_complet)`). Paramètres:
  
	* `type = 0` retirer les informations sur les noeuds.

* Affiche :
  
 	1. La classe prédite.
  	2. La probabilité d'appartenir à la classe.
  	3. Le pourcentage d'observations dans la noeud. 

* `visTree(abre_complet)` afficher l'arbre avec le nombre de données dans chaque noeud (`library(visNetwork)`).

### Qualité

* `printcp(cart)` afficher la complexité de l'arbre.
* `plotcp(cart)` afficher l'erreur relative en foonction de la complexité.

## Package party

`library(party)`

`ctree(y_reel~., dtf_train, control = ctree_control())`

* `ctree_control()` paramètres de l'arbre.

	* `minsplit = 2` effectif minimal pour séparer un noeud.
	* `minbucket = 1` effectif minimal dans chaque noeud terminal.
	* `maxdepth = 30` hauteur (profondeur) maximale de l'arbre
	* `mincriterion = 0.3` c1-p-valeur à partir de laquelle on souhaite cesser la croissance.
 
 `plot(arbre_ctree)` afficher l'arbre.
 
``` R
prp(cart, type = 2, extra = 1, split.box.col = "lightgray")
rpart.plot(cart)
```
