```
PROC HPSPLIT <option>;
  CLASS variable_quali ;
  MODEL variable_expliquée = variables_explicatives ;
  <paramètre>;
RUN;
```

`ODS GRAPHICS ON/OFF;` afficher les graphiques.

Option :

* `SEED=nbre`
* `MAXBRANCH=nbre`
* `MAXDEPTH=nbre` nombre de niveaux de l'arbre.
* `NODES=`

	* `DETAIL` afficher les régles de arriver à chaque noeud.
	* `SUMMARY` afficher les règles pour obtenir chaque feuille.

Paramètre :

* `OUTPUT OUT=data` exporter l'arbre de décision.
* `ID identifiant` identifier des individus.
* `RULES FILE='fichier.txt'` exporter les régles.
* `PRUNE metrique / valeur;`

	* `ENTROPY` 
	* `GINI` critère de Gini. Valeurs possibles `N<=valeur` nombre de total de feuilles maximun.
