## Normaliser les données

`from sklearn.preprocessing import StandardScaler`

```
sc = StandardScaler() # créer la fonction de normalisation
sc.fit_transform(data) # centre et réduit avec les paramètres  
sc.transform(data) # centre et réduit avec les paramètres précédent
```
