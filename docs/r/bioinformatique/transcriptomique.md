single cell arn seq
objectif est de caracteriser les populations cellulaires.

!!! warning
	En cours on a fait varier le nombre de clusters avec un vecteur de résolution puis on fait l'umap. Le nombre de groupes peut être determiner avec clustree.

`library(Seurat)`

1. Contrôle qualité
2. Normaliser les quantités ARN pour comparer les niveau d'expression. La quantité d'ARNm par gène est divisée par le quantité d'ARNm total par cellule. Les valeurs sont ensuite transformer avec une fonction `log` pour obtenir une distribution normale. Pour les gènes qui ne sont pas transcript, la valeur est mise à 0.
3. Choix des gènes. Tous les gènes n'apportent pas le même niveau d'information. Les gènes peu exprimés ne sont pas vraiment informatifs car ils ont tendance à diluer l'information sur les différences entre les types cellulaires. Dans les faits, on conserve les gènes avec la plus grand variabilité (écart-type) de transcript pour l'analyse.
4. Les gènes ont différents niveau d'expression et de distribution. La contribution des gènes est différentes si tu ne veux pas que l'analyse dépende des gènes hautement exprimé il faut les 
5. Réduction de dimension : permet de renforcer le signal d'expression entre les gènes.

### Contrôle qualité

Il faut retirer les cellules avec :

- trop de peu de gènes : cellules trop peu séquencées.
- trop de gènes : souvent des gouttes qui contiennent plusieurs cellules.
- trop d'ARNm souvent lorsqu'il y a plusieurs cellules fans la goutte `library(doublefinder`.
- trop de quantité de gènes mitochondriales : La plupart des ARN mitochondriaux ne contiennent pas  de queue ploy-A sauf en cas de stress cellulaire et de marqueur de mort cellulaire. max entre 5 et 10%.

Seurat format :

`seurat[["percent.mt"]] <- PercentageFeatureSet(seurat, pattern = "^MT[-\\.]")` calculer la quantité de gènes mitochondriales 

- __nFeature__ nombre de gènes 
- __nCount__ nombre d'ARNm.

`VlnPlot(seurat, features = c("nFeature_RNA", "nCount_RNA", "percent.mt"), ncol = 3)`

`pt.size=0` masquer les points.

`FeatureScatter(seurat, feature1 = "nCount_RNA", feature2 = "nFeature_RNA")` nuage de points des différents paramètres.

`seurat <- subset(seurat, subset = nFeature_RNA > 500 & nFeature_RNA < 5000 & percent.mt < 5)` filtrer les gouttes en fonction des différents paramètres.

!!! note
		On garde souvent les gouttes avec moins de 5% de ARNm mithochondriaux.
!!! note
	Il existe des outils qui permettent d'affiner les filtres pour ne garder que les gouttes avec 
#### Normaliser les données

`seurat <- NormalizeData(seurat)` normaliser les quantités

#### Sélection des gènes 
`seurat <- FindVariableFeatures(seurat, nfeatures = 2000)` sélectionner les n gènes transcrit avec un maximum de variabilité.

`top_features <- head(VariableFeatures(seurat), 20)` sélectionner les gènes la valeur de variabilité la plus importante.
`VariableFeaturePlot(seurat)` 
`LabelPoints(plot = plot1, points = top_features, repel = TRUE)` ajouter les noms des gènes avec les plus grands niveaux de variabilité transcriptomique.

### Mettre à l'échelle les données d'expression

`ScaleData(seurat)`
	- `vars.to.regress = c("nFeature_RNA", "percent.mt")` choix des variables à utiliser pour retirer les variations entre les gouttes.
 `SCTransform(seurat, variable.features.n = 3000)` la normalisation par log introduit des artéfacts zéro inflation. La méthode de régularisation par une négative regression binomial pour normaliser les données. Il y a aussi une étape aléatoire dans la transformation qui fait que les résultats obtenues sont différents à cahque exécution. Cette fonction peut permettre d'atténuer certains biais liés à la normalisation.

La variation est retiré en utilisant une ajutant un modèle linéaire
the number of detected genes/transcripts (nFeature_RNA / nCount_RNA), mitochondrial transcript percentage (percent.mt), and cell cycle related variables (see below).

!!! note
	Dnas un premier temps il n'est pas conseillé de faire une regression sauf si des sources de variations hétérogènes dominent.

### Réduction de dimensions

1. `seurat <- RunPCA(seurat, npcs = 50)` 
2. `ElbowPlot(seurat, ndims = ncol(Embeddings(seurat, "pca")))` afficher les valeurs propres.
Premier axe de vrai différence dans l'expression des gènes et l'autre différence du à l'aléatoire,
3. `PCHeatmap(seurat, dims = 1:20, cells = 500, balanced = TRUE, ncol = 4)` afficher les gènes qui contribut le plus à cahque composante.

### Réduction de dimension non linéaire pour la visualisation
Le problème de la réduction de dimensions est qu'il faut souvent garder plus de 10 axes se qui rend la visualisation compliqué méthode qui transforme les données pour les représenter et ocnserver ls t-distributed Stochastic Neighbor Embedding (t-SNE) and Uniform Manifold Approximation and Projection (UMAP)

##### TSNE

1. `tsne <- RunTSNE(seurat, dims = 1:20)`
2. `TSNEPlot(tsne)`
##### UMAP

1. `RunUMAP(seurat, dims = 1:20)`
2.  `UMAPPlot(seurat)`
!!! note 
	tSNE or UMAP conseillé. tSNE adapté au groupes distincts et UMAP perserves trajectory-like structure better when data contains 'continuum'
	
`FeaturePlot(seurat, c("MKI67","NES"), ncol=3, reduction = "tsne"/umap)` représenter les résultats avec la coloration pour l'expression de cahque gène.
### Classification non supervisée

compliqué d'appliquer une algo de classification car beaucoup de données;

on utilise généralemet graph-based community identification algorithm.

1. `seurat <- FindNeighbors(seurat, dims = 1:20)` Shared Nearest Neighbor (SNN)
2. `seurat <- FindClusters(seurat, resolution = 1)` la résolution est entre [0.1 et 1] 

Les résultats sont  The newest clustering result can be obtained by `Idents(seurat)` or `seurat@active.ident`. Other clustering results are also stored, as different columns in the meta.data slot (`seurat@meta.data`)

`DimPlot(seurat, reduction = "umap", label = TRUE)`

`DoHeatmap(seurat, features = ct_markers) + NoLegend()` afficher le heatmap.
	`FindAllMarkers(dt_kluster)` déterminer tous les marquerus.
`FindMarkers(pbmc, ident.1 = 5)` trouver les markers pour un groupe


### Klusters
nombre de groupes clustree on garde le nombre de kljsters qui limite l'echange de cellules entre les klusters.

permet de determiner la resolutions.

### Integration

faire correspondre les tyodes cellulaires entre les echantillons pour comparer les types en eux.

algorithme recommandé harmony.

#### Ressources
[scRNA anaylisis](https://github.com/quadbio/scRNAseq_analysis_vignette/blob/master/Tutorial.md) tutoriel Seurat pour l'analysis single cell.
