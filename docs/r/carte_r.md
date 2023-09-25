## Les cartes
 
 Nécessite un compte [Google developper](https://console.developers.google.com).
 
### Obtenir la position géographique d'une adresse (lattitude et longitude) en requêtant Google Map
 
Soumettre la requête : `https://maps.googleapis.com/maps/api/geocode/xml?address=`ADRESSE`&key=`CLE

```
library(XML)
resultRequest = xmlTreeParse(readLines(REQUETE), useInternalNodes=TRUE)
root = xmlRoot(resultRequest)
lattitude = as.numeric(xmlValue(root[['result']][['geometry']][['location']][['lat']]))
longitude = as.numeric(xmlValue(root[['result']][['geometry']][['location']][['lng']]))
```

## Graphique with ggplot2

```
library(ggplot2)
mapWorld = borders("world", regions = "Malta")
ggplot() + mapWorld
```

* `coord_map()` garder un ratio entre longitude et lattitude (package `mapproj`).

## Graphique avec un fond de carte Google Map

Attention activer 

```
library(ggmap)

register_google(key = key)

# récupérer la lattitude and longitude d'un endroit
malta = as.numeric(geocode("Malta"))

# récupérer une carte sur google map (enable the static maps API on google cloud)
map = get_googlemap(center = malta, zoom = 11, scale=, maptype = "roadmap")

library(ggrepel)
googlegraph = ggmap(map) +
  geom_point(data = donnee, aes( x=long , y = latt, size=turnover, color=turnover)) + 
  geom_text_repel( data=donnee, aes(long,latt), label = donnee$name )
googlegraph
```
## Carte avec des fichiers shapefile : DBF, PRJ, SHP, SHX

Package : `rgdal`

* `readOGR(dsn = dossier, layer = debut_fichier, stringsAsFactors = F, encoding = 'UTF-8')`

## Spatial Polygon et Point DataFrame

### Importer un fichier GeoJson

Package : `rgdal`

* `readOGR("fichier.geojson", stringsAsFactors = F,encoding = 'UTF-8')`

### Manipuler les données SpatialPolygonsDataFrame

Package : `spdplyr `.

* Il s'utilise comme dplyr.

### Réaliser une carte avec tmap

Package : `tmap`.

Mode de carte `view` ou `plot` : `tmap_mode(mode)`

* `tm_shape(SpatialPolygonsDataFrame)` données à représenter.
* `tm_borders()` ajouter des frontières.
* `tm_fill()` remplir la carte.
* `tm_text("variable")` afficher du texte.
 * `ymod = absisse` décaler l'etiquette sur l'axe des abscisses.
 * `just="top/bottom/left/right"` position du texte. 
* `tm_dots()` afficher sous forme de points.
 * `size=taille` taille des points.

Paramètre :
* `alpha = 0.8` transparence.
* `col = couleur/variable` changer la couleur.
* `palette = "couleur"` changer la palette.

## Exporter le graphique

* `tmap_save(data, filename = "fichier.png")` exporter le graphique png, html.

### Personnaliser les couleurs

library `RColorBrewer`

`brewer.pal(nbNiveau, palette )` créer une palettes 

| code | couleur 1 | couleur 2 | couleur 3 |
|---|---|---|---|
| `YlOrRd` | jaune | orange | rouge |
| `YlOrBr` | jaune | orange | marron |
| `YlGnBu` | jaune | vert | bleu |
| `RdYlGn` | rouge | jaune | vert |

## Créer un fichier GeoJson

library `rgdal`

```
SpatialPointsDataFrame(longitute lattitude,autres variables)
### export au format GeoJson
writeOGR(data, 'fichier.geojson','nom couche', driver='GeoJSON')
```

## Changer le repère de projection

`spTransform(x = spatialPointsDataFrame, CRSobj = CRS )` changer de repère (package `sp`).

| CRS | résultat |
|---|---|
| `"+init=epsg:4326"` | en degré |

## Transformer un SpatialPolygonsDataFrame en DataFrame pour ggplot2

```
polyToGgplot2 = function(SpatialPoly){
  repere = spTransform(x = SpatialPoly, CRSobj = "+init=epsg:4326")
  fortifier = fortify(repere)
  repere@data$id = unique(as.numeric(fortifier$id))
  polyToGgplot2 = join(fortifier, repere@data, by="id")
  polyToGgplot2
}
```

## Leaflet

Ajouter des labels

`addLayersControl(group = groupe)` Ajouter une interface de choix de couche
Option :
 * `Options = layersControlOptions(collapsed = FALSE)` afficher les couches.
`addPolygons()` ajouter des polygones.
Option : 
 * `highlight = highlightOptions()` action lors du passage de la souris.
 * `labelOptions =

* ` addLegend(position, colors = , labels = , group = "mammals")` ajouter une légende. Pensez à la fonction `levels()` pour `colors` et `labels`.
Positions : 
* `"bottomleft"`

`addPolygons(fillColor = ~couleurs)`
 Option : 
  * `weight = nb` largeure des bordures.
  * `fillColor = couleurs` couleurs de remplissage.
  * `color = couleur` couleur des bordures.
  * `highlight = highlightOptions(options)` action en passant la souris.  
  * `label = etiquette`
   Paramètre : `labelOptions = labelOptions(options)`
   Options :
    * `style = list("font-weight" = "normal", padding = "3px 8px")`
    * `textsize = "15px"` taille du texte.
    * `direction = "auto"` direction du texte.
  * `fillOpacity = 0.2` pensez mettre la valeur à 0.6 
  Options :
   * `weight = largeur`
   * `bringToFront = TRUE`

### Simplifier les polygons

Package : `rmapshaper`

* `ms_simplify(SpatialPolygonsDataFrame)` simplifier les polygones (les contours des zones géographiques).
 * `keep=compression` taux de compression, par défaut `0.05`.
