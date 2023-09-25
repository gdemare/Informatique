## Tableau statistique élémentaire

```
PROC TABULATE <option>;
  CLASS variablesDescriptif ;
  VAR variableAnalyse ;
  TABLE ligne,colonnes*calculs ;
  <FORMAT variable format>
RUN;
```

Option :
* `MISSING` créer une modalité "valeur manquante".
* `var='libellé'` changer le libellé dans le tableau.
* `FORMAT variable format.` formater une variable.

Principales statistiques disponibles dans la PROC TABULATE.

| Fonction | Définition |
|---|---|
| `N` | effectif |
| `<zone>PCTN` | fréquence d'obsevation total par ligne (ROW), par colonne(COL) |
| `NMISS` | nombre de valeurs manquantes |
| `<zone>PCTSUM`| 
| `MEAN` | moyenne |
| `SUM` | somme |
| `MIN/MAX` | minimun et maximum |
| `MEDIAN` | médiane |
| `Qa` | quartiles a. |
| `Px` | centile à x% (ex : P15 -¿ 15%) |
| `VAR` | variance |
| `STD` | écart type |
| `LCLM/UCLM` | intervalle de confiance (borne inf et sup) |

## Tableau indicateurs (moyenne, médiane, max, min, variance)

```
PROC MEANS <options>;
  VAR variable;
  CLASS modalite;
RUN;
```

Options :
`MAXDEC=n` nombre de décimale

## Tableau récapitulatif

```
PROC SUMMARY
RUN;
```

## Tableau fréquences

```
PROC FREQ <option>;
  TABLE col / <option> ;
RUN;
```

Options:
* `NOCUM` supprimer les fréquences cumulatives.
* `MISSING` afficher le nbre de valeurs manquantes.
* `CHISQ` test du khi 2.

## Description pour chaque variable

```
PROC UNIVARIATE;
  VAR variabe;
  <HISTOGRAM>;
RUN;
```
* `HISTOGRAM` afficher l'histogramme.

## Corrélation

```
PROC CORR <PEARSON/SPEARMAN> ;
  VAR var1 var2 var;
RUN;
```
Option :

* `NOPROB` masquer la p-value.
* `NOCORR` masquer le coefficient de corrélation.

## Afficher

```
PROC PRINT <option>;
RUN;
```

Option :
* `NOOBS LABEL` afficher le label des individus à la place du numéro d'observation (`NOOBS`).
* `OUTOBS=nbre` nombre d’individus en sortie.
