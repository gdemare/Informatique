`model_log <- glm(y_reel~., data = dt_train, family="binomial")` déclarer le modèle.

`summary(selection)` information sur la regression. Paramètres :

* `$formule` formule du modèle.

* `predict(model_log, dt_train, type = "link")` renvoier la valeur avant l'application de la fonction logit.
* `predict(fit_glm, train2, type = "response")`renvoier la probabilité d'appartenance.

## Graphique

``` py
# réaliser les predictions
glm_link_scores <- predict(model_log, dt_train, type = "link")
glm_response_scores <- predict(model_log, dt_train, type = "response")

score_data <- data.frame(link = glm_link_scores, 
                         response = glm_response_scores,
                         bad_widget = train2$FlagASV,
                         stringsAsFactors = FALSE)
# graphique
score_data %>% 
  ggplot(aes(x = link, y = response, col = as.factor(bad_widget))) +
  geom_point() + 
  geom_rug() + 
  ggtitle("Both link and response scores put cases in the same order") +
  xlim(-10, 10) + 
  theme_minimal()
```
