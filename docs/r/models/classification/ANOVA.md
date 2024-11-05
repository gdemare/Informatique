## Anova à 1 facteurs

```
anova = aov(var ~ group, data = donnees )# analysis of variance
summary(anova)

# test de tukey pour connaitre les différences de moyennes entre les groupes
TukeyHSD(anova)`
```

Résultats : 
- **DF** : Les degrés de liberté pour chaque source de variation.
- **Sum Sq** : La somme des carrés (variance expliquée par chaque source).
- **Mean Sq** : La moyenne des carrés.
- **F value** : La statistique de test F pour l’ANOVA.
- **Pr(>F)** : La p-valeur associée. Si elle est inférieure au seuil (par exemple, 0,05), cela indique une différence significative entre les groupes.
### Comparaison deux à deux des groupes

`TukeyHSD(anova)` comparaison des moyennes entre les groupes avec un test de Tukey pour savoir deux à deux quels sont les groupes différents.

`leveneTest(value ~ group, data = data)` test de Levene homogénéité des variances.

Installer le dépendance du package pour pouvoir l'installer :
`devtools::install_github("matherion/userfriendlyscience", dependencies=TRUE)`
`library(userfriendlyscience)`


* `games.howell(group, value)` test de Games Howell comparaison des moyennes pour des échantillons apparérié
*```
```
oneway(InsectSprays$spray, y = InsectSprays$count, posthoc = 'games-howell')
```

!!! note
		Lorsque les hypothèses d'application de l'ANOVA sont vérifiées, les résultats sont quasiment les mêmes.