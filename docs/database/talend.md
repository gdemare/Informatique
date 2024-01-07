## Installation

Installer Talend sur un poste :

1. Intaller Java SE Development Kit 13
2. Créer la variable JAVA_HOME:

	1. PC propriété 
	2. Paramètres systèmes avancés
	3. Variables d'environnement
	4. Créer une nouvelle variable 

		* Valeur  : jre1.8.0_77
		* Nom 	  : JAVA_HOME.

	5. Ajouter %JAVA_HOME%/bin à la variable Path.

3. Installer Talend.

## Intégration des données

### Logs & erreurs

* `tLogRow` afficher les données dans la console.
* `tFileInputDelimited` charger un fichier délimiteur.

### Filtre

* `tFilterRow`

### Transformation

* `tMap` manipuler les données.
1/ Ajouter une table de sortie.

| fonction | définition |
|---|---| 
| `StringHandling.LEN()` | taille d'une chaine de caractère |
| `lenght(varaible)` | nombre de caractère de la chaîne. |


Format | defintion |
---|---|
`Integer.parseInt(texte) | integer vers string |

## Les fonctions

### La condition SI

* `CONDITION ? VRAI : FAUX`

## Les formats

### Le texte

"texte" en java

### Les dates

| Code | Définition |
|---|---|
| `yyyy` | année |
| `MM` | mois
| `dd` | jour
| `HH` | heure
| `mm` | minute |

`colonne!=null && !"".equalsIgnoreCase(colonne)? TalendDate.parseDate("dd/MM/yyyy HH:mm", colonne) : null` instruction pour convertir un string en date avec des dates null.


