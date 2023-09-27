## Une variable

```
g = ggplot() + theme_minimal() + aes(x)
```

* `geom_histogram(<option>, binwidth = 5)` histogramme.
Option :
  * `aes(fill = var)` ajouter une variable.
  * `position = "fill"` empiler les éléments avec une hauteur normalisée.
  
* `geom_bar(<option>)` diagramme en barre.
Option :
  * `position = "dodge"` positionner les éléments les uns à coté des autres `aes(...,fill = var)`.
  * `aes(var), position = "fill"` empiler les éléments avec une hauteur normalisée.
  * `aes(var), position = "stack"` empiler les éléments.
  * `stat = 'identity'` pour afficher deux varibles.
Présentation :
* `coord_flip()` transformer en diagramme en barre horizontal.

### Deux variables

```
g = ggplot() + aes(x,y)
```

Type de graphique :

* `geom_boxplot()` boxplots.
* `geom_point(<option>)` nuage de points. Option :
	* `aes(colour = var)` colorier les points en fonction de var.
	* `aes(size = var)` dimensionner les points en fonction de var.
	* `shape = ` forme du point.

| id | forme |
|---|---| 
| 15 | carré plein |
| 21 | cercle entrouré |

Libellés :

* `geom_text_repel( aes(x,y), label = var )` ajouter des étiquettes de données (library ggrepel).
* `geom_label_repel( aes(x,y), label = var )` ajouter des étiquettes de données avec fond (library ggrepel).
* `geom_line(<option>)`
  * `aes(group = var)` une courbe pour chaque modalité de var.
  * `stat='count'` avec une seul variable.
  * `geom_col()` diagramme en barre avec la valeur des y. Pour classer les labels, il faut `reorder(label, valeur)` dans le `aes()`.
* `geom_area()` coubre pleine.

## Autre 

* `geom_polygon( aes(x=long, y=lat, group = group)` tracer des polygones identifié par un groupe (notamment pour les cartes).
Option : 
	* `fill = var` remplir les zones
* `geom_hline( yintercept = valeur )` ligne hotizontale
* `geom_vline( xintercept = valeur )` ligne veticale.

## Thémes 

* `theme_void()` théme sans axe et graduation.
* `theme_minimal()` théme épuré.

## Présentation

* `ggtitle("titre")` titre du graphique.
* `xlab("titre")` titre de l’abscisse.
* `ylab("titre")` titre de l’ordonnée.
* `xlim(min, max)` taille de l'abscisse.
* `ylim(min, max)` taille de l'ordonnée.
* `coord_equal(ratio=1)` garder un ratio abscisse/ordonnées.
* `labs(color = titre, fille = titre )` changer le titre de la légende.

## Créer des graphiques en fonction d’une variable

* `facet_grid(.~variable)` sur une ligne.
* `facet_grid(variable~.)` sur une colonne
* `facet_wrap( ~variable)` en ligne et en colonne.

## ordonner la variable a afficher

`reorder(variable, )`

## Exporter le graphique

* `ggsave(plot=p, file="nom.extension")` exporter le graphique.

## Graphique interactif

* `ggplotly( graph )` rendre le graphique interactif (package plotly).

## Afficher une fonction

```
fonc = function(x){test(x)/x}
p <- ggplot(data = data.frame(x = 0), mapping = aes(x = x))
p + stat_function(fun = fonc) + xlim(-5,5)
```

## Les couleurs à ajouté 

### Couleurs personnalisées

* `scale_colour_manual(couleurs)` changer la couleur 
* `scale_fill_manual(couleurs)` changer la couleur

### Palette prête 

library : `RColorBrewer`

* `display.brewer.all()` afficher les palettes disponibles.

* `graph + scale_color_brewer(palette="Dark2")`
* `scale_fill_brewer(palette)`

## Graphique avec plotly
package : plotly

%>% pour ajouter des options.

* `plot_ly(data, labels = ~categorie, values = ~valeur)`

### Supprimer la légende

```
layout(title = 'Répartition des espèces évaluées',
         xaxis = list(showgrid = FALSE, zeroline = FALSE, showticklabels = FALSE),
         yaxis = list(showgrid = FALSE, zeroline = FALSE, showticklabels = FALSE))
```

### Donuts et cambenbert

```
add_pie(hole = 0.6)
```

### Séries temporelles

`library(dygraphs)` pour des graphiques temporels


