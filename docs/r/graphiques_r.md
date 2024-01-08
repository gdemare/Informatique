## ggplot 2

`aes()` dans la fonction geom ou à l'extérieur.

### Une variable

```
g = ggplot() + theme_minimal() + aes(x)
```

!!! note
	Il y a la possibilité de sélectionner une colonne avec son nom en caractère `aes_string(x = "col")` ou `!!sym("col1")`.

Faire des groupes (dans aes) :

* `fill = var` remplissage.
* `color = var` contour. 

* `geom_histogram(<option>, binwidth = 5)` histogramme. Option :

	* `position = "fill"` empiler les éléments avec une hauteur normalisée.
  
* `geom_bar(<option>)` diagramme en barre. Option :

	* `position = "dodge"` positionner les éléments les uns à coté des autres `aes(..., fill = var)`.
	* `aes(var), position = "fill"` empiler les éléments avec une hauteur normalisée.
	* `aes(var), position = "stack"` empiler les éléments.
	* `stat = 'identity'` pour afficher deux varibles.

!!! note 
	`x = reorder(id_chaine, nb_couple), y = nb_couple` permet de trier les résultats.

* `geom_density()` répartition, densité, distribution.

Présentation :
	
* `coord_flip()` transformer en diagramme en barre horizontal.
* `alpha = 0.4` transparence du remplissage.

###  Deux variables

```
g = ggplot() + aes(x,y)
```

Type de graphique :

* `geom_boxplot()` boxplots (x=name, y=value).
* `geom_point(<option>)` nuage de points. Option :

	* `aes(colour = var)` colorier les points en fonction de var.
	* `aes(size = var)` dimensionner les points en fonction de var.
	* `shape = ` forme des points.

id  	| Forme
--------|------------
`15`	| carré plein
`21`	| cercle entrouré
`18`	| losange plein

Libellés :

* `geom_text_repel(aes(x,y), label = var)` ajouter des étiquettes de données (library ggrepel).
* `geom_label_repel(aes(x,y), label = var)` ajouter des étiquettes de données avec fond (library ggrepel).
* `geom_line(<option>)` courbe. Paramètres : 

 	* `aes(group = var)` une courbe pour chaque modalité de var.
	* `stat = 'count'` avec une seul variable.
	* `geom_col()` diagramme en barre avec la valeur des y. Pour classer les labels, il faut `reorder(label, valeur)` dans le `aes()`.
	* `lty = type` type de ligne (`dashed` pointillé; `dotdash` point pointillé, ).
  	* `lwd = épaisseur` épaisseur.
 	
* `geom_area()` coubre pleine.

## Autre 

* `geom_polygon(aes(x = long, y = lat, group = group))` tracer des polygones identifiés par un groupe (notamment pour les cartes). Option :

	* `fill = var` remplir les zones.

* `geom_hline(yintercept = valeur)` ligne hotizontale.
* `geom_vline(xintercept = valeur)` ligne veticale.
* `geom_abline(intercept = 0, slope = 1)` droites et fonctions linéaires.

## Thémes 

* `theme_void()` thème sans axe et graduation.
* `theme_minimal()` thème épuré.

## Présentation

* `ggtitle("titre")` titre du graphique.
* `xlab("titre")` titre de l’abscisse.
* `ylab("titre")` titre de l’ordonnée.
* `xlim(min, max)` taille de l'abscisse.
* `ylim(min, max)` taille de l'ordonnée.
* `coord_equal(ratio = 1)` garder un ratio abscisse/ordonnée.
* `labs(color = titre, fille = titre)` changer le titre de la légende (color ou filled dépendent dû type de coloration).
* `scale_color_discrete(labels = c("label 1", "label 2"))` modifier les valeurs des modalités de la légende (même chose avec `filled`).

## Créer des graphiques en fonction d’une variable

* `facet_grid(.~variable)` sur une ligne.
* `facet_grid(variable~.)` sur une colonne.
* `facet_wrap( ~variable)` en ligne et en colonne.

## Exporter le graphique

* `ggsave(plot=p, file="nom.extension")` exporter le graphique.

## Graphique interactif

* `ggplotly(graph)` rendre le graphique interactif (package `plotly`).

## Afficher une fonction

```
fonc = function(x, a){a * x**2}
p <- ggplot(data = data.frame(x = 0), mapping = aes(x = x))
p + stat_function(fun = fonc, args = list(a = 3)) + xlim(-5,5)
```

## Les couleurs à ajouté 

### Couleurs personnalisées

* `scale_colour_manual(couleurs)` changer la couleur.
* `scale_fill_manual(couleurs)` changer la couleur.

### Palette prête 

library : `RColorBrewer`

* `display.brewer.all()` afficher les palettes disponibles.

* `graph + scale_color_brewer(palette = "Dark2")`
* `scale_fill_brewer(palette)`

## Graphique avec plotly

package : `plotly``

`%>%` pour ajouter des options.

* `plot_ly(data, labels = ~categorie, values = ~valeur)`

### Supprimer la légende

```
layout(title = 'Répartition des espèces évaluées',
         xaxis = list(showgrid = FALSE, zeroline = FALSE, showticklabels = FALSE),
         yaxis = list(showgrid = FALSE, zeroline = FALSE, showticklabels = FALSE))
```

### Donuts et cambenbert

`add_pie(hole = 0.6)`

### Séries temporelles

`library(dygraphs)` pour des graphiques temporels.

## Matrice colorée

Library `corrplot`

* `corrplot(matrice, method = "color")` matrice de corrélation.

--------------------------------

## Graphiques rapides

* `plot(var1, <var2>)` graphique rapide. 

	* `type = 'h'`
 
 		* `h` histogramme.
   		* `l` courbe.
		* `p` points
		* `b` points et lignes.
		* `c` points vides et lignes.
		* `o` for overplotted points and lines
		* `s` escalier.
    	
	* `log = "y"` utiliser une échelle logarithmique.
 	* `labels = etiquette` etiquette.

* `boxplot(var)` boxplot.
* `barplot()` diagramme en barre.

Paramètres :

* `main = titre` titre.
* `sub = sous_titre` sous titre.
* `col =` couleur.

*`heatmap(data)` heatmap.

### Ajouter des éléments 

* `abline(v = vertical, h=horizontal, a =, b =)` ajouter une droite.
* `points(coordonée, pch = 16)` ajouter un point (pch=16 rond plein).

## Tracer une fonction 

### Afficher une fonction en 2D

* `curve(fonction, from = -5, to = 10)`  afficher une fonction en 2D.

### Afficher une fonction en 3D

```
z = outer(x, y, fonction)
graphique
```

* `contour(x, y, z, nlev = 10)` courbes de niveau.
* `persp(x, y, z, shade = 0.8, axes = T, ticktype = "detailed")` fonction en 3D.
