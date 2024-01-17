## Package rpart

`library(rpart)`, `library(rpart.plot)`.

`cart = rpart(data = data, Cible ~ ., control = rpart.control())` construire l'arbre.

Option :

* `methode = class/anova` variable à expliquer de type qualitative/quantitative.
* `parms = list(split = "gini")` critère à utiliser.
* `control = rpart.control()` pour controler les paramètres de l'arbre. Paramètres :

	* `minsplit = 5` nombre minimum d'obseration dans chaque noeud.
	* `minbucket = 1` l'effectif minimal dans chaque noeud terminal.
 	* `maxdepth = 30` hauteur (profondeur) maximale de l'arbre.
	* `cp = 0` paramètre de pénalisation pour la complexité.
	* `mincriterion = 0.3` 1-p-valeur à partir de laquelle on souhaite arrêter.

`summary(cart)` information sur l'arbre.

Retourne :

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
