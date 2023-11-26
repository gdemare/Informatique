### Avec TensorFlow et Keras

L'installation nécessite d'utiliser Python :

1. Installer Tensorflow dans un environnement condas.
2. Installer `keras` et `tensorflow`.
3. Charger les bibliothèques `library(keras)` et `library(tensorflow)`.
4. Choisir l'environnement à utiliser `use_condaenv(".../User/anaconda3/envs/env_tensorflow/")`.

#### Créer le modèle 

!!! warning
    Le modèle prend en entré uniquement des matrices `as.matrix()` ou des tenseurs.

```
model <- keras_model_sequential() %>%
    couche1(shape(nb_entré)) %>%
    couche2
```

Les types de couches :

* `layer_dense(units = 10, shape(nb_var), activation = 'linear')`couche normale.
    
Type: 

    * `activation = sigmoid/relu/linear`  fonction d'activation.

#### Fonction perte

```
model %>% compile(
  optimizer = optimizer_adam(learning_rate = 0.01),
  loss = 'mean_absolute_error'
)
```

#### Entrainer le modèle

```
history  <- model %>% fit(
  dt_x_train, dt_y_train,
  batch_size = 16, epochs = 200, verbose = 0,
  validation_split = 0.2
)
plot(history)
```

#### Evaluer et prédire

* `model %>% evaluate(dt_x, dt_y, verbose = 0)` évaluer le modèle.
* `predict(model, dt_x, verbose = 0)` réaliser les prédictions.

### Avec Net

`library(nnet)`

```
nnet(data= , cible~variables, size=nb_couche, maxit=nb)
```
Paramètres :
* `size=nb` nombre de couches cachées.
* `maxit=nb` nombre d'itérations maximum.

Option :

* `weights = poids` 

Valeur :

* `$wts` poids des neurones.
* `$value` value of fitting criterion plus weight decay term.
* `$fitted.values` the fitted values for the training data.
* `$residuals` résidus du jeu d'apprenissage.the residuals for the training data.
* `$convergence` nombre d'itérations.

## Prédiction 

`predict(modele, newdata=test, type=)`
`type=` :
* `class` renvoie la probabilité d'appartenance pour chaque classe
* `raw` renvoie la modalité la plus probable.
