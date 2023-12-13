`/opt/sas/data/` chemin du dossier SAS.

`LIBNAME nomBiblio "chemin";` Créer une bibliothèque.

`OPTION FMTSEARCH=(bibliotheque.format)` créer une bibliothèque format.

* `nom:` joker sur SAS.
* `var1-var8` selectioner les variables de var1 à var8.
* `variable--varh` selectioner les variables situer entre variable et varh.
* `"nom variable"n` nom de variables avec des espaces.
* `_CHARACTER_` selectionner les variables de type charactère.
* `_NUMERIC_` selectionner les variables de type numériqu.

# Les arguments des tables

```
DATA=table <(option)>
```

Listes des arguments :

* `DROP = var` champs à supprimer.
* `KEEP = var` colonne à garder.
* `RENAME = ( col=NV NOM ... )` renommer une colonne.
* `FIRSTOBS=num` numéro de l’observation de départ.
* `OBS=nbre` nombre d’observations à sélectionner.

## DATA

```
DATA nomtable;
	instruction ;
RUN ;
```

* `LENGTH <$> taille;` taille des colonnes.
* `FORMAT variable <$> taille.;` format des colonnes.
* `WHERE condition;` sélectionner une partie du jeu de données.
* `SET table;` utiliser une table.
* `INFORMATION variable <type>;` format d'affichage de la table.
* `KEEP variable;` colonne à garder (NB : voir arguments m chose).
* `LABEL variable='libelle';` labelliser une colonne.
* `RETAIN variable;` garder la valeur de la ligne au dessus.
* `ARRAY variabel colonne:`parcourrir les colonnes d'un data
* `DO OVER variable_colonne ; intruction; END;` parcourrir les colonnes.
* `DO i=1 TO nbre ; END;` DIM(court)

```
ARRAY variable "Dim 1"n-"Dim 7"n;
	DO i=1 TO DIM(variable);
		variable{i} = variable{i}/(11*SQRT(%SCAN(&inertie.,&i.,' ')));		
	END;

```

## Les jointures

```
MERGE tab1 tab2
	BY clé;
IF condition;
```

Joindre par le numéro de la ligne.
```
SET tab1;
SET tab2;
```

## Importer un jeu de données

```
INFILE fichier <option>;
```

Options :

* `MISSOVER` lire des enregistrements avec des données manquantes en fin d'enregistrement.
* `DSD` deux séparateurs successifs implique une donnée manquante.
* `DELIMITER = delimiteur` séparateur de champs.

## Déclarer un jeu de données dans DATA

```
DATALINES;
données
;
```

## Condition

```
IF condition THEN DO;
	<instruction1>;
END;
<ELSE IF a THEN DO;>
	<instruction2>;
END;
<ELSE DO;>
	<instruction3>;
END;
```

Instruction possible

Instruction	| Action
----------------|---
`OUTPUT`	| conserver l'observation
`DELETE`	| supprimer l'observation

### Comparateur

SAS | Définition
---|---
`val1 = val2` | égalité |
`var IN (val1, val2)`	| dans la liste |
`val1 ¡¿ val2` 		| différent |
`val1 ¡= val2` ou `val1 ¿= val2`| supérieur, inférieur ou égal |
`IS NULL` | valeur nulle pour les chaînes de caractères |
`=.` | valeur nulle pour les numériques |

## Opérateur logique

| SAS | Définition |
|---|---|
| `NOT condition` | négation |
| `condition1 &/AND condition2` | et |
| `condition1 —/OR condition2` | ou |

## Fusion

```
SET table1 table2;
```

## Fonctions

| SAS | Définition |
|---|---|
| `ABS(numérique)` | valeur absolue |
| `TRIM(chaine)` | enlever les blancs |
| `LENGTH(chaine)`| nombre de caractère |
| `N` | numéro de lignes. |
| `LAG(variable)` | renvoyer la valeur de l'observation précédente. |
| `MISSING(variable)` | renvoie vrai si la valeur est manquante. |
| `DELETE` | supprimer l'observation lu. |
| `PUT( variable, format)` | convertir le format d'une variable. |
| `SYMGET(macro-varibe)` | utiliser une macro dans un data. |
| `INPUTN( date, format)` | créer une variable date. |
| `SUBSTR( chaîne , début, fin)` | extraire une chaine de caractère. |
| `chaine1 || chaîne2` | concaténer des chaînes de caractères. |
| `CATX(délimiteur,chaîne1, chaîne2)` | concaténer des chaînes des caractères. |
| `COMPRESS(texte)` | concaténer du texte en supprimant les blancs. |
| `FLOOR(variable)` | arrondir à l'entier inférieur. |
| `CALL SYMPUT('var','valeur')` | attribuer une valeur a une macro variable dans une step DATA. |
| `COUNTW( phrase, "séparateur")` | compter le nombre de separateur. |
| `RAND("UNIFORM")` | générer un nombre aléatoire entre 0 et 1. |
| `UPCASE(var)` | mettre en majuscule |
| `LOWCASE(var)` | mettre en minuscule |
| `INDEX(variable, 'chaine')` | vérifier que la chaine est présente dans un champ. |

## Fonctions date

| SAS | Définition |
|---|---|
| `DATEPART(dateheure)` | extraire la date d'une datetime. |
| `TIMEPART(dateheure)` | extraire l'heure d'une datetime. |
| `YEAR(date)` | récupérer l'année |
| `MONTH(date)` | récupérer le mois. |
| `INTNX( type, datetime, nbre )` | ajouter des jours, mois, à une date (`'YEAR'`, `'MONTH'`, `'DAY'`, `HOUR`, `MINUTE`, `SECOND`). |
| `MDY( mois, jour, année)` | créer une date. |
| `HMS(heure, minute, seconde)` | créer une heure. |
| `DHMS(date, heure)` | créer une date heure. |
| `QTR(date)` | donner le trimestre de la date. |
| `INTCK("YEAR", date1, date2, <"C">)` | calculer la date l'âge. NB : utiliser DATEPART |

## Paramètrer les sorties SAS 

`GOPTIONS `
Options : 

* `HTEXT=4pct` taille de la police.
* `FTEXT="police";` type de police.

## Les jockers

* `var1--var8` selection les variables 1 à 8.

## SQL

```
PROC SQL <option>;
	requeteSQL
;QUIT;
```

Option :

* `OUTOBS=nbre` nombre d'observation en sortie.
* `FORMAT=format` formater une colonne.

## Trier

```
PROC SORT <option>;
	BY (DESCENDING/ASCENDING) champ;
RUN;
```

Options :

* `NODUPKEY` supprime les doublons du BY.

## Décrire le contenu d'une table

```
PROC CONTENTS;
	<option> ;
RUN ;
```

Option :

* `BY variable;` appliquer la description pour chaque modalité d'une variable.

## Transposer

```
PROC TRANSPOSE;
	VAR valeur;
	BY grouper ;
	ID nv_variables;
RUN;
```

| grouper | nv_variables | nv_variables | nv_variables |
|---|---|---|---|
| grouper | valeur |valeur |valeur |
| grouper | valeur |valeur |valeur |

Réalise une transposer simple sans paramètre : ligne <-> colonne

Option :

* `_NAME_ = nom`

## Normaliser 

```
PROC STANDARD ;
	VAR variable;
RUN;
```

Option :

* `MEAN=moyenne` centrer les données.
* `STD=ecart-type` réduire les données.

## Tableau de Burt ou disjonctif

```
PROC TRANSREG;
	MODEL CLASS (variables </ option2 >;
	OUTPUT OUT=table;
	ID indentifiant; 
RUN;
```

Option :

* `DESIGN` ne pas attribuer des coefficients aux variable
* `NOPRINT` ne pas afficher le tableau en sorte.

Option 2 :

* `ZERO = NONE` valeur par défaut.

## Supprimer/renommer une table

```
PROC DATASETS <library=> ;
	<action> table1 table2;
	CHANGE ancien\_nom = nouveau\_nom;
RUN;
```

Action :

* `DELETE` supprimer des tables (KILL supprime toutes les tables).
* `NODETAILS` ne pas afficher de sortie.
* `CHANGE` renommer des tables.

## Créer une variable rang

```
PROC RANK <OUT=data>;
	VAR col;
	RANKS nvcolonne;
	<BY> col;
RUN;
```

## Exporter le résultat

Output Delivery System exporte le résultat des procédures.

### Dans SAS

```
ODS TRACE ON ;
	procédure;
ODS TRACE OFF;
```

Lister les objets crées par la procédure.

### En PDF

```
ODS PDF FILE="fichier.pdf";
	procédure;
ODS PDF CLOSE;
```

### En excel

```
ODS EXCEL FILE="fichier.xlsx" <OPTIONS(option)>;
	table1;
ODS EXCEL <OPTIONS(option)>;
	graph2;
ODS EXCEL CLOSE;
```

Option :

* `SHEET NAME="feuille1"` nommer la feuille de l'export.
* `START AT="nligne,ncol"` choisir la position de la premier cellule du tableau.
* `EMBEDDED TITLES="yes"` exporter les titres.

### en XML

```
ODS TAGSETS.EXELXP FILE = "fichier.xml" <OPTIONS(option)>;
	procédure;
ODS TAGSETS.EXELXP CLOSE;
```

### Créer une table SAS

```
ODS OUTPUT nom=libellé;
	procédure;
ODS OUTPUT CLOSE;
```
convertir la sortie de la procédure en table SAS.

```
PROC EXPORT DATA=table
		    DBMS=csv 
		    OUTFILE="C:\Users\Public\Documents\test.csv"  
		    REPLACE;
 		    DELIMITER=";";
RUN;
```

### Afficher les graphiques des procédures

```
ODS GRAPHICS ON;
procédure;
ODS GRAPHICS OFF;
```

### Paramètre supplémentaire

```
ODS SELECT/EXQLUDE nomTable=libelleObjet ;
```

Garder/retirer des objets de la PROC mettre avant l'ODS.

## Envoyer par email

```
FILENAME MAIL EMAIL=destinataire FROM='emetteur' SUBJECT='sujet' <option>;
DATA _NULL_;
	FILE MAIL;
	PUT 'ligne1';
	PUT 'ligne2';
RUN;
```
Option :

* `CC = email` mettre en copie.
* `ATTACH =("fichier" CONTENT TYPE="application/excel")` joindre un fichier.

## Données SAS

* `SASHELP.VSTABLE` vue de l'ensemble des tables et leur bibliothèque.
