## Calcul des paramètres pharmacocinétiques

`library(PKNCA)`

https://billdenney.github.io/pknca/news/index.html

!!! warning 
    Ne fonctionne pas avec `units`.

!!! note
    La bibliothèque a été pensée pour intégrer de nouveaux indicateurs qui n'auraient pas été pensé par les auteurs.

Données minimum : concentration, dose, and time.

* zeros (0) below the limit of quantification.
* NA valeur manquante.
* `superposition(conc_obj, tau=24, check.blq=FALSE)` pour les études de multidosage. 

1. Formater les données pour les calculs :
   
    * `conc_obj <- PKNCAconc(dt, Conc~Time|Subject)` pour les fécès et l'urine. Pour les fèces et les urines `duration=` et `volume=` avec la colonne déclarer `"colonne"`.
  
       * `time.nominal =` afficher les réels de prélévements (n'est pas utilisé pour les calculs).
       * `intervals = ` ?????
         
    * `dose_obj <- PKNCAdose(dt, Dose~Time|Subject)` déclarer les doses et leurs temps d'injection.
        
        * `route = ` précisier la route.
            
            * `"intravascular"` injection. Si l'injection est lente (infusion), il faut ajouter l'option `rate=` ou `duration=`.
            * `"extravascular"` ingestion. 

!!! note
    La formule `treatment+subject` possibilité d'utiliser plusieurs colonnes pour créer un id sujet et `/Group` pour déclarer des groupes.

    
2. `PKNCAdata(conc_obj, dose_obj)` fusionner les tables doses et concentration. Le résultat est un tableau avec tous les paramètres cinétiques pour chaque individu.

3. `results_obj <- pk.nca(data_obj)` calculer les indicateurs.

Résultats : 

* `summary(results_obj)` résumer le résultat.

Personnaliser les indicateurs :

* `PKNCA.options()` configuration.
* Ajouter des indicateurs :

```R 
PKNCA.set.summary(
  name=nom,
  description = "median and 5th to 95th percentile",
  point=fct1,
  spread=fct2,
  rounding=list(signif=3)
)
```

### Les unités

`library(units)`

!!! warning
    Quand il n'y a pas d'unité, mettre "".

* `valid_udunits()` lister les unités valides.
* `valid_udunits_prefixes()` lister les ordres de grandeurs.
* `units(val_1) <- "km/s"` ou `set_units(x, unit[1], mode = "standard")` attribuer une unité ET convertir dans une autre unité.
* `deparse_unit(valeur)` récupérer l'unité.
* `mixed_units(df$valeurs, df$unite)` créer une vecteur avec des unités différentes (Attention, elles s'affichent pas dans les sorties des dataframes).
* `drop_units(x)` supprimer l'unité.
* `units_options(negative_power = TRUE)` modifier l'affichage des unités.
* `attributes(dt$Value[[1]])` vérifier la valeur possède une unité.
 
!!! note
    Si deux jeux de données avec des unités différentes, elles sont converties durant la fusion.

!!! warning
    Le `.` doit être transfomé en `*`.

### Rempsyc

Package avec de nombreuses fonctions pour 

!!! note 
    Il est normalement utiliser pour la Convenience functions for psychology.

https://rempsyc.remi-theriault.com/

### ADME
Variable utilisé pour calculer les indicateurs :

* concentration de la substance
* poids de l'individu
* temps

Grands types d'indicateurs calculés :

* clairance : décrit la capacité de l'organisme à éliminer une substance médicamenteuse du système biologique.
Cela correspond au volume d'un fluide de l'organisme (souvent plasma) purifié éliminé par unité de temps. C'est
rapport entre la quantité d'une substance éliminée par unité de temps et la concentration dans un fluide de l'organisme.


!!! note 
    Il existe principalement deux clairances : hépatique et reinnale.

liste des indicateurs calculés dans PKexpress :

La concentration

* $C_t$ concentration à un temps donné.
* $CL = \frac{Dose}{AUC}$ clairance.

Le temps :

* $t_{1/2}$ temps de demi vie.
* $t_{last}$ temps de la mesure de $C_{last}$.
* $AUC_{t}$ area under the curve. Aire sous la courbe entre $t_{0}$ et $t_{last}$.
* temps de demi vie

Concentration normalisée :



send_bio_analyse <- function(file){

  print()
}

send_bio_analyse('Kluster_Import_PB-21-SNC055-018-DDBA_2021-07-02.xlsx')
  
"high value of variability" noté CV%

