# Tensorflow

### Couche

```
from tensorflow import keras
from tensorflow.keras import layers

model = keras.Sequential([
	tf.keras.Input(shape=(16,)),
	layer1,
	layer2,
	])
```

Les couches 
* `layers.Flatten()` transforme une matrice en vecteur.
    * `input_shape=(28,28)` ou `[1]`  taille des données en entrés. 
* `layers.MaxPool2D` pooling.
* `layers.Dense( units, activation= fonction)` couche la plus simple.  une couche. units correspond aux nombres de sorties.
Fonctions d'activation :
	* `relu`
	* `sigmoid` utile notamment pour renvoyer une probabilité pour les classificateurs binaires.
	* `softmax` renvoie la valeur la plus élevée (notamment pour les classificateurs avec plus de deux classes).
* `Conv2D(filters=64, kernel_size=3, activation="relu", padding='same')` couche convulsive.
* `layers.Dropout` remplace aléatoirement des valeurs par des zéros dans la matrice.

_Rmq :_ il est possible d'appler les fonctions d'activation par `tf.nn.fonction`.

`model.summary()` récapitulatif des couches du modèle.
`keras.utils.plot_model(model, show_shapes = True,expand_nested = True,dpi = 80)` graphique qui reprend la structure du modèle.

### Compiler

```
model.compile(
    optimizer=,
    loss='binary_crossentropy',
    metrics=['binary_accuracy']
)
```
Optimizer, le type de correction appliqué au modèle soit `'optimisateur'` ou, par exemple, `tf.keras.optimizers.Adam()`. Les algorythmes d'optimisation possibles sont :  `Adadelta`, `Adagrad`, `Adam`, `Adamax`, `Ftrl`, `Nadam`, `RMSprop`, `SGD`.
On peut spécifier la valeur de la correction des poids grâce à `epsilon=0.01`.

Loss, l'indicateur a prendre en compte améliorer le modèle : 
* `sparse_categorical_crossentropy` plusieurs classes.
* `categorical_crossentropy`
* `binary_crossentropy` deux classes.
* `mean_squared_error` minimise l'erreur au carré.

Metrics :
* `accuracy` AUC pour cela il faut un jeu de données de validation (fit avec `validation_data`).
* `binary_accuracy`

## Apprendre, évaluer et prédire

### Entrainer le modèle

`model.fit( ds_train, epochs=2 )` entrainer le modèle.
* `epochs=nbre` nbre de fois que l'on effectue l'optimisation sur les données d'entrainement pour ajuster les poids.
* `verbose=0/1` afficher les informations.
* `validation_data=donnée` ajouter des données de validations pour suivre la performance du modèle.
* `validation_split=0.8` marche pas.

### Evaluer le modèle 

`model.evaluate(données, valeurs)` évaluer le modèle.

* `history.params` renvoie les paramètres.
* `history.history` renvoie l'évolution des indicateurs.

### Prédiction ou prévision

`model.predict([])`

## Sauvegarder et importer un modèle

* `model.save(dossier_model)` exporter un modèle. L'extension `dossier_model.h5` permet de sauver le modèle dans un unique fichier.
* `keras.models.load_model('path/to/location/dossier_model')` importer un modèle.

### Lire les images 

tf.io :
* `read_file(image)`
* `decode_jpeg(image, channels=1)`

tf.image :
`resize(image, size=[height, width ])` redimensionner l'image.

`tf.squeeze(image).numpy()` 

Reformater l'image pour la rendre compatible avec tensorFlow
```
image = tf.image.convert_image_dtype(image, dtype=tf.float32)
image = tf.expand_dims(image, axis=0)
```

`tf.squeeze(image_filter)` reformater une image pour la rendre affichable.

```
conv_fn = tf.nn.conv2d
conv_fn(
    input=image,
    filters=kernel,
    strides=1, # or (1, 1)
    padding='SAME',
)
relu_fn = tf.nn.relu
image_detect = relu_fn(image_filter)
```

# Les données en entré

## Sans BatchDataSet  

`np.array(, type=float)`

Appliquer une tranformation au jeu de données


## tf.data.Dataset

Library : `keras.utils`

La méthode batch (lot) est le modèle de données le plus performant pour traiter ses données. Il fonctionne en lot de 32 fichiers réunis dans des liste.

* `donnee.take(1)` permet de sélectionner aléatoirement un lot.
* `donnee.shuffle(9)`
* `donnee = image_dataset_from_directory(dossier)` un dossier avec des images.

* Les étiquettes de données :
    * `labels='inferred'`
    * `label_mode='binary'`
* Création d'une 
    * `shuffle=True` par défaut les fichiers sont ajoutés aléatoirement.
    * `seed=1337` fixer la génération de l'aléatoire pour le mélange des données.
Autres :    
* `batch_size=32` nombre de fichier par lot. Par défaut 32. 
* `shuffle` 
_pas compris a quoi ca sert__
* `validation_split=0.8`
* `subset=training/validation` type de sous ensembles. Il faut créer un training et un validation.

* `donnee.class_names` donne le nom des classes.

* `donnee.take(nb)` créer un échantillon de nbx32 élements.
* `donnee.range(nb)` sélectionner un élément. Il peut être utile de fixer le seed pour obtenir le même élément à chaque fois.

`train, valid = tf.keras.utils.split_dataset( dataset, left_size=None, right_size=None, shuffle=False, seed=None )` séparer les données en deux jeux . !! fonction en cours de développement, il faut l'ajouter séparément!!.

### Les images

* `color_mode='rgb/grayscale/rgba'`

``` 
from keras.preprocessing.image import ImageDataGenerator
# apprentissage
training_datagen = ImageDataGenerator(rescale=1./255) # normalisation
train_generator = training_datagen.flow_from_directory(
    dossier,
    target_size = (150,150),
    class_mode = 'categorical' ou binary)
# validation
```

## Importation d'un dossier d'images

* `image_size=[128, 128]` prétraitement qui re.
* `interpolation='nearest'`
* `color_mode="rgb" ou "grayscale" ou "rgba"` reformater en entrée.

Afficher 9 images d'exemples avec les labels.

```
from matplotlib import pyplot as plt
class_names = train_ds.class_names
plt.figure(figsize=(10, 10))
for images, labels in train_ds.take(1):
    for i in range(9):
        ax = plt.subplot(3, 3, i + 1)
        plt.imshow(images[i].numpy().astype("uint8"))
        plt.title(class_names[labels[i]])
        plt.axis("off")
```
