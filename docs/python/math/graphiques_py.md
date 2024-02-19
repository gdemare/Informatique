## ggplot2

`from plotnine as pln`

``` python
(
    ggplot(economics)  # What data to use
    + aes(x="date", y="pop")  # What variable to use
    + geom_line()  # Geometric object to use for drawing
)
```

* `geom_point()`
* `geom_histogram()`
* `geom_line()`
* ``
* ``
* ``
* ``

## Fenêtre et interface

* `fig = plt.figure(figsize=(25,20))`  changer la taille du graphique.
* `fig, axes = plt.subplots(nrows=1, ncols=3, figsize=(15,5))` sous diviser un graphique en plusieurs cases ou superposer deux graphiques (sans nrows/ncols).

!!! warning
	Dans ce cas indiquer l'argument : `ax=axes[i]` lorsqu'il n'y a qu'une ligne.

#### Subdiviser la fenêtre graphiques

Cela permet d'afficher plusieurs graphiques sur la même sortie (image).

``` python
fig, axes = plt.subplots(nrows=2, ncols=1)
graph_sans = pd.crosstab(data['ligne'], data['colonne'], normalize='index').plot.bar(stacked=True, ax=axes[0])
graph_avec = pd.crosstab(data['ligne'], data['colonne'], normalize='index').plot.bar(stacked=True, ax=axes[1])
```

A la fin, on peut forcer l'affichage avec `plt.show()`

## Pyplot graphiques 

`from matplotlib import pyplot as plt`

Utiliser le style de seaborn : `sns.set()`

* `plot(<x>, y, type_point)`

Paramètre : faire une chaîne de caractères

* L1 couleur `'r'` rouge `'y'` jaune `'b'` bleu
* L2 type de points :

	* `o` gros points
	* `.` petit points 
	* `^` triangle
	* `s` carré
	* `+` croix

* L3 type de lignes :

	* `-` ligne.
	* `--` pointillé.

!!! example
	`ro--` points rouges reliés par des traits en pointillé.

### Types de graphiques

* `plt.scatter(x,y)` nuage de points.
* `plt.bar(libelle, valeur, width=, align='edge')` Diagramme en barre et histogramme. Les libellés doivent être au format texte.
* `plt.pie(valeur, labels=, radius=)` camembert.

### Paramètres des axes

* `plt.show()` afficher le graphique.
* `plt.axis([xmin, xmax, ymin, ymax])` changer l'affichage des axes. 

	* `"off"` ne pas afficher d'axe. 	

* `plt.grid(True)` afficher une grille.
* `plt.xticks(rotation=45)` changer la rotation des étiquettes de données.
* `plt.yscale('log')` passer en échelle logarithmique. paramètre :
	* `base=2` changer la base

Masquer un axe :

``` python
ax = plt.gca()
ax.get_yaxis().set_visible(False)
```

### Etiquettes, libellés et titre

* `plt.xlabel(texte)` libellés de l'axe des abcisses.
* `plt.ylabel(texte)` libellés de l'axe des ordonnées.
* `plt.title(titre)` ajouter un titre.
* `plt.text(x, y, texte)` placer du texte n'importe ou dans la fenêtre.
* `plt.legend(loc='upper right')` position de la légende (légende à l'extérieur du graphique `plt.legend(bbox_to_anchor=(1.02, 1), loc='upper left', borderaxespad=0)`).

	* `title="titre"` titre de la box.

* `plt.grid()` afficher une grille.

### Ajouter plusieurs graphiques à une seule image

* `plt.figure('train', (largeur, hauteur))` créer une image subdiviser.
* `subplot(nb_lignes, nb_col, i+1)` ajouter un graphique à l'image. Les  positions sont numérotées à partir de 1.

### Autres

* `plt.boxplot(vecteur)` boxplot.
* `plt.matshow(mat_cor)` matrice de corrélation.
* `plt.fill_between(valeur_moyenne, valeur_dessus, valeur_dessous, color='b', alpha=0.2)` ajouter un intervalle d'erreur.

### Afficher une image

* `imshow(numpy)` Paramètre : 
	
	* `cmap='gray'` en valeur de gris.

``` python
plt.imshow(img)
plt.axis('off') # retirer les axes.
plt.show()
```

## Seaborn graphique

Library `import seaborn as sns`

Paramètres :

* `data=data` jeu de données.
* `hue='prot_diff'` mettre une couleur pour chaque groupe.
* `color=` couleur
 
Graphiques :

* `heatmap(protfreq, annot=True)` matrice de température. Paramètres :

	* `annot_kws={"fontsize":8}` taille des annotations.
	* `fmt='.0f'` changer le format des nombres (0 indique le nbre de décimals).

* `clustermap()`
* `histplot(vecteur)` afficher la distribution d'un vecteur quantitatif.

	* ` multiple="stack"`empiler les valeurs avec `hue="var"`.

* `ecdfplot(data, x='var')` le nombre d'effectifs cumulé.

   *  `complementary=True` inverser le cumule.

* `barplot()` diagramme en barre.

	* `orient=v/h` horizontal, vertical.

* `boxplot(x=valeur, y=groupe)` boxplot.
* `scatterplot(comm, x='CTR-PTROTAC', y='P3')` nuage de points.

	* `s=1` taille des points. 

* `lineplot(x=, y=)` lignes.	

### Superposer deux graphiques

Superposer deux graphiques :

``` python
fig, ax1 = plt.subplots()
sns.histplot(x=donnee['RT [min]'], ax=ax1)
ax2 = ax1.twinx()
sns.lineplot(x=x, y=y, color = 'r', ax=ax2)
```

### Faire plusieurs graphiques en fonction d'une condition

``` python
g = sns.FacetGrid(donnee, col="condition")
g.map(sns.histplot, "% ACN", binwidth=2).set(yscale='log')
```

#### Ajouter un élément au graphique

* `fig.axvline(1.25)` ou `fig.axhline(1.25)` ajouter une ligne verticale ou horizontale. Paramètres :
	
	* `linestyle=` type de lignes (`:` pointillé, `--` tiré ).

### Ajouter les étiquettes de valeurs sur le graphique 

``` python
bars = sns.graph(...)
for container in graph1.containers:
    bars.bar_label(container)
```

### Transformer des axes

* `graph.set_xscale()` changer le type d'axes (type : `log`, `symlog`, ...).
* `graph.get_xticklabels()` récupérer la valeur des axes.

### Modifier la présentation graphique

* `graph.set_xlabel("Colors")` changer le libellé de l'axe (`set_ylabel` pour y).
* `graph.set(xlabel='x-axis label', ylabel='y-axis label')` titre des deux axes.
* `graph.set_title("Colors vs Values")` ajouter un titre.
* `graph.set_xticklabels( fig.get_xticklabels(), rotation=45, horizontalalignment='right')` changer la rotation des libellés.
* `plt.xticks(valeur, libellé)` changer les libellés des axes.

## Enregister un graphique 

`graphique.get_figure().savefig('fichier.png')` enregistrer un graphique.

Si les libellés sont tronqués.

``` python
from matplotlib import rcParams
rcParams.update({'figure.autolayout': True})
```

## Diagramme de Venn

`from matplotlib_venn import venn2, venn3`

* `venn2(subsets=(10,5,2), set_labels =('Group A', 'Group B'))` diagramme de Venne avec deux groupes.
* `venn3(subsets=(10,8,22,6,9,4,2))` diagramme de Venne avec trois groupes.

##  Pandas graphiques

Les dataframe pandas intégrent directement des représentations graphiques.

`data.plot(x=, y=)`

Type de graphique :

* `area()` aire.
* `density()` fonction de densité.
* `line()` lignes.
* `pie()` camembert.
* `bar()` diagramme en barre.
* `barh()` diagramme en barre horizontal (`.sort_values()`) pour classer les données. Paramètres :

	* `stacked=True` empilé.

* `scatter()` nuage de points.
* `hist()` histogramme.

Paramètres : 

* `legend=False` enlever la légende
* `ax=` déterminer la position du graphique avec les fenetres subdivisées.
