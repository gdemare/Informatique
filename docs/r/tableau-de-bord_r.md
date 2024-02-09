## Shiny

```
library(shiny)

ui <- fluidPage(...)

server <- function(input, output) {
    contenu
  }
shinyApp(ui = ui, server = server) #executer l'application
```

### Interface utilisateur

```
fluidPage(
  contenu
)
```

* `title = titre` titrer l'application
* `skin = couleur` theme utilisé.

### Shiny dashboard

`library(shinydashboard)`

`dashboardPage(éléments)` créer une page shiny dashboard.

#### Entête

`dashboardHeader(title = "titre", titleWidth = largeur)`

#### Menu

`dashboardSidebar(width = largeur, title = titre)`

Ajouter un onglet :

```
sidebarMenu(
        menuItem(text = "onglet", tabName = "onglet")
      )
```

#### Corps de la page

```
dashboardBody(
    fluidRow(contenu)
)
```

`tabItems(contenu)` page

```
tabItems(
  tabItem(tabName = onglet, contenuOnglet)
)
```
Créer un onglet. Parametres :

* `badgeLabel = nom, badgeColor = couleur` Ajouter un badge
* `disable = TRUE` desactiver la barre.

##### Contenu des onglets

###### Contenu non modifiable

!!! note
	Le contenu non modifiable est basé sur les balises hmtl.

Code           		| Type
--------------------|-----------------
`p("texte simple)`  | Texte simple.
`h1("titre 1")`     | Titre de hiéarchie 1.
 
###### Panneau de saisie

`mainPanel()` principale
`sidebarPanel()` saisie

Code            					| Type
------------------------------------|-----------------
`box()`         					| classique
`infoBox()`     					| texte statique
`tabBox()`      					| valeur
`valueBox()`   						| valeur dynamique
`modalDialog()`						| fenêtre pop up (ajouter un boutont `modalButton("Dismiss")`
`HTML("## markdown")`               | afficher du texte makdown directement
`renderMarkdown(fichier)`         	| afficher du texte markdown

* `showModal(modalDialog("Test"))`

Boîte avec un tableau. Arguments :

* `title = titre`
* `footer = pied de la page`
* `width = largeur`
* `color = couleur`


!!! example 
	Table box
	```
	tabBox(
	  title = titre,
	  tabPanel(title = "titre", tableOutput("nomTable"))
	) 
	```

!!! note
	Pour rendre une valeur dynamique avec valueBox sur server.
	```
	output$nom <- renderValueBox({  
	    valueBox(a completer)
	})
	```
 
###### zone de saisie

* `type(inputId = id, ....)`
* `input$id`

R                                                 | Type
--------------------------------------------------|-----------------
`actionButton()`                                  | bouton
`checkboxInput()`                                 | 
`checkboxGoupInput()`                             |
`dateInput()`                                     |
`dateRangeInput()`                                |
`fileInput("inputId", "label", multiple = FALSE)`    | importer un fichier
`numericInput()`                                  |
`paswordInput()`                                  | 
`colourInput()` (package `colourpicker`)          |
`radioButtons()`                                  |
`selectInput(choices = liste)`               	  | liste à choix multiples (liste de liste pour avoir des groupes)
`sliderInput()`                                   | barre de défilement
`textInput()`                                     |
`textAreaInput()`                                 | zone de saisie de texte.

Option :

* `inputId = id` id qui permet de récupérer la valeur.
* `label = 'titre'` texte a afficher.

### Server

```
server <- function(input, output) {
  output$nom <- resultat
}
```

!!! note
	Pensez à isoler une processus avec `isolate()` pour continuer à utliser l'application même lorsque des traitements sont en cours.

Les sorties doivent être stockées dans la variable

code server                       | rendu                     | code ui
----------------------------------|---------------------------|-------
`renderText({texte})`             | texte                     | `textOutput('variable')`
`renderPlot({graphique})`         | graphique                 | `plotOutput('variable')`
`renderTable({tableau})`          | tableau                   | `tableOutput('variable')`
`renderDataTable({dataFrame})` ou `renderDT()`   | donnees (package DT)      | `dataTableOutput('variable')` ou `DTOutput()`
`renderPlotly({graphique})`       | donnees                   | `plotlyOutput('variable')`
`renderPrint(variable)`           | variable                  |

Package `DT` Afficher un dataframe 

* `renderDataTable({dataFrame}, options = list(scrollX = TRUE))` si l'affichage depasse de l'écran.

#### Variable réactive

* `variable = reactive(valeur de la variable)` actualiser la rapport en fonction de la variable.
* `variable()` utiliser une variable réactive.
* `eventReactive(input$action, {variable})` réactive variable à la suite d'un évènement.

#### Liste interactive utilisant une variable réactive

```
ui :
  uiOutput("interaction_slider")
```

server :

```
  filterGenre <- reactive(genre)
  output$interaction_slider <- renderUI({
    selectInput("select", label = "Select box", 
                choices = as.list(genre)$genre_label, selected = 1)
```

### Selection sur un tableau

`library(DT)`

```
output$tableau <- DT::renderDataTable({ 
 instruction
})
input$tableau_rows_selected # indice des lignes selectionnées
```

## Déployer l'application sur le site Shinyapps

`selection = valeur` 

* `single` une seule ligne.

Requis la bibliothèque `rsconnect`

1. Découper le projet en deux fichiers : sever.R et ui.R.
2. Générer un jeton depuis le site [shinyapps](https://www.shinyapps.io) : Token. 

### Tester et déployer l'application

* `runApp()` tester l'application.
* `deployApp()` déployer l'application.

### Récupérer des données depuis une page Html vers R

* `session$clientData$url_protocol`

## Inserer des sorties R dans une page HTML

`ui = htmlTemplate(filename = "page.html", sortie1, entree1)`

!!! note
	Ajouter `server <- function(input, output, session) {`

`{{ sortie }}` dans le fichier HTML.

### Markdown

Library : `htmltools`

* `includeMarkdown("fichier.md")` insérer un fichier markdown.

-------------------

## Flexdashboard : site web dynamique à partir d'un fichie Rmarkdown

`library(flexdashboard)`

[Flexdashboard](https://rmarkdown.rstudio.com/flexdashboard/)

```
output: 
    theme: theme
```

Theme     | Couleur              | Commentaire
----------|----------------------|--------
default   | bleu                 |
bootstrap | gris blanc           |
cerulean  | bleu relief          |
journal   | saumon               | New time roman
flatly    | vert turquoise       | 
readable  | blanc                |
spacelab  | bleu blanc relief    |
united    | bordeau              |
lumen     | blanc                |
paper     | bleu                 | ++
sandstone | vert moche           |
simplex   | rouge                |
yeti      | bleu                 |

`runtime: shiny` intégrer du code shiny (nécessite un server shiny).

### Ajouter une box et des onglets

```
Column {data-width=600}` préciser la largeur de la colonne.
-------------------------------------
``` 
séparateur de colonnes/lignes. Lorsque l'on spécifie une largeur il faut 

```
Page 4 {data-navmenu="Menu B"}
=====================================
```
 Ajouter des pages de naviguations.

* `.tabset .tabset-fade` ajouter des onglets à une box.

### Afficher tableau et valeur box

* `knitr::kable(data)` Afficher une table
* `valueBox(comments, icon = "fa-comments")` ajouter une valeur box.


## Golem et testthat : organiser son code

library `golem`

La philosophie de Golem est d'organiser le code de son application comme un module.

ui.R

```
mod_bars_echarts_ui("bars_echarts_ui_1")
```

server.R

```
callModule(mod_bars_echarts_server, "bars_echarts_ui_1")
```

R/Mod_bars_echarts.R

```
mod_bars_echarts_ui <- function(id){
    ns <- NS(id)
    tagList( )
}

mod_bars_echarts_server <- function(input, output, session){
    ns <- session$ns
}
```
