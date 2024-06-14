[Boomer](https://www.boomer.org/c/p1/Ch05/Ch0506.html) bon site en anglais avec l'explication pour chaque paramètre en PKNCA.

Variable utilisé pour calculer les indicateurs :

* concentration de la substance.
* poids de l'individu.
* temps.
* la dose 
* mode d'adminitration (IV Bolus=injection rapide en intra, Voie orale, 

!!! note
    "Nominal" correspond à théorique par opposition à mesurée.

Les princiapux acronymes et leur signification :

* Below Limite of Quantification (BLQ) sous la limite de quantification.
* Lower Limit Of Quantification (LLOF) is the lowest amount of an analyte in a sample that can be quantitatively determined with suitable precision and accuracy
* high value of variability (CV) en % : $\frac{sd(vec)}{mean(vec) \cdot 100}$.

## Hypothèse

La pente correspond au taux de disparition du médicament.
La concentration dans les tissus est proportionnelle à celle du sang.
Vitesse de disparition constante car proportionnelle. Pour linéariser, on calcule la vitesse : il faut tracer la concentration en fonction de concentration par le temps.
En principe on se ramène à une équation différentielle du premier ordre.
linéaire en phase ascendante logarithmique en phase d'élimination.
L'élimination est aussi proportionnelle.

## Les indicateurs

!!! note 
    On ajoute l'adjectif "effective" (par opposition à "terminal") pour parler des indicateurs calculer sur extrapolation vers un temps infini.
    Les mesures de concentration sont prolongée à partir de la pente des deux dernières mesures.

### Principaux indicateurs

* clairance : décrit la capacité de l'organisme à éliminer une substance médicamenteuse du système biologique.
Cela correspond au volume d'un fluide de l'organisme (souvent plasma) purifié éliminé par unité de temps. C'est
rapport entre la quantité d'une substance éliminée par unité de temps et la concentration dans un fluide de l'organisme. $CL = \frac{Dose}{AUC}$ clairance.

!!! note 
    Il existe principalement deux clairances : hépatique et reinale.
    
* AUC décrit l'exposition à un médicament durant toute la durée de mesure ($g \cdot h \cdot mL^{-1}$).

    * $AUC_t$ ou $AUC_{last}$ AUC terminal entre $t_{0}$ et $t_{last}$.
    * $AUC_{int}$ AUC effective sur un intervalle de temps donné.
    * $AUC_{\inf}$ AUC extrapolé de $t_last$ à $t_{\infty}$
    * RacD1 = AUC/AUCt (t last AUC finale). Si l'a $RacD1 \lt 20%$ alors $AUC_t$ n'est pas représentative.

* $V_D$ Volume de Distribution ou Volume Steady State (Vss). Il permet de savoir si le médicament est distribué dans les tissus . Volume de fluide par masse de médicament $V_d = \frac{D}{C}$. Décri à l'état d'équilibre, la répartition d'un médicament dans l'organisme. Il est défini comme la période où la concentration du médicament dans le plasma sanguin et la concentration dans les tissus périphériques. Il permet notamment de déterminer la dose à administré pour arriver à la concentration thérapeutique. $Vss \cdot \frac {\ln 2}{CL}$ Vss = volume de médicament dans le corps/la concentration plasmitique
 
    * Vd_beta Terminal volume of distribution (V=T½*Cl/ln2) defined as the volume in which the amount of drug would need to be uniformly distributed to produce the observed whole blood concentration

* F biodisponibilité. Rapport AUC voie orale/AUC voie IV = % dans le sang.



### Les indicateurs concentration

* $C_0$ ou $C_p$ concentration initiale. Elle peut être déduit à partir de la courbe, par exemple, pour la voie ... : $C_0 = \frac{D}{V_{blood}}$.
* $C_t$ concentration à un temps donné.
* $C_{max$ concentration maximale observée.
* $C_{last}$ dernière concentration observées au dessus de BLQ.
  
### Indicateur temporel

* $t_{max}$ temps avec la concentration maximale.
* $t_{1/2}$ temps de demi vie càd temps nécessaire pour éliminer la moitié du médicament.
* $t_{last}$ temps de la mesure de $C_{last}$.
* Mean Residence Time (MRT) temps moyen de résidence du médicament dans l'organisme. Il est souvent déterminé à partir de Michaelis-menten ou vss.

### Autres :


Indicateurs         | IV bolus dose | Description
--------------------|---------------|-----
`start`             |               |
`end`               |               |
`auclast`           |               |
`aucall`            |               |
`c0`                | X             | Estimé la concentration à t0. plusieurs méthode c("c0", "logslope", "c1", "cmin", "set0")
`ae`                |               | montant excrété (`sum(conc*volume)`)

