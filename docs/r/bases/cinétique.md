[Boomer](https://www.boomer.org/c/p1/Ch05/Ch0506.html) bon site en anglais avec l'explication pour chaque paramètre en PKNCA.

Variable utilisée pour calculer les indicateurs :

* concentration de la substance.
* poids de l'individu.
* temps.
* la dose càd la quantité de médicament administré. 
* mode d'adminitration (en intravasculaire, IV Bolus pour les injections rapides et infusion pour les injections longues, sinon par voie orale). 

!!! note
    "Nominal" correspond à théorique par opposition à mesurée.

Les princiapux acronymes et leur signification :

* Below Limite of Quantification (BLQ) sous la limite de quantification.
* Lower Limit Of Quantification (LLOF) quantité d'analyte la plus faible qui peut être détecter quantitativement avec précision et exactitude.
* high value of variability (CV) en % : $\frac{sd(vec)}{mean(vec) \cdot 100}$.

## Rappel

* precision (précision) cohérence des mesures. 
* Accuracy (exactitude) proximité avec une valeur de référence.
* Erreur relative : % de variation de la différence entre la valeur réelle et théorique par rapport à la valeur théorique.

## Hypothèse

* La pente correspond au taux de disparition du médicament. Elle est proportionnelle à la quantité de médicament présent.
* La concentration dans les tissus est proportionnelle à celle du sang.
* La vitesse de disparition constante car proportionnelle. Pour linéariser, on calcule la vitesse : il faut tracer la concentration en fonction de concentration par le temps.
En principe on se ramène à une équation différentielle du premier ordre : elle est linéaire en phase ascendante et logarithmique en phase d'élimination.

## Les indicateurs

!!! note 
    On ajoute l'adjectif "effective" (par opposition à "terminal") pour parler des indicateurs calculés à partir de l'extrapolation vers un temps infini.
    Les mesures de concentration sont prolongées à partir de la pente des deux dernières mesures.

### Principaux indicateurs

* Absorption :
* Exposition :
* Résidence :
* Distribution :
* Elimination :

Convention de nommage des princiaples valeurs :

* $C_0$ ou $C_p$ concentration initiale. Elle peut être déduite à partir de la courbe, par exemple, pour la voie ... : $C_0 = \frac{D}{V_{blood}}$. Il existe plusieurs méthodes "c0", "logslope", "c1", "cmin", "set0".
* $C_t$ concentration à un temps donné.
* $C_{last}$ et $t_{last}$ dernière concentration observées au dessus de BLQ et son temps.

#### Absorption

* $K_a$ (Constante d'absorption): Taux auquel le médicament est absorbé dans la circulation systémique.
* $F$ biodisponibilité est le rapport $\frac{AUC voie orale}{AUC voie IV} = %\ dans\ le\ sang$.

#### Exposition

* AUC décrit l'exposition à un médicament durant toute la durée de mesure ($g \cdot h \cdot mL^{-1}$).

    * $AUC_t$ ou $AUC_{last}$ AUC terminal entre $t_{0}$ et $t_{last}$.
    * $AUC_{int}$ AUC effective sur un intervalle de temps donné.
    * $AUC_{\inf}$ AUC extrapolé de $t_last$ à $t_{\infty}$
    * $RacD1 = \frac{AUC}{AUCt}$ (t last AUC finale). Si l'a $RacD1 \lt 20%$ alors $AUC_t$ n'est pas représentative.

*   maximale observée.
* $C_{max}$ et $t_{max}$ concentration maximale et son temps associé.

#### Résidence

* Mean Residence Time (MRT) temps moyen de résidence du médicament dans l'organisme. Il est souvent déterminé à partir de Michaelis-menten ou vss.
* Mean Absorption Time (MAT) temps moyen pour l'absorption compléte du médicament.

#### Distribution 

* $V_D$ Volume de Distribution ou Volume Steady State (Vss). Il permet de savoir si le médicament est distribué dans les tissus . Volume de fluide par
  masse de médicament $V_d = \frac{D}{C}$. Décri à l'état d'équilibre, la répartition d'un médicament dans l'organisme. Il est défini comme la période où
  la concentration du médicament dans le plasma sanguin et la concentration dans les tissus périphériques. Il permet notamment de déterminer la dose à
  administré pour arriver à la concentration thérapeutique. $Vss \cdot \frac {\ln 2}{CL}$ $Vss = \frac{volume\ de\ médicament\ dans\ le\ corps}{Concentration\ plasmitique}$.
 
    * $Vd_{beta}$ Terminal volume of distribution ($V = T_{\frac{1}{2}} \cdot \frac{Cl}{\ln 2}$) defined as the volume in which the amount of drug would need to be uniformly distributed to produce the observed whole blood concentration

#### Elimination

* __Clairance__ mesure la capacité de l'organisme à éliminer une substance médicamenteuse du système biologique.
Cela correspond au volume d'un fluide de l'organisme (souvent plasma) purifié éliminé par unité de temps. C'est
rapport entre la quantité d'une substance éliminée par unité de temps et la concentration dans un fluide de l'organisme. $CL = \frac{Dose}{AUC}$ clairance.
* $K_e$ (Constante d'élimination) taux d'élimination du médicament de la circulation systémique.
* $t_{1/2}$ temps de demi vie càd temps nécessaire pour éliminer la moitié du médicament.
* __ae__ montant excrété.

!!! note 
    Il existe principalement deux clairances : hépatique et reinale.


Superposition est une méthode pour prédire les concentrations à partir des valeurs obtenues. Les données peuvent servir pour déterminer les temps pour les doses répétées.
