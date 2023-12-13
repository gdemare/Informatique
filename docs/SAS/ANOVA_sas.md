```
PROC ANOVA;
  CLASS variable ;
  MODEL variable_explique = variable_qualitative_explciative ;
  <paramètre>
 RUN;
```

var1 | var2 interactions entre les variables.

Paramètres :

* `MEANS variable_qualitative_explciative </ option>;` 
 
Options :

* `LSD` test de Fisher, comparaison des moyennes de chaque groupe.
* `CLDIFF` intervalle de confiance.
* `TUCKEY` test de Tuckey, comparaison des moyennes de chaque groupe.
* `DUNCAN` Waller-Duncan -ratio test
* `WALLER` means of the Strain levels with Duncan’s multiple range test
  
* `TEST H=var1 E=var2*var1`

## Interprétation

* **Class Level Information** synthèse des variables explicatives et des observations.


