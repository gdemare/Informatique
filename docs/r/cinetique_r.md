
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

"high value of variability" noté CV%
