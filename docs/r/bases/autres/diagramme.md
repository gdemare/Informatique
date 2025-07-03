`library(DiagrammeR)`
# langage DOT pour les diagrammes son pendant javascript est le mermaid.

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
