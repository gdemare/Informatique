Nécessite un tableau disjonctif en entré (`PROC TRANSREG`).

```
PROC CORRESP option;
	VAR variables ;
	<ID identifiant;>
	<SUPPLEMENTARY var_illustrative;>
RUN;
```

* `NVARS=nbre` nombre de variables avant le tableau de Burt.
* `ODS GRAPHICS ON/OFF;`

Option :

* `MCA` ACM ur tableau de Burt.
* `DIMENS=nbre` nombre d'axes à conserver.
*  `NVARS=nbre`
* `ALL` afficher tout.
* `PLOTS=ALL`afficher les graphiques.
* `OUTC = table` exporter les variables.
