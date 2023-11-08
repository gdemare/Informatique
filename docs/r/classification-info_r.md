#### V-cramer

```
cramer  <- matrix(NA,ncol(credit2),3)
for (i in (1:ncol(credit2)))
{     cramer[i,1] <- names(credit2[i])
cramer[i,2] <- sqrt(chisq.test(table(credit2[,i],credit$Cible))$statistic/
                      (length(credit2[,i])))
cramer[i,3] <- chisq.test(table(credit2[,i],credit$Cible))$p.value
}
colnames(cramer) <- c("variable","V de Cramer","p-value chi2")

# affichage des variables par V de Cramer décroissants
vcramer <- cramer[order(cramer[,2], decreasing=T),]
vcramer

par(mar = c(8, 4, 4, 0))
barplot(as.numeric(vcramer[,2]),col=gray(0:nrow(vcramer)/nrow(vcramer)),
        names.arg=vcramer[,1], ylab='V de Cramer', ylim=c(0,0.35),cex.names = 0.8, las=3)
abline(h=0.1, lty=2)
abline(h=0.2, lty=2)
```

* > 0.2 :
* > 0.1 :

### Réaliser des prédictions

```
pred = predict( object = modele, newdata = test, <type => )
```

Option type en fonction du type de modèle

| Méthode | <Type> |
|---|---|
| Abre de décision | `\` |
| Régression logistique | `type="response"` |
| Forêt aléatoire | `type= "prob")[,2]` |
| boosting | type ='prob' )[,2] |
| classificateur naive baysien| `)$posterior[,2]` |
 
## Comparer la performance de modèles

### Courbe de (Receiver Operating Characteristic)

```
predtion = prediction(pred, test$cible,label.ordering=c(0,1))
roc = performance(predtion, "tpr", "fpr")
```

Affichage graphique 
``` 
library(ggplot2)

fonc = function(x){x}
roc = ggplot() + stat_function(fun = fonc, data = data.frame(x = c(0, 1))) +
  xlab("sensibilité") + ylab("Taux de vrais positifs") + theme_minimal()

roc +
  geom_line( aes(x= roc.reg@x.values[[1]], y=roc.reg@y.values[[1]]), color="blue" )
``` 

#### Area Under the Curve (AUC)

```
library(ROCR)
performance(predtion,"auc")@y.values[[1]]
```

### Courbe de Lift (courbe de gain)

```
library(dplyr)

nb.cible = length(which(test$cibke==1))
ref = c(rep(1,nb.cible), rep(0,length(test$FlagASV)-nb.cible))

lift.rf = data.frame( cible = test$FlagASV, proba = pred.rf)
lift.rf = lift.rf %>% arrange(desc(proba)) %>%
  mutate( cumden = cumsum(cible)/sum(cible)*100,
          perpop = (seq(n())/n()*100),
          parfait = cumsum(ref)/sum(ref)*100 )
```

```
library(ggplot2)

fonc1 = function(x){
    classe = nb.cible/nrow(test)*100
    ifelse(x<classe, (x/classe)*100, 100)
  }
fonc = function(x){x}
lift = ggplot() + theme_minimal() + stat_function( fun = fonc1, data= data.frame(x = c(0, 100))) +
  stat_function(fun = fonc) + xlab("% population") + ylab("% cible")
lift + geom_line( aes(x= lift$perpop, y=lift$cumden), colour = "blue")
```

## Descente de gradient

La descente de gradient permet de trouver le minimum d'une fonction 

* `optim(par = c(-5,5), fn = fonction, method="BFGS")` minimiser une fonction. Méthode:

	* `BFGS`
 	* 

Sortie :

  * `$par` valeurs qui donnent le minimum.
  * `$value` valeurs obtenues.
