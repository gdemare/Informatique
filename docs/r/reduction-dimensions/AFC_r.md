## AFC

```
res.afc = CA( table(var1,var2), graph = F)
```

## Interprétation

### Valeurs propres

```
res.afc$eig
fviz_eig(res.afc) 
```

### Profil ligne et colonne

```
res.afc$row
res.afc$col
```

### Projection

```
fviz_ca(res.afc, repel = T)
```
