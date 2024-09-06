## Sélectionner

```
SELECT * FROM tab
```

## Filtrer

```
SELECT * FROM tab
WHERE condition
```

## Limiter le nombre de lignes à récupérer

```
SELECT * FROM tab
LIMIT n1 <OFFSET n2>
```

Options :
* `OFFSET` saisir le numéro du 0 pour le LIMIT.

## Filter avec une fonction d'agrégation

```
SELECT * FROM tab
HAVING fct(col1)
```

## Agréger les données

```
SELECT col1, col2, <fct\_agr> FROM table
GROUP BY col1, col2
```

NB : il est possible d’utiliser le numéro de la colonne à la place de son nom.

## Tirer 

```
SELECT * FROM tab
ORDER BY col1 <ASC/DESC>, col2 <ASC/DESC> ;
```

Paramétre (par défaut ASC) :

* `ASC` trier par ordre croissant (par défaut).
* `DESC` trier par ordre décroissant.

## Renommer les libellés

* `col AS nv_nom` renommer une colonne.
* `table AS nv_nom` renommer une table.

## Les comparateurs

| Comparateur | Comparateur |
|---|---|
| `=` | égale |
| `=>` ou `<=` | inférieur/supérieur ou égale |
| `IN ('var1', 'var2' )` | dans la liste |
| `<>` | différent |
| `is not null` | |

## Les fonctions d’agregation

| SQL | Fonctions |
|---|---|
| `SUM()` | somme |
| `MAX()` | maximum |
| `MIN()` | minimum |
| `COUNT()` | compter le nombre de lignes |

## Fonctions

| SQL | Fonctions |
|---|---|
| `ROUND()` | arrondir |
| `UPPER()` | afficher une chaîne en majuscule |
| `LOWER()` | afficher une chaîne en minuscule |
| `NOW()` | date et heure actuelle |
| `RAND()` | retourner un nombre aléatoire |
| `CONCAT()` | concaténer des chaînes de caractères |
| `CAST(variable AS type)` | convertir une donnée dans un autre format |
| `GROUP_CONCAT( col1 )` | regrouper les valeurs non nulles d’un groupe en une chaîne de caractère |

## Les fonctions date

| SQL | Fonction | 
|---|---|
| `CURRENT_DATE()` | date actuelle |
| `DATE_PART(date, 'type')` | extraire une partie d'une date (`DAY`,`MONTH`,`YEAR`) |
| `YEAR(date)` | extraire l'année |
| `MONTH(date)` | extraire l'année |
| `DAY(date)` | extraire l'année |

## Les jointures

```
SELECT * FROM table1 
jointure table2 
ON table1.a=table2.b
```

| SQL | definition |
|---|---|
| `INNER JOIN` | intersection de la table1 et table2 |
| `CROSS JOIN` | produit cartésien |
| `LEFT JOIN` | tout les enregistrements de table1 avec l’intersection de la table2 |
| `RIGHT JOIN` | tout les enregistrements de table2 avec l’intersection de la table1 |
| `FULL JOIN` | |
| `SELF JOIN` | |
| `NATURAL JOIN` | |
| `UNION JOIN` | fusion de table |


## Créer une table et sa structure

```
CREATE TABLE table 
( 	col1 type <option1>,
	col2 type <option2>, 
	... 
)
```

## Créer une table à partir d’une table

```
CREATE TABLE tab AS
[SELECT * FROM tab1]
```

Option :
* `NOT NULL` empecher la variable d’être nulle.
* `DEFAULT` attribuer une valeur par défaut.
* `PRIMARY KEY` clé primaire.

## Modifier une table

```
ALTER TABLE table
```

## Supprimer une table

```
DROP TABLE table
```

## Modifier des lignes

```
UPDATE table
SET colonne = ’nouvelle valeur’
WHERE condition
```

## Les formats

| SQL | Format |
|---|---|
| `BINARY` | booléen |
| `CHAR` | caractère |
| `DATE` | date |
| `DATETIME` | date heure | 
| `TIME` | heure |

## Si Alors

```
CASE <champ>
       WHEN condition THEN valeur 
       ELSE valeur2
END
```

## supprimer des lignes de données

```
DELETE FROM table
WHERE condition
```
