Library : `torch`

Les tenseurs sont :

* un type de tableau spécialisé pour la modélisation qui sont optimisés pour les GPU.
* un type particulier de `numpy`. GPU beaucoup plus rapides. parallèle contre séquentiel bcp plus de coeurs.
* des tableaux mutlidimentionnels avec des opérations particulières.

### Utilisation de GPU

L'apprentissage sur les tenseurs peut être accélérer en utilisant la puissance des cartes graphiques.

`cuda.is_available()` Vérifier si le GPU peut être utilisé pour les calculs. Dans le cas où c'est le cas, il faut `tensor.to('cuda')`.

## Déclarer un tenseur

Il faut créer une classe avec les caractéristiques :

```
class donnee(torch.utils.data.Dataset):
    
    def __init__(self):
     	# déclarer les données en séparant données explicative et la variable à prédire.
        self.x = lot.get(clés[1])
        self.y = lot.get(clés[1])
        
    def __getitem__(self, index):
    	# renvoie les variables explicatives et celle expliqué
        return self.x[index], self.y[index] 
    
    def __len__(self):
    	# renvoie la dimension
        return len( self.x )
```

Library `torch.utils.data.`

* `train, test = random_split(dataset, [20000, 5000])` créer un jeu de test et d'apprentissage à partir d'un tenseur.
* `torch.utils.data.DataLoader(dataset = donnee())` transformer un data en tensor. Paramètres de DataLoader :

	* `batch_size=nbre` taille des lots.
	* `shuffle=True` répartir aléatoirement les individus.

### Convertir en tenseur

Library : `torch`

* `tensor(data)` convertie un numpy en tenseur.
* `data.numpy()` convertie un tenseur en numpy.
* `from_numpy()` convertie en tenseur.
* `ones_like(tenseur)` créer un tenseur de meme dimension.
* `rand_like(tenseur)` créer un tenseur de meme dimension avec des valeurs aléatoire.
* `rand(dimension)` exemple dimension = (2,3,) `ones()` avec des 1 avec des `zeros()` avec des 0.

Paramètre :

* `dtype=type` préciser le type de variable.

Type 			| Définition
----------------|--- 	
`torch.float`	| décimaux
`torch.int32`	| entiers 

* `tenseur.dtype` affiche le type de data de chaque champs du tenseur.
