```
db.collection.fonction().option
```

* `$colonne` notation des colonnes.
* `"$item.sousitem"` accéder à un sous item.

## Option sortie

* `.limit(nbre)` limiter le nombre de sortie
* `.sort({ champ: 1 })` trier le résultat croissant (-1 décroissant)

## Première fonction

* `findOne()` afficher le premier document
* `count()` afficher le nombre de document
* `distinct("champ")` afficher les données pour un champ.

## Filtrer les données

```
db.restaurants.find(
  { name: "La Grenouille" },
  <{champ: 1 }>
).pretty()
```
* _id: 1/0 : identifiant du document



| Opérateur | Définition |
|---|---|
| $eq | égalité |
| $gt | supérieur |
| $gte | supérieur ou égale |
| $lt | inférieur |
| $lte | inférieur ou égale |
| $in | dans la liste |

| Opérateur logique | Définition |
|---|---|
| $and | et |
|$or | ou |
| $nor | ou sans l'intersection |

## Agréger les données

```
db.restaurants.aggregate([
	{ $match: { name: { $ne: "" }} },
    	{ $group: { _id: "$name", nb: { $sum: 1 }}},
	{ $sort: { nb: -1 }},
	{ $limit: 10 }
])
```

| Fonction | Définition |
|---|---|
| `$sum: champ` | somme | 
| `$avg: champ` | moyenne | 
| `$min: champ` | minimum | 
| `$max: champ` | maximum |
| `$concat: [ "champ1",  "champ2" ]` | concaténer des champs |
| `$addToSet:` | ????????

| fonction | | 
|---|---|
| `$group: { _id: "$champ" }` | 
| `$limit: nbre` | limiter le nombre de lignes |
| `$sort: { champ: 1/-1 }` | 
| `$unwind: "$champ"` | découpage en plusieurs lignes. |

| Valeur | défintion  |
|---|---|
| `Missing` | valeur manquante |
| `Null` | valeur nulle |
