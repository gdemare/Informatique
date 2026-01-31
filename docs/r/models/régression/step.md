Algorimthe de selection automatique des variables

```
biggest <- formula(lm(score~.,cbind(Y_train, X_train))) # important pour la méthode forward
step(model, direction = "forward", scope = biggest)
```

`direction = "both"/"forward"/"backward"`