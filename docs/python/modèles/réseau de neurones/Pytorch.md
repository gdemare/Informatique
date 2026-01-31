```
#test = pd.read_csv("test.csv", sep=",")
train = pd.read_csv("train.csv", sep=",")
survie = pd.read_csv("gender_submission.csv", sep=",")

x_val = train.loc[:, ["Survived", "Fare", 'Age']]
y_val = x_val.iloc[:,0]
x_val = x_val.drop('Survived', axis=1)
x_val.fillna(0, inplace=True)

class MyDataset(Dataset):
 
  def __init__(self,x_var, y_var):
 
    x=x_var.values
    y=y_var.values
 
    self.x_train=torch.tensor(x,dtype=torch.float32)
    self.y_train=torch.tensor(y,dtype=torch.float32)
 
  def __len__(self):
    return len(self.y_train)
   
  def __getitem__(self,idx):
    return self.x_train[idx],self.y_train[idx]

tenseur = MyDataset(x_val, y_val)

class ConvNet(torch.nn.Module):
    
    def __init__(self):
        super( ConvNet, self).__init__()
        self.fc1 = torch.nn.Linear(2, 1)

    def forward(self, x):
        x = self.fc1(x)
        return x


model = ConvNet()
print(model)
criterion = torch.nn.BCEWithLogitsLoss() # probabilité de la classe remplace le sigmoide. BCELoss
optimizer = torch.optim.Adam(model.parameters(), lr=0.1)

epochs = 100

train_losses = []
for a in range(epochs):

    y = tenseur.y_train.view(tenseur.y_train.shape[0], 1)
    output = model(tenseur.x_train)
    #
    optimizer.zero_grad()
    loss = criterion( output, y) # différence entre la valeur obtenue et la valeur prédite
    train_losses.append(loss.item()) # la valeur de l'indicateur.
    loss.backward()
    optimizer.step() # màj des poids

    # information sur le modèle tous les 10
    if a%10 == 0:
      sc = output.round()
      acc = sc.eq(y).sum() / float(y.shape[0])
      print( "loss :", loss.item(), "Accuracy :", acc )

# évolution du critère
graph_losses = range(1, len(train_losses)+1)
pl.plot(graph_losses, train_losses, ".-" )
```

### Installer pytorch

1. Installer [Anaconda](https://www.anaconda.com/products/distribution), la dernière version de python prise en charge est intégrer à l'installateur.
2. Sur le site pyTorch, installer via la commande en Administrateur.

`conda install package`

Ajouter le dossier au variable environnement `C:\ProgramData\Anaconda3\Library\bin`

NB : pour installer tensor flow `conda create -n tf tensorflow` puis `conda activate tf`

### Réseau de neurones

Library : `torch.nn`

* `Conv2d(channel entrée, channel sortie, noyau)` 
 * channel input : type de matrice en entrée 1= une couleur, 2 deux et 3 trois.
 * channel output : nombre de filtres appliqués.
* `Linear(input, output)` régression linéaire et neurones simples. Pour créer un réseau de neurones en utilisant un fonction d'activation. Pour avoir un réseau multicouche il faut ajouter plusieurs linéares.
* `Dropout(probabilité)` remplacer aléatoirement des valeurs par des zéros dans la matrice.

#### Pooling 

* `nn.BactchNorm1d(input)` normalise les données.
* `MaxPool1d(noyau)` pooling.
* `nn.functional.Softmax()` renvoie une somme égale à 1 (probabilité). Pour déterminer la colonne avec la plus grande probabilité il faut appliqué la fonction max.
* `valeur, position = torch.max(matrice, dim=1)` renvoie la valeur et la positon la plus élevée.

### Fonctions d'activation

Library `torch`

| Python | Fonction |
|---|---|
| `relu(x)` | relu |
| `max_pool2d(x)` | pooling |
| `sigmoid(x)` | sigmoïde |

### Fonction qui 

Library `torch.nn.functional`

| Python | Fonction |
|---|---|
| `Relu(x)` | relu |
| `max_pool2d(x)` | pooling |
| `Sigmoid(x)` | sigmoïde |
| `Softmax(x)` | softmax |

`x.view()` (comme reshape) redimensionner notre matrice. Exemple `x.view(x.size, -)` pour linéariser.

_Rmq :_ pour la classification en classe il faut en sortie un vecteur (pensez à utiliser la fonction view).

`torch.flatten()` transforme une matrice en vecteur.
`pool(x)`

### Fonctions d'optimisation

Les fonctions d'optimisation sont dans `torch.optim`

Fonction : `fonction( model.parameters(), learning_rate )`

| Fonction | Descritpion |
|---|---|
| `Adam()` | Adam algorithme |
| `MSELoss()` |  |
| `SGD()` | Stochastic gradient descent |
| BCE | Binary Cross Entropy |

### Critère

* `nn.CrossEntropyLoss()`
* `nn.BCELoss()`

### Les paramètres du modèle

```
for param in model.parameters():
    param.requires_grad()= False
model.fc = nn.Linear(entré,output)
```

### Transformer les données

`transforms.Compose([transformation1, transformation2])` transformation séquentiel de données.
`transforms.` library pytorch.transforms ?

| Fonction | Transformation |
|---|---|
| `Resize()` | redimensionner |
| `ToTensor()` | transforme en tenseur. |
| `Normalize(moyenne,écart type)` | normaliser les données |

### Les images

library `torchvision`   

```
model = ConvNet()

crit = nn.CrossEntropyLoss()
optimize = optim.Adam(model.parameters(), lr=0.001)

for epoch in range(epochs):
    for id, (data, targets) in enumerate(dataloader):

        scores = model(data)
        loss =  crit(scores, targets)

        optimize.zero_grad()
        loss.backward()

        optimizer.step() #mettre à jour les poids
```

## Torch vision 

Certains modèles ont été implémentés :
`resnet18(pretrained=T)` classification d'images (torchvision.models)  

## OCTR reconnaissance de caractères et de texte

Library `python-doctr`

## Notes à revoir

Créer des couches de neurones de façon récursive `nn.ModuleList()`

probabilité de mettre un zéro à  un neurone.

Je ne sais pas à quoi ca correspond.
model.
`.eval()`
`.train()`
`.state_dict()` renvoie la valeur des poids.

`loss.data` pour accéder à la valeur.

```
optimizer.zero_grad()
loss.backward()
optimizer.step()
```
