## Créer un nouveau format
```
PROC FORMAT <option> ;
	VALUE/INVALUE <\$> nomFormat
	modalite1 = libelle1
	modalite2 = libelle2
	<OTHER = "AUTRE"> ;
RUN;
```

* `VALUE`tranformer le format.
* `INVALUE` transformer l'information.

Option :

* `LIBRARY=bibliotheque` stocker le format dans une bibliothèque.

* `$ variable` d'origine est en caractère.
* `valeur1 - valeur2 = 'libelle'` construire des intervalles (`LOW` : mini `HIGH`: max ¡ pour exclure la valeur).
* `<` permet d'exclure la valeur d'une borne.
* NB : utile pour les variables ordinales et la création d'intervalles.
* `modalité1, modalité2` plusieurs éléments pour une modalité proc format.

* `""` valeur manquante caractère. 
* `.` valeur manquante numérique.

# Date et heure

* `'31MAR2017'd` déclarer une date. 
* `'31MAR2017 12:00:01'dt` déclarer un datestamps.
* `'12:00:01't` déclarer une heure.

## Date

| Format | SAS | Exemple |
|---|---|---|
| DDMMMYY | `DATEw.` | 16MAR08 |
| | DATE5. | 16MAR
| | DATE6. | 16MAR |
| | DATE7. | 16MAR08 |
| | DATE8. | 16MAR08 |
| | DATE9. | 16MAR2008 |
| | DATE11. | 16-MAR-2008 |
| | DDMMYY5. | 24/12 | 
| | DDMMYY6. | 241205 |
| | ddmmyy7. | 241205 |
| | ddmmyy8. | 24/12/05 |
| | DDMMYY10. | 24/12/2005 |
| yyyymmdd | `YYMMDDx10.` | 20170331
| yy-mm-dd | `YYMMDDx8.` | 170331 |


`x` délimiteur entre les informations. Liste des valeurs possibles :

* `d` tiret du 6 (2017-03-31).
* `s` slash (2017/03/31).

## Datetime

| Format | SAS | Exemple |
|---|---|---|
DDMMMYY hh:mm:ss | `DATETIME.` | 31MAR17 12:31:10 |
hh:mm:ss | `TIME8.` | 11:09:15

## Pourcentage

| Format | SAS | Exemple |
|---|---|---|
| NN% | `PERCENTw` | 97% |

## Les délimiteurs

| Délimiteur | SAS |
|---|---|
| tabulation | `'09'x` |

## Convertir

| Fonction | Définition |
|---|---|
| `INPUT( 'texte', format_num)` | texte en numérique |
| `PUT(nombre, format_carac)` | numérique en caractère |
| `INTPUT( 'texte, format_date)`  | texte en date |
| `INTPUT( PUT(numerique, BEST8.), format_date)` | numérique en date |
