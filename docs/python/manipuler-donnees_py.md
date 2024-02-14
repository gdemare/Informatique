Package `import pandas as pd`

`data.fonction_()` l'underscore indique que le résultat remplace les données de départ.

Trois types principaux de strucutres de données : 

* les dataframes avec Pandas as pd.
* les matrices et les vecteurs avec Numpy as np.
* les tenseurs (jeux de données pour les modèles)  Pytorch ou Tensor.

`map(fonction, list)` appliquer une fonction aux élements d'un vecteur. Renvoie un objet de type map qu'il faut généralement le convertir en liste.

!!! example
	`map( ma_fonction, liste)` la fonction est sans parenthèse.

## Les fichiers

### Importer 

* `pd.read_csv(fichier, sep="\t")` lire un fichier csv.
* `pd.read_excel(fichier, sheet_name=1/feuille)` lire un fichier excel.
* `pd.ExcelFile(excel)` sinon pour importer un fichier et récupérer des informations.
	
	* `.sheet_names` renvoie le nom des feuilles d'un fichier Excel. 

Paramètres :

* `index_col="colonne"` colonne de l'index.

### Exporter 

* `tableau.to_csv('fichier.csv', sep='separateur')` exporter un data en csv.
* `tableau.to_excel('fichier.xlsx', sheet_name="feuill")` exporter un data en excel.

Paramètres :

* `index=False` les index.
* `header=True` nom des colonnes.

Pour exporter dans plusieurs feuilles, il faut installer `pip install xlsxwriter`.

``` python
writer = pd.ExcelWriter(fichier, engine='xlsxwriter')
	input.to_excel(writer, sheet_name="feuille1", index=False, header=True)
	input.to_excel(writer, sheet_name="feuille2", index=False, header=True)
```

## Dataframe

### Déclarer un dataframe

* `pd.DataFrame({ "col1" : valeurs, 'col2' : valeurs})` créer un data frame à partir d'un dictionnaire. Vide lorsqu'il n'y a pas d'arguments. Paramètres :
  
	* `index=nom_lignes` 
	* `column=nom_colonnes`

* `pd.DataFrame(columns=, index=, tableau_valeurs)` créer un dataframe.
* `dataframe.astype({'Survived': 'float'})` déclarer (à vérif) ou changer le type de variable d'un data frame.
* `data = pd.DataFrame(columns=['chemin', 'fichier', 'extension'])` créer un dataframe vide.
* `data_copy = data.copy()` copier un dataframe dans une autre variable. Attention sinon cela créer des dataframes liés.
* `pd.to_datetime("colonne")` convertie une colonne en date.
* `pd.Series(vecteur, index=)` créer une série (jeu de données avec une colonne).
* `data["nouvelle"] = valeur` ajouter directement.
* `tableau.assign(nomCol=valeur )` ajouter une nouvelle colonne. Pour appliquer des fonctions, il faut utiliser la library numpy.
* `df.insert(position, 'col_name', [value1, value2, value3, ...])` insérer une colonne à une position. Enregistre automatiquement la colonne de faire =.
* `colonne = pop("columne")` sauvegarde la colonne dans une variable et la supprime du dataframe.

### Attribut et types de variables

* `type(objet)` renvoie le type d'objet. Pour l'utiliser dans des conditions, on utilise généralement  `is type` . 
* `vecteur.astype(type)` changer le type d'un vecteur ou d'un tableau (type : `int`, `str`).

Fonction  			| Définition
--------------------|---
`str()` 			| convertie en caractère
`list()` 			| convertie en liste
`variable.decode()` | de bytes à normale (byte est signalé par un b avant la valeur.)

* `donnee.dtypes` renvoie le type de données de chaque colonne.
* `donnee.index` nom des lignes.
* `donnee.columns` nom des colones (`data.columns.values` pour ne récupérer que les valeurs et pour renommer les colonnes) .
* `donnee.head()` renvoie les premières lignes du pandaframe.
* `donnee.describe()` tableau récapitulatif des données (moyenne, médiane, écart type,...). Les valeurs manquantes ne sont pas prises en compte.
* `donnee.info(memory_usage="deep")` affiche une description poussée du dataframe. 
* `stack(niveau)` modifier les niveaux de données.

créer un jeu de données aléatoire.
```
index = [np.random.randint(0,len(data)) for i in range(5000)]
export = data.iloc[ index,: ]
```

### Sélectionner et extraire des données

* `tableau['colonne']` sélectionner une colonne.
* `tableau[['col1', 'col2]]` sélectionner plusieurs colonnes.
* `tableau[num_ligne]` sélectionner une ligne (fonctionne avec `debut:fin`).
* `tableau.iloc[nb_row, <nb_col>]` sélectionner en fonction du numéro des lignes et du numéro des colonnes.
* `tableau.loc[nb_row, <nom_col>]` sélectionner en fonction du numéro des lignes et du nom des colonnes.
* `for i in data.index:` parcourir un dataframe grâce à l'index.
* `for index, row in df.iterrows():` parcourir un dataframe en récupérant directement les valeurs.

!!! note 
	`:` permet de sélectionner tous ce qui se trouve avant ou après (ex : `2:` est équivalent à 2 et après).

* `data.loc[len(data)] = ["test1", "test2", 'test3']` ajouter une ligne de données.

### Filtrer

* `.drop(colonnes, axis=1)` supprimer une colonne.
* `.sort_values(colonne, ascending=T)` classer les données.
* `.reset_index()` changer l'ordre naturel des lignes.
* `.unique()` liste des valeurs pour une colonne.
* `value_counts()` permet de renvoyer le nombre de lignes uniques.
* `colonne.str.contains("mot")` contient le mot. Paramètres :

	* `na=none` ? valeur a renvoyer lorsque la recherche n'a pas été trouvée ?(False).
 	* `case=False` Prendre en compte la caste.	 

* `data[data["colonne"]==True]` filtrer les données en fonction d'une condition. S'il y a plusieurs conditions, il faut les mettre entre parenthèses.
* `data[ data['colonne'].isin(['KO_EF_01', 'KO_EF_02', 'KO_EF_03']) ]` in pour les conditions dans un tableau.
* `data.nsmallest(30, 'p value')` top des valeurs les plus faibles.
* `data.nlargest(30, 'p value')` top des valeurs les plus élevées.
* `vecteur.notnull() / .notna()` valeur non nulle 'nan' et none.
* `filter(valeur, axis=1)` filtrer par l'index ou le nom des colonnes.

	* `regex='e$'` filter en fonction d'une expression régulière.

### Recoder les données

* `.str.rsplit(séparateur)` sépare une chaine de caractères. Paramètres :

	* `expand=True` créer une variable pour chaque séparation.

* `data[condition] = valeur` remplacer les valeurs vraies pour la condition. 
* `.fillna(0)` remplacer les valeurs manquantes.
* `.drop_duplicates(keep='last')` supprimer les doublons.
* `.rename(columns=/index={"ancien" : "nouveau"})` renommer une colonne (ou `.columns.values=[col1, col2]`). Paramètres :

	* `inplace=True` pour remplacer les données.
	* `.set_index('colonne', inplace=True)` mettre une colonne comme indexer les données
   
Autres fonctions :
* `.apply(fonction, axis=1)` appliquer une fonction sur les données. Rmq pour ajouter la colonne il faut passer par `tableau["colonne"] = `.

!!! example
	Fonction apply :
 
	``` python
	def present_fct(row):
		if row>7:
			value= 1
		else :
			value=0
		return value
	```

#### Discrétiser

* `pd.cut( vecteur, bins=range(0, 150, 10) )` discrétiser une variable en fonction d'intervalles.
* `pd.qcut(variable, nb_groupe)` discrétiser une variable en créant des groupes d'effectifs uniformes.

	*  `duplicates='drop'` supprime les intervalles redondants.

#### Les intervalles 

* `interval(left, right)` déclarer un intervalle.

	* `intervalle.right/.left` récupérer la valeur.

#### Les dates

* `pd.Timestamp('2017-01-01T12')` convertir un texte en date.
* `pd.to_datetime(data_new['date'])` convertir une colonne en date.

Récupérer les inforamtions sur une date : `datetemps.<>`

Python 			| Définition
----------------|--------------
`.day_name()`	| jour de la semaine 
`.month`		| num du mois
`.year`			| année
`.day`			| num du jour


## Analyser et grouper les données

Fonction 			| Définition
--------------------|---
`.count()`			| nombre de lignes
`.median()`			| médianes
`.mean()` 			| moyenne
`.max()`			| maximum
`.min()`			| minimum
`.std()`			| écart type
`.size()`			| nombre de lignes
`.value_counts()`	| tableau effecitf par modalité `normalize=True` renvoie les %
`.nunique()` 		| nbre de valeurs uniques
`.sum()` 			| somme

### Grouper les données

* `.groupby(["colonne"])` grouper par.
* `.resample("A")` grouper par année.
* `.rolling(window=7)` définir une fenêtre qui se déplace (exemple, pour les moyennes mobiles).

Il est également possible d'utiliser les fonction sans grouper les données. Paramètres :

* `axis=0/1` en fonction de la colonne/ligne.

### Tableau croisé

* `pd.crosstab( ligne, colonne)` faire un tableau croisé avec deux variables avec la possibilité de calculer la proportion.

	* `normalize='all'/'index'/'columns'` calcul les fréquences.

* `pivot(data, columns='country', values='quantity', index='fruit')` faire un tableau crois sans fonction d'aggrégation. Il faut s'assurer que la transformation ne permet d'obtenir d'une ligne par index. Paramètres :

	* ` margins = True, margins_name='Total'`ajouter une ligne totale.

* `pivot_table(data, columns='country', values='quantity', index='fruit', aggfunc='sum')` faire un tableau croisé avec fonction d'aggrégation (possibilité d'appliquer plusieurs fonctions avec `["max", "min"]`).

* `tableau_croise.reset_index()` transformer un tableau croisé en tableau.
* `melt(data, id_vars='fruit', value_vars=colonnes)` transformer plusieurs variables en une seule.
* `columns.get_level_values(level)` récupérer les valeurs de l'index dans le cas de plusieurs sous catégories.
* `agg(['mean', 'min']))` calculer des indicateurs pour plusieurs colonnes ou lignes.

### Jointure 

* `pd.merge(gauche, droite, how=type_jointure, on=clé)` joindre deux tables. Paramètres :

	* `how=inner/left/right/outer/cross`  outer	est union (ou) et inner est intersection (et).
	* `left_on/right_on=colonne` id de la jonction.
	* `left_index/right_index=True/False` si la clée l'index. 

* `pd.concat([jointure, nvdf])` concaténer deux tableaux par colonne ou par indice. Attention les dataframes sont à déclarer sans "". Paramètres :

* `axis=1` fusionner par ligne (même index).
* `join="type"` type de jointure.

Vérifier les propriétés d'une colonne :

* `pd.api.types.is_numeric_dtype(colonne)` c'est numériques ?
* `pd.api.types.is_string_dtype` c'est un chaine de caractère ?

### Graphiques

Library `import matplotlib.pyplot as plt`

* `tableau.plot(x='col1', y='col2')` afficher un graphique.

## Autres

### Statistique

* `data.corr()` matrice de corrélation.
* `data.cov()` matrice de covariance.

### Standariser les données 

`import sklearn.preprocessing`

* `preprocessing.StandardScaler().fit_transform(comparatif)` standariser les données _Attention la standarisation a lieu par colonne (transposer)_ .
* `preprocessing.Normalizer(norm='l1').fit_transform(data)` normaliser les données.
