
### Diagramme

`library(DiagrammeR)`

[DiagrammeR](https://rich-iannone.github.io/DiagrammeR/) utilise le langage DOT pour les diagrammes.

!!! note
	Le pendant DiagrammeR en JavaScript est le mermaid.

``` R
grViz("
digraph shiny_app {
  graph [layout = dot, rankdir = LR]

 // commentaire
  node [shape = box]
  input1 [label = 'Input: utilisateur']
  fun1 [label = 'fonction_input()']
  fun2 [label = 'calcul_pk()']
  output1 [label = 'Tableau résultats']

 A -> B 
 A -> {B1 B2}
}
")
```

- `rankdir = LR` alignement des éléments :
	- `LR` gauche à droite.
	- `TB` du haut vers le bas).
- `A -> B [style = dashed, label = '', color = "red"]` personnaliser le lien.

!!! note
	Pour utiliser plusieurs éléments le même élément il faut créer plusieurs éléments avec des id différents mais avec le même label.

#### node 

- `fillcolor = limegreen, style=filled` remplir une forme d'une couleur [couleurs](https://rich-iannone.github.io/DiagrammeR/articles/graphviz-mermaid.html?q=color#colors).
- `color = pink` couleur du contour.
- `shape = rect` forme.

| Valeur | Couleur | hexadécimale |
|---|---|---|
| `Gold` | jaune | #ffd700 | 
| `grey` | gris| #c0c0c0 |
| `Coral` | orange | #ff7f50 |
| `Orchid` | violet | #da70d6 |
| `Pink` | rose très clair | #ffc0cb |
| `LightBlue` | Bleu clair | #add8e6 |
| `Paleturquoise` | bleu clair | #afeeee | 
| `PaleGreen` | Vert clair | #98fb98 |
| `tan` | marron clair | #d2b48c |

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

#### Enregistrer en image

`library(rsvg)` et `library(DiagrammeRsvg)`

``` R
diagramme %>% export_svg %>% charToRaw %>% rsvg_svg("graph.svg")
```

#### Shiny

- `renderGrViz({grViz("")})` server.
- `grVizOutput(id, heigth)` ui.

### Modèle de données

`library(dm)` [dm](https://dm.cynkra.com/)

- `new_dm(list)` créer un modèle de données.
- `dm_add_pk(table = table, columns = col)` déclarer une clé primaire.
- `dm_add_fk(ref_table = df_group, table = df_subject, columns = idPk_group)` déclarer une clé secondaire. 
- `dm_enum_pk_candidates(table = df_group)` lister les colonnes qui peuvent servir potentielement de clé primaire.
- `dm_draw(view_type = "all")` afficher le modèle de données :

	- `all` afficher toutes les colonnes.
	- `keys_only` afficher uniquement les colonnes déclarées comme clés.
