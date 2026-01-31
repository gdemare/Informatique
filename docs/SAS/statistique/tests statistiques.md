## Tests non paramétriques

```
PROC NPAR1WAY <option>;
VAR var_quanti;
CLASS var_quali;
RUN;
```

### Paramètres

* `BY`
* `WHERE condition` filtrer le jeu de données avant les tests.
* `D` afficher les graphiques (nécessite ODS GRAPHICS).
* `KS` Kolmogorov-Smirnov.

### Options :

* `PLOTS` afficher les graphiques associés aux tests.
