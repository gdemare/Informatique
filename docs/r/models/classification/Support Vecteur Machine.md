`library(e1017)`
 
## SVM linéaire
 
`svmlin = svm(Species ~ ., data = iris, kernel = "linear", probability = TRUE, cost = 1)`

* `kernel = type` type du noyau ( `linear`, `polynomial`).
* `cost = 1`
* `degree = 2` nombre de degrés.
* `cross = 10` par validation croisée.
* `gamma = 1`

`summary(svmlin)`

## Coefficient et erreur moyenne

```
svmlin$coefs
mean(svmlin$fitted != iris[,"Species"]) # 0.2003106
```
