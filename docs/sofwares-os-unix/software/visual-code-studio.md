[Recommandation pour R officiel](https://code.visualstudio.com/docs/languages/r)

### Terminal R

Pour un terminal avec les commandes colorées.

1. Installer `radian` (sur Ubuntu il faut passer par pipx pour installer radian `pipx pipx install radian`).

### Sortie graphique de R

1. Installer le package `install.packages("httpgd")`
2. Activer l'option dans les paramètres de l'extension R `R > Plot: Use httpgd`

### Paramétrer R markdown

0. Installer knitr, rmarkdown.
1. Dans les paramètres utilisateurs (Crtl + Shift + p) :
2. Rechercher `user settings (JSON)`
3. Ajouter/remplacer dans la section `"files.associations":`  `"*.Rmd": "rmd",` et `"*.rmd": "rmd"`

Changer l'interpréteur de ctrl+shift+P, `Pyhon : select Interpreter` 

### Copilot

Copilot est équivalent à une autocomplétion en plus puissant. Il prend en compte le contexte et les commentaires
du code pour proposer une solution.

#### Poser une question 

``` R
# q: What is the definition of the mean ?
# a:
```

