## Calcul des paramètres pharmacocinétiques

`library(PKNCA)`

https://billdenney.github.io/pknca/news/index.html

!!! warning 
    Ne fonctionne pas avec `units`.

!!! note
    La bibliothèque a été pensée pour intégrer de nouveaux indicateurs qui n'auraient pas été pensés par les auteurs.

Données minimum : concentration, dose, and time.

### Préparer les données

* `as_sparse_pk(conc, time, subject)` données clairsemées.

#### Valeurs manquantes et BLQ

* `zeros (0)` below the limit of quantification.
* `NA` valeur manquante.
* `superposition(conc_obj, tau=24, check.blq=FALSE)` pour les études de multidosage. 

Remplacer les valeurs :

* `clean.conc.blq()`
* `clean.conc.na()`

#### Méthode d'imputation

* `PKNCA_impute_method_start_conc0()`
* `PKNCA_impute_method_start_cmin()`
* `PKNCA_impute_method_start_predose()`

### Calculer les PK

1. Formater les données pour les calculs :
   
    * `conc_obj <- PKNCAconc(dt, Conc~Time|Subject)` pour les fécès et l'urine. Pour les fèces et les urines `duration=` et `volume=` avec la colonne déclarer `"colonne"`.
  
       * `time.nominal =` afficher les théoriques de prélévements (n'est pas utilisé pour les calculs).
       * `sparse = FALSE` échantillons clairesemés.
         
    * `dose_obj <- PKNCAdose(dt, Dose~Time|Subject)` déclarer les doses et leurs temps d'injection.
        
        * `route = ` précisier la route.
            
            * `"intravascular"` injection. Si l'injection est lente (infusion), il faut ajouter l'option `rate=` ou `duration=`.
            * `"extravascular"` ingestion.

!!! note
    La formule `treatment+subject` possibilité d'utiliser plusieurs colonnes pour créer un id sujet et `/Group` pour déclarer des groupes.
    
2. `PKNCAdata(conc_obj, dose_obj)` fusionner les tables doses et concentration. Le résultat est un tableau avec tous les paramètres cinétiques pour chaque individu (`summary(data_pknca)` afficher le résumé des groupes).
   
   * `intervals =` liste des indicateurs à ajouter (`data.frame(start = 0, end = Inf, cmax = TRUE...`).
   * `units = d_units` associer une unité aux valeurs (`pknca_units_table(concu="ng/mL", doseu="mg/kg", time="hr")`.
  
    Retour :
     
    * `$intervals` renvoie les paramètres calculés.
  
!!! note
    Il peut être utile de récupérer le tableau par défaut pour avoir les intervalles détectés automatiquement.
    1. Exécuter PKNCA une première fois pour récupérer les intervalles puis modifier le tableau en fonction des besoins utilisateurs.

4. `results_obj <- pk.nca(data_obj)` calculer les indicateurs.

    * `$result` ou `as.data.frame(results_obj)` afficher le tableau avec les résultats individuels.
    
6. `summary(results_obj)` résumer le résultat (`roundingSummarize()` ?). Les informations sur les valeurs entre crochet sont affichées sous le tableau dans le champ cation. Paramètre :
   
    * `pretty_names = T` afficher les jolies noms des PK.
    * `not_requested = "value"` valeur pour les indicateur non demandés.
    * `not_calculated = "value"` valeur pour les paramètres non calculés.

!!! note
    Pour les dosages répétés, les paramètres sont calculés pour chaque dose.

Fonctions supplémentaires : 

* `assert_PKNCAdata()` être un objet PKNCAdata.
* `pk_nca_result_to_df()` convertir le résultat en dataframe ?
* `roundString(numeric, nb_chiffres)` renvoyer un nombre en texte avec un nombre d'arrondis.
* `signifString(numeric, nb_chiffres)` renvoyer un nombre en texte avec un nombre de chiffres significatifs.
* `setDuration(obj, valeur)` ajouter une duration.
* `setRoute(obj, valeur)` ajouter une route.
* `find.tau(dose_tps)` détermine la durée entre chaque dose (pour les doses répétées). 
* `time_calc()` calculer le temps par rapport à un événement par exemple, un dosage.
* `exclude(myconc, reason="Carryover", mask=c(TRUE, rep(FALSE, 6)))` exclure certains points.
###  Les parametres cinétiques

* `PKNCA.options()` configuration.
* `PKNCA.options.describe("min.span.ratio")` avoir une description du champ.
* 
    * `$adj.r.squared.factor` value
    * `$max.missing` value
    * `$auc.method = "lin up/log down"`
    * `$conc.na` "drop"
    * `$conc.blq` blq `$first` ou `$middle` ou `$last` valeur possible `"keep"` ou `"drop"`.
    * `$first.tmax` TRUE
    * `$allow.tmax.in.half.life` FALSE
    * `$min.hl.points` 3
    * `$min.span.ratio` 2
    * `$max.aucinf.pext` 20
    * `$min.hl.r.squared` 0.9
    * `$tau.choices` NA
    * `$single.dose.aucs`
      
* `add.interval.col()` ajouter un indicateur avec un intervalle.
* `pk.calc.<indicateur>` utiliser une fonction de calcul d'un indicateur.

R                            | Description
-----------------------------|----
`tmax(conc, time)`           | $t_max$
`pk.tss.data.prep()`

#### Lister les PK

* `get.interval.cols()` lister les indicateurs disponibles (`$auclast.dn` pour avoir les informations sur un pk en particulier).

Mettre les indicateurs dans un dataframe.
``` R
dt_param <- get.interval.cols() %>%
  as_tibble() %>%
  select(-start, -end) %>%
  t() %>%
  as.data.frame()
```

* `pk.calc.dn` afficher la formule de la fonction.

#### Ajouter des indicateurs

Ajouter un nouveau PK.


``` R
add.interval.col("cmax",
                 FUN="pk.calc.cmax",
                 values=c(FALSE, TRUE),
                 unit_type="conc",
                 pretty_name="Cmax",
                 desc="Maximum observed concentration",
                 depends=c())
```

Déclarer la façon de calculer les valeurs des groupes

```R 
PKNCA.set.summary(
  name=nom,
  description = "median and 5th to 95th percentile",
  point=fct1,
  spread=fct2,
  rounding=list(signif=3)
)
```

#### Modifier les méthodes de calculs

modifier les fonctions de bases et ajouter une règle métier:

``` R
my_mean <- pk.business(FUN=mean)
my_mean(c(1:3, NA))
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
* `keep_units(fonction, x)` appliquer une fonction incompatible avec le format unit.
 
!!! note
    Si deux jeux de données avec des unités différentes, elles sont converties durant la fusion.

!!! warning
    Le `.` doit être transfomé en `*`.

### Rempsyc

Package avec de nombreuses fonctions pour 

!!! note 
    Il est normalement utiliser pour la Convenience functions for psychology.

https://rempsyc.remi-theriault.com/
