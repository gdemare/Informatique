```
PROC PRINCOMP OUTSTAT=stat <option>;
	VAR variable1--variable2;
	ID libelle;
	<WEIGHT poids;>
RUN;
```
Info : par défaut ACP normé.

Options :

* `N = nbre` nombre d'axes principales à afficher.
* `COV` afficher la matrice de covariance. L'ACP effectuait ne sera pas normé.
* `PLOTS <(NCOMP=nb)> = ALL` Afficher les graphiques en limitant le nbbre d'axe avec NCOMP (nécessite `ODS GRAPHICS ON/OFF;`).

## Interprétation

* Eigenvalues of the Covariance Matrix
