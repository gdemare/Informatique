``` 
PROC LOGISTIC <option>;
  MODEL var_explique <(EVENT='modalite' )> = var_quantitative / <option MODELE>;
RUN;
```
## Paramètre
* `BY variable;` séparer les analyses en fonction d’une variable.
* `CLASS variables qualitative / <option>;` déclarer les variables qualitatives.
  * `MISSING` les valeurs manquantes sont traitées comme une modalité.
* `WEIGHT variable;` pondérer les observations.

## Option MODELE

* `CORRB` afficher la matrice des corrélations.
* `CTABLE PPROB=proba` afficher la matrice de confusion en fonction du seuil.
* `LINK=fonction` fonction de liaison (`logit`).
* `SELECTION=backward/stepwise/forward` algorithme de selection des variables explciatives.

## Option

* `INMODEL=data` charger un modèle existant (créer à partir de OUTMODEL).
* `PLOTS = ALL`  afficher les graphiques (nécessite ODS GRAPHICS).
* `OUTMODEL=data`  exporter le modèle.
* `OUTEST=data` jeu de test.
