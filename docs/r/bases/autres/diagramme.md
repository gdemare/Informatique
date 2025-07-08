
### Diagramme

`library(DiagrammeR)`

DiagrammeR utilise le langage DOT pour les diagrammes.

!!! note
  Le pendant DiagrammeR en JavaScript est le mermaid.

### Modèle de données

`library(dm)`

``` R
grViz("
digraph shiny_app {
  graph [layout = dot, rankdir = LR]


  node [shape = box]
  input1 [label = 'Input: utilisateur']
  fun1 [label = 'fonction_input()']
  fun2 [label = 'calcul_pk()']
  output1 [label = 'Tableau résultats']

  input1 -> fun1 -> fun2 -> output1
}
")
```

- `rankdir = LR` alignement des éléments :
	- `LR` gauche à droite.
	- `TB` du haut vers le bas).


#### node 

- `fillcolor = limegreen, style=filled` remplir une forme d'une couleur [couleurs](https://rich-iannone.github.io/DiagrammeR/articles/graphviz-mermaid.html?q=color#colors)![image](https://github.com/user-attachments/assets/d3d46c00-e34f-4a3f-8b1d-0b4a74b290ee).
- `color = pink` couleur du contour.
- `shape = rect` forme.

| Valeur | Couleur |
|---|---|
| `Gold | jaune |
| `Coral | orange |
| `Orchid | violet |
| `Pink` | rose très clair |
| `LightBlue` | Bleu clair |
| `Paleturquoise` | bleu clair |
| `PaleGreen` | Vert clair |

[couleurs](https://rich-iannone.github.io/DiagrammeR/articles/graphviz-mermaid.html?q=color#colors)
  
| Valeur | Forme |
|---|---|
| `ellipse` | ellipse 
| `rect` | rectancle |
| `oval` | ovale |
| `cylinder`  | cylindre |
| `note`  | fichier |
| `diamond` | losange |
| `folder` | dossier |

### Modèle de données

[dm](https://dm.cynkra.com/)

