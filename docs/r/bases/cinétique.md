Variables utilisées pour calculer les indicateurs :

* concentration de la substance.
* poids de l'individu.
* temps.
* la dose càd la quantité de médicament administré. 
* mode d'adminitration (en intravasculaire, IV Bolus pour les injections rapides et infusion pour les injections longues, sinon par voie orale). 

!!! note
    "Nominal" correspond à théorique par opposition à mesurée.

Les principaux acronymes et leur signification :

* Below Limite of Quantification (BLQ) sous la limite de quantification.
* Lower Limit Of Quantification (LLOF) quantité d'analyte la plus faible qui peut être détecter quantitativement avec précision et exactitude.
* high value of variability (CV) en % : $\frac{sd(vec)}{mean(vec) \cdot 100}$.
## Rappel

* Precision (précision) cohérence des mesures. 
* Accuracy (exactitude) proximité avec une valeur de référence.
* Erreur relative : % de variation de la différence entre la valeur réelle et théorique par rapport à la valeur théorique.
## Hypothèse

* La pente correspond au taux de disparition du médicament. Elle est proportionnelle à la quantité de médicament présent.
* La concentration dans les tissus est proportionnelle à celle du sang.
* La vitesse de disparition est constante car proportionnelle. Pour linéariser, on calcule la vitesse : il faut tracer la concentration en fonction de la concentration par le temps.
En principe on se ramène à une équation différentielle du premier ordre : elle est linéaire en phase ascendante et logarithmique en phase d'élimination.
## Les indicateurs

!!! note 
    On ajoute l'adjectif "effective" (par opposition à "terminal") pour parler des indicateurs calculés à partir de l'extrapolation vers un temps infini.
    Les mesures de concentration sont prolongées à partir de la pente des deux dernières mesures.
### Principaux indicateurs

Convention de nommage des principales valeurs :

* $C_0$ ou $C_p$ concentration initiale. Elle peut être déduite à partir de la courbe, par exemple, pour la voie ... : $C_0 = \frac{D}{V_{blood}}$. Il existe plusieurs méthodes "c0", "logslope", "c1", "cmin", "set0".
* $C_t$ concentration à un temps donné.
* $C_{last}$ et $t_{last}$ dernière concentration observées au dessus de BLQ et son temps.

!!! warning
	Les valeurs d'intégration ou à prendre en compte varie en fonction de la route.  
#### Absorption

* $k_a$ (constante d'absorption) - $k_a = \frac{1}{MAT} = \frac{\ln{2}}{t_{\frac{1}{2}a}}$ : taux auquel le médicament est absorbé dans la circulation systémique.
* $t_{\frac{1}{2}a} = \frac{\ln{2}}{k_a}$ temps de demi vie d'absorption.
* $F$ biodisponibilité est le rapport $\frac{AUC_{PO}}{AUC_{IV}}$. Elle correspond au % du médicament qui a pu être absorbée par le tube digestif.
#### Exposition

* $AUC = \int{c(t) \cdot dt}$ décrit l'exposition à un médicament durant toute la durée de mesure ($g \cdot mL^{-1}  \cdot h$). Une AUC élevée signifie soit que le médicament a atteint une valeur élevée ou qu'il reste longtemps dans l'organisme.

    * $AUC_t$ ou $AUC_{last}$ AUC terminal entre $t_{0}$ et $t_{last}$.
    * $AUC_{int}$ AUC effective sur un intervalle de temps donné.
    * $AUC_{\inf}$ AUC extrapolé de $t_last$ à $t_{\infty}$
    * $RacD1 = \frac{AUC}{AUC_t}$ (t last AUC finale). Si l'a $RacD1 \lt 20\%$ alors $AUC_t$ n'est pas représentative.
* $C_{max}$ et $t_{max}$ concentration maximale et son temps associé.
* $AUCM = \int{c(t) \cdot t \cdot dt}$  en ($g \cdot mL^{-1}  \cdot h^2$)

!!! note
	L'intégration se fait en sommant l'aire de chaque trapèze $(c_2 + c_1) \cdot \frac{(t_2 - t_1)}{2}$.

!!! note
	Deux méthodes d'extrapolation pour la dernière décroissance : en utilisant le taux d'élimination $\lambda$ (et le modèle) ou en utilisant le triange avec la dernière valeur mesurée. 
#### Résidence

* Mean Residence Time (MRT) - $MRT = \frac{AUCM}{AUC}$ :  temps moyen de résidence du médicament dans l'organisme. Il est souvent déterminé à partir de Michaelis-menten ou de la $Vss$ .
* Mean Absorption Time (MAT) - $MAT = MRT_{po} - MRT_{IV}$ : temps moyen d'absorption complète du médicament.
#### Distribution

* $V_D$ ou $Vss$, volume de Distribution ou Volume Steady State. Il permet de savoir si le médicament est distribué dans les tissus. Volume de fluide par masse de médicament $V_d = \frac{D}{C_0}$. Il décrit à l'état d'équilibre càd la répartition d'un médicament dans l'organisme. Il correspond au volume de plasma nécessaire pour que la concentration soit homogène dans tous le corps. Il permet notamment de déterminer la dose à administrer pour arriver à la concentration thérapeutique. $Vss \cdot \frac {\ln 2}{CL}$ et $Vss = \frac{volume\ de\ médicament\ dans\ le\ corps}{Concentration\ plasmatique}$. $V_d = D \cdot \frac{AUMC}{AUC^2}$. Un $Vss$ faible signifie que le médicament est principalement dans le sang.
* $Vd_{beta}$ Terminal volume of distribution ($V = T_{\frac{1}{2}} \cdot \frac{Cl}{\ln 2}$) défini comme le volume pour lequel la quantité de médicament soit distribuée de façon uniforme pour expliquer la concentration observée dans le sang.
#### Elimination

* $t_{\frac{1}{2}e} = \frac{\ln{2}}{k_e}$ temps de demi vie d'éliminitation càd temps nécessaire pour éliminer la moitié du médicament.
	* __Clairance__ mesure la capacité de l'organisme à éliminer une substance médicamenteuse du système biologique. Cela correspond au volume de plasma purifié (dont le médicament est éliminé) par unité de temps. C'est le rapport entre la quantité d'une substance éliminée par unité de temps et la concentration dans un fluide de l'organisme. $CL = \frac{Dose}{AUC} = V_d \cdot k_e$ clairance.
* $k_e = \frac{1}{MRT} = \frac{\ln{2}}{t_{\frac{1}{2}e}} = \frac{CL}{V_d}$ (constante d'élimination) taux d'élimination moyen du médicament de la circulation systémique. Il est calculé sur la phase d'élimination

* $ae$ montant du produit excrété dans l'urine en g ou mol. Nb il existe aussi le pourcentrage de la dose exrétée.
* $Cl_R$ clérance rénale $\frac{ae}{AUC_t}$ volume de plasma sanguin débarrassé du produit par unité de temps.

!!! note 
    Il existe principalement deux clairances : hépatique et reinnale.

Superposition est une méthode pour prédire les concentrations à partir des valeurs obtenues. Les données peuvent servir pour déterminer les temps pour les doses répétées.

### Ratio blood plasama

Le ratio blood plasma est le proportion entre la concentration en médicament dans le sang et celle de la siys fraction de plasma.

Clariance sanguine = clairance plasmatique / ratio blood/plasma
### Bibliographie 

* [Boomer](https://www.boomer.org/c/p1/Ch05/Ch0506.html) site avec toutes les méthodes de pharmacocinétique.
* [Non-compartmental analysis](https://blog.djnavarro.net/posts/2023-04-26_non-compartmental-analysis/) vulgarisation de la pharmacocinétique non compartiemental. 
