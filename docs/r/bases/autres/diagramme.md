
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

- `fillcolor = limegreen, style=filled` remplir une forme d'une couleur [couleurs](https://rich-iannone.github.io/DiagrammeR/articles/graphviz-mermaid.html?q=color#colors)![image](https://github.com/user-attachments/assets/d3d46c00-e34f-4a3f-8b1d-0b4a74b290ee).
- `color = pink` couleur du contour.
- `shape = rect` forme.

| Valeur | Couleur |
|---|---|
| `Gold` | jaune |
| `Coral` | orange |
| `Orchid` | violet |
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
