```
PROC FASTCLUS <option>;
  ID variable ;
  VAR variablesQuanti;
RUN;
```

## Paramètres

* `WEIGHT variable ;`
* `BY variables ;`

## Options

* `MAXC=nbre` nombre de classes.
* `MAXITER=10` nombre d'iteration maximum.
* `OUT=table` exporter le résultat dans une table.
* `OUTSEED=table` exporter les infos sur les classes.
* `DELETE=nbre`supprimer les classes d'un nombre inférieur d'individus.
