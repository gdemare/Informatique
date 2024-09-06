* `Alt + Entré` retour à la ligne dans une cellule.
* `"symbole`caractère d'échappement.

## Protéger les données de modifications possibles

* `Révision" > "Protéger la feuille` protéger une feuille.
* `Révision" > "Protéger le classeur` protéger un classeur.
* `Affichage" > "Figer...` figer une ligne ou un colonne.

### Protéger des cellules

1. Sélectionner les cellules à protéger.
2. Clic droit, `Format de cellule`
3. Onglet `Protection`
4. Décocher `Verrouillé`, puis `OK`
5. Aller dans `Révision > Protéger la feuille`

## Opérateurs logiques

* `ET(condition1;condition2)` Et.
* `OU(condition1;condition2)` Ou.
* `ESTVIDE(cellule)` test si la cellule est vide.
* `NON()` négation. 

## Les conditions

* `SI([condition];[condition vrai];[condition fausse])` exemple: SI(cell=<14;0;cell-13)
* `RECHERCHEV(valeur;zone;numéro; valeur_proche)` renvoyer la valeur de la colonne numéro de la ligne.
* `RECHERCHEH(valeur;zone;numéro; valeur_proche)` renvoyer la valeur de la ligne numéro de la colonne.

## Manipuler les dates

* `AUJOURDHUI()` afficher la date du jour.
* `DATE(année;mois;jour)` construire une date.
* `JOUR(date)` extraire le jour.
* `MOIS(date)` extraire le mois.
* `ANNEE(date)` extraire l'année.
* `JOURSEM(date;type)` numéroter les jours de la semaine. Type :

	* `1` dimanche=1 samedi=7
	* `2` lundi=1 dimanche=y
	* `3` lundi=0 dimanche=1

* `NO.SEM(date; type)` numéroter les semaines. Type :
 
	* `1` dimanche le premier jour de la semaine
	* `2` lundi le premier jour de la semaine

* `NO.MOIS(date;type)` numéro du mois. Type :
  
	*  `1` dimanche le premier jour de la semaine
	* `2` lundi le premier jour de la semaine\
 
 * `TEXTE(date;code)` afficher le nom du mois ou du jour.

Code    | Définition
--------|---
`"jjj"` | jour
`"mmm"` | mois

* `DATEDIF(date1;date2;code)` age entre deux date (NB : date1=<date2).

Code   | Definition
-------|---
`"y"`  | années
`"m"`  | mois
`"d"`  | jours
`"ym"` | mois, une fois les années soustraite
`"yd"` | jours, une fois les années soustraites
`"md"` | jours, une fois les années et mois soustraits

### Ajouter une nombre d'années, mois, jours

`DATE(ANNEE(A2)+B2;MOIS(A2);JOUR(A2))`

## Formater du texte

Fonction 			| Définition
--------------------|---
`MINUSCULE(text)` 	| mettre le texte en minuscule
`MAJUSCULE(text)` 	| mettre le texte en majuscule
`NOMPROPRE(text)` 	| mettre une majuscule à la première lettre des mots
`STEXT()` 			|
`NBCAR(text)` 		| compter le nombre de caractères

## Supprimer un tableau

1. Onglet "Création tableau".
2. Création.
3. Convertir en plage.

## Les heures

`TEMPS(heure;minute;seconde)` déclarer une heure.
Les opérateurs fonctionnent directement. 
Calculer un nombre d'heures. Il faut formater la case en `[h]:mm;@` sinon le total ne peut pas dépasser 24 heures.

## Graphique 

* Echelle logarithmique `Cliquer sur l'axe. > Option axe > Echelle logarithmique`.
* Barre d'erreurs `Barre d'erreurs > Histogramme > Personnaliser`.

### Histogramme variable continue

Il faut calculer la taille des classes (abscisses) :

* Superposition 100%
* Largeur de l'intervalle 0%

## Indicateurs statistiques

Formule 			| Définition
--------------------|---
`MEDIANE()` 		| médiane
`QUARTILE(;1 ou 3)`	| quartile
`VAR.P` 			| variance
`VAR.S` 			| variance corrigée
`ECARTYPE.P` 		| écart type
`ECARTYPE` 			| écart type corrigé 
`NB()` 				| nombre de cellules non vides

## Les tests statistiques

`Anova` activer dans Compléments > Analysis ToolPak. Onglet Données
`T.TEST(col1 ; col2 ; 1 ou 2 ; )` test de student.

* `1` par paires.
* `2` sur deux échantillons de variance égale (homoscédastique).
* `3` sur deux échantillons de variances différentes (hétéroscédastique).

## Nbre aléatoires

`ALEA.ENTRE.BORNES(borne_inf, borne_sup)` génére un nombre aléatoire entre deux nombres.

## Chaine de caractères 

* `SUBSTR(chaîne_de_caractères; début; longueur)` 
* `NBCAR(texte)` renvoie le nombre de caractères de la chaine.
* `CHERCHE("ul";texte; )` renvoie la positon de la chaine de caractères.
* `STXT(texte; position début; nb_caractères)` renvoie la sous chaine de caractères.
