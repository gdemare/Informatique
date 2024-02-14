## Les opérateurs

Symbole		| Opération
------------|-----------------------
`+` 		| addition (`var += 1`)
`-` 		| soustraction
`*` 		| multiplication
`//` 		| division entière → a // b est le quotient de l'entier a par l'entier b
`/` 		| division avec des nombres flottants
`a ** b`	| puisance
`a % b`		| modulo (reste division euclidienne)
`abs(valeur)` | valeur absolue.

### Fonctions mathématiques 

* `range(nbre1, nbre2 <,pas>)` créer une liste de nombres (attention pour l'afficher il faut la convertir en liste `list()`).
* `np.linspace(val_min, val_max, nb)` renvoyer un tableau avec nb point de l'intervalle.
* `round(numeric, nb_decimal)` arrondir un nombre.
* `max(vecteur)` maximum.
* `min(vecteur)` minimum.
* `count(vecteur)` compter le nombre de valeurs.

#### Nombre aléatoire

Library : `random`

Générer une seule valeur

Fonction 			| Défintion
--------------------|-------------------
`randint(nb1,nb2)`	| nbre entier au hasard entre nb1 et nb2.
`random()` 			| nbre aléatoire entre [0;1].
`randrange(nbre)` 	| nbre entier aléatoire entre 0 et nbre.
`gauss(mu, sigma)` 	| nbre aléatoire par la loi normale.

* `random.suffle(list)` mélanger les éléments d'une liste.
* `random.choices(list, weights=liste_poids, k=nbre_element)` générer une liste avec des éléments particuliers et des poids.
* `np.random.randn(n)` générer n nombres aléatoires.

#### Fonction mathématique

Bibliothèque `math`

Fonction 		| Définition
----------------|----------------
`sin()`			| sinus
`cos()`			| cosinus
`tan()`			| tangente
`factorial()`	| factoriel
`exp()`			| exponentielle
`log()`			| logarithme


-----------------------------

## Numpy (matrice et vecteur)

### Créer une matrice

!!! warning 
	Attention il faut passer par `copy.deepcopy(tableau)` pour copier une valeur.

* `np.array(liste, )` créer un array.
* `np.asarray(matrice)` convertie un array.
* `np.arrange(1,10, pas)` créer une matrice avec une liste incrémentée.
* `np.empty([lignes,colonnes])` créer un array vide d'une certaine taille.
* `np.transpose(matrice)` transposer.
* `np.maxtrix(vec1, vec2)` matrice ligne 1=vecteur 1, ligne 2=vecteur 2. 
* `np.full((n,p), valeur)` créer une matrice de n, p dimension avec la valeur.
* `np.zeros(shape=(5,5))` matrice de zéro.
* `np.ones()` matrice de 1.
* `np.diag(vecteur ou matrice, position )` deux fonctions :

	* diagonaliser un vecteur en matrice la position indique la colonne où commencer la diagonalisation.
	* renvoie la diagonale.

* `np.reshape( donnee, (dimension) )` modifier les dimensions d'une matrice. Paramètres : 

	* `order='C'` préciser la facon de réordonnées les éléments. `'F'` 

* `np.resize()` modifier la dimension sans renvoyer d'erreurs si elles ne sont pas compatibles.
* `np.unique()` renvoie les valeurs uniques.
* `np.sign(nbre)` renvoie le signe.
* `np.loadtxt(fichier)` charger une matrice depuis un fichier (exemple `1	70	230`).
* `np.loadtxt("array.dat", tableau)` enregister un array dans un fichier.
* `np.concatenate((array1, array2), axis=1)` concaténer deux arrays.


Attributs associés à un array :

* `.shape` dimension (ligne, colonne,...)
* `.T` transposée.
* `.ndim` nombre de dimensions. 
* `.size` nombre d'éléments total.

#### matrice de booléen et remplacement de valeurs

* `tableau[condition]` renvoie une matrice booléenne (opérateur `|`, `&`,...)
* `tableau[condition] = nv_valeur` modifie la valeur uniquement lorsque c'est vrai.

### Sélectionner une valeur ou une plage

Deux méthodes pour sélectionner un élément ou une plage :

* `table[i,j]`
* `table[i][j]`

* `for i in array:` parcourir ligne par ligne un tableau (rmq, il peut être utile de transposer pour passer par colonne).

### Opération sur les valeurs

* `multiply(tableau, nbre, out=nouv_tableau)` multiplier les valeurs d'un tableau.
* `matmul(mat1, mat2)`produit matriciel.
* `np.dot(mat1, mat2)` produi matriciel.
* `add(5)` ajouter 5 à toutes les valeurs.
* `mat1 * mat2` produit des éléments à la même position.

Paramètres :

* `axis= 0/1` effectuer l'opération sur chaque ligne, colonne. 

Python	| Fonction
--------|----------
`std()` | écart type.
`mean()`| moyenne.
`max()` | maximum.

### Matrice carré

Dans le sous module `linalg`

* `inv()` inverser une matrice.
* `det()` déterminant.

* `eig()` valeurs propres et vecteurs propres :

	* `.` vecteurs.
	* `[1][0]` valeurs propres.

* `diag()` diagonsaliser la matrice.

### Insérer

* `np.append(data, vecteur)` ajouter un dernière colonne. 
* `np.insert( data, position, vecteur)` ajouter une colonne à une position particulière.

### Statistique

* `np.corrcoef(x, y)` coefficient de corrélation de Pearson.

### Fonctions mathématiques 

Fonction 			| Définition
--------------------|---
`np.log(x, base)`	| logarithme
`np.exp()` 			| exponentielle
