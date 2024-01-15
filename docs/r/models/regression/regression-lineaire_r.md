`mod <- lm(Y~., data = dt)` créer une régression linéaire.

retourne : 

* `$coefficients` les coefficients pour chaque variable.


`summary(mod)` résumé détaillé du modèle.

Std. Error (Std. Error) :  écart type de l'estimation du coefficient
Test de significativité : 
R-squared : proportion de la variance expliquée par le modèle.

enlever les variables corréler (même si on utilise les méthodes de sélection des variables) car le modèle ne converge pas. Un variable qui ne converge pas signifie qu'il n'arrive pas à déterminer les paramètres du modèle.

`plot(mod1)` affiche quatre graphiques : 

*
*
*
*

`anova(fit)` pour estimer l'effet de la variance sur celle à prédire.

Test le coefficient est il égale à 0 ?.
résidu erreur entre la valeur réel et la prédiction.

$R^2$ coefficient de détermination. (inversement l'erreur explique peu la variance).
Ajuster calculer sur le nombre d'observation. (Moyenne)

validité du modèle

Résidus : 

* homoscédasticité
* résidus centré,
* identiquement distribué (indépendance), distribution des résudus et errer en fonction des valeurs prédites.
