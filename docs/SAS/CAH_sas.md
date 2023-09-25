```
PROC CLUSTER <option>;
  ID variableID;
RUN;
```

La selection du nombre de classe se fait avec la `PROC TREE`

`ODS GRAPHICS ON/OFF;` afficher le graphique/

# Options

* `CCC` afficher le Critére de Classification Cubique.
* `OUTTREE=table` exporter les résultats.
* `METHOD=méthode` 
  * `AVERAGE`
  * `WARD` méthode Ward.
* `PRINT=nbre` nombre de classe à afficher.

 Semi-partial R-squared : mesure la perte d'inertie intraclasse.
