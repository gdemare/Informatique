Packages :  FactoMineR, factoextra, arules.

```
res.acm = MCA(pop.3, graph = F )

res.acm$eig
fviz_eig(res.acm) # histogramme des valeurs propres

res.acm$var
res.acm$ind

# + foncton résumé

fviz_mca(res.acm, repel = TRUE, c(1,2) )
facto_summarize(res.acm, element = "var", axes = 1:2)
```
