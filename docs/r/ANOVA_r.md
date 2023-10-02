## Anova à 1 facteurs

```
anova = aov(var ~ group, data = donnees )# analysis of variance
summary(anova)
```

### Comparaison deux à deux des groupes

`TukeyHSD(anova)` comparaison des moyennes entre les groupes avec un test de Tukey.