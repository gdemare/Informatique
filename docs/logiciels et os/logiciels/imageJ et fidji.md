
Objectifs du traitement d'images :
* Suivi de trajectoire.
* Identifier et classer les objets en fonction de leurs caractéristiques.
* Augmenter la visibilité des objets.

## Utiles

* `Help > Update... > Manage update sites` installer un pugins.

## L'image 

Le nombre de bit détermine le nombre de niveau de couleur (exemple : 8bits = 2^8 = 255).
La calibration d'une image est l'opération qui consiste à associer à un pixel une taille.

### Traitement des images en lot

La foncion Stack permet de traiter les images en lot `Image > Stacks > Image to stacks`. Il permet de :
* Appliquer le meme traitement à un lot d'images.
* Sauvegarder dans un seul fichier de type Tiff.

### La couleur

* Propriété de l'image `Image > Propeties`
* Niveau des gris : `Analyse > Histogramm`. Information 
  * `Mode : ` médian de gris.
* Séparer les canaux de couleurs `Image > Color > Spit image`
* Transformer une image en niveau de gris `Image > Type > 8bit`
* Inverser les couleurs `Edit > Inverse`
* Ajouter une échelle `Analyze > Set scale`
* Le contraste :
 * Normaliser le contraste (étaler la couleur sur toute la plage du specte). Cela revien à augmenter le contraste `Process > Enhance Contrat`
 * Ajuster le contraste `Image > Ajust > Brightness / Constrast`

## Les prétraitements de l'image : les filtres

### Le bruit 

Le numérique de l'image avec des filtres pour atténuer le bruit. Dans `Process > Filter`.

Rmq : il est intéressant d'appliquer plusieurs fois un filtre.

Généralement, on utilise un seul filtre.

Linéaire :
* Mean Filter (augmente le flou l'image).
* Gaussian respect mieux les contours (++).

Non linéraire :
* Median filter (++).
* Morphological filter.

### Binarisation de l'image
 
 Binarisation par seuillage.
 
* Seuillage manuelle `Image > Adjust > Threshold`
* Seuillage automatique `Image > Adjust > Auto threshold...`
* Méthode de binarisation `Process > Make binary`

#### Seuillage automatique

Les plus utilisés :

| Méthode de seuil | Définition | Avg/incon |
|---|---|---|
| Global thresholding | un seuil pour toute l'image | rapide  |
| Local adaptative thresholding | un seuil pour chaque pixel en fontion de son environnement | gourmand en ressources mais performant |

## Analyse des objets sur l'image

 Il faut de préférence binairanizer l'image avant d'appliquer des filtres sur les objets en blanc et fond en noir.
* `Analyse > Analyze Particles` analyser les objets par taille et par forme.
* `Process > Binary > Watershed` séparer des objets accolés.
* `Analyze > Set measurements` ?????????

## Transformation de Fourrier

Transformation de Fourier : `Process > FTT > FTT`
La transformation de Fourrier sert à :
* La détection de d'orientation spécifique notamment de l'astigmatisme. L'astigmatisme est une déformation de l'image par l'objectif.

## Filtres morphologiques

Plugin `morphology`

`Process > Morphology > Gray morphology`
Les filtres morphologiques servent notamment à :
* Extraire des caractéristiques.
* Supprimer le bruit.

Les filtres morphologiques sont des extracteurs de caractéristiques (voisinage - neighbordhood) :
* connexity 8 = carré
* connexity 4 = croix
* horizontal = ligne
* vertical = colonne

L'image :
* Erosion ???
* Dilation ??
* Opening ??
* Closure ???

### Apprentissage machine

Télécharger et ajouter le plugin `Plugins > Segmentation > Weka segmentation`
Lancer Weka `Plugins > Segmentation > Weka segmentation`
