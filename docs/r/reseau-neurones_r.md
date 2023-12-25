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

* `layer_dense(units = 10, shape(nb_var), activation = 'linear')` couche normale.
    
Type: 

    * `activation = sigmoid/relu/linear` fonction d'activation.

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
  batch_size = 16, epochs = 200, verbose = 0
)
plot(history)
```

Ajouter un jeu de données de validation `validation_data = list(dt_x_train, dt_y_train)` ou `validation_split = 0.2`.

#### Evaluer et prédire

* `model %>% evaluate(dt_x, dt_y, verbose = 0)` évaluer le modèle.
* `predict(model, dt_x, verbose = 0)` réaliser les prédictions.

### Avec Net

`library(nnet)`

Deux façons de déclarer un réseau de neurones : 

* `nnet(data = , cible~variables, size = nb_couche, maxit = nb)` avec une variable cible.
* `nnet(matrice_x, matrice_y, size = nb_couche)` cette méthode permet de fournir une matrice a obtenir en résultat.

Paramètres :

* `size = nb` nombre de couches cachées.
* `maxit = nb` nombre d'itérations maximum.
* `trace = F` masquer l'affichage.
* `weights = poids` saisir les poids.

Sorites :

* `$n` structure du réseau (nbre de neurones par couches).
* `$nunits` nbre de neurones total. 
* `$wts` poids des neurones.
* `$value` valeur du critère d'évalution en prenant en compte la pénalité sur les poids.
* `$fitted.values` valeurs prédites obtenues sur le jeu d'apprentissage.
* `$residuals` résidus (différence entre la valeur réel et celle prédite) du jeu d'apprentissage.
* `$convergence` nombre d'itérations jusqu'a converger.

* `plotnet(model)` visualiser la structure du réseau (`library(NeuralNetTools)`).

## Prédiction 

`predict(modele, newdata = test, type = )` paramètres 
pour :
    * `type=` 

		* `class` renvoie la probabilité d'appartenance pour chaque classe
		* `raw` renvoie la modalité la plus probable.
