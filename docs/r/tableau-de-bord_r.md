## Shiny

``` R
library(shiny)
library(shinydashboard)

ui <- fluidPage(
  interface
)

server <- function(input, output) {
    contenu
  }
shinyApp(ui = ui, server = server) #executer l'application
```

### UI

Paramètres :

* `title = titre` titrer l'application
* `skin = couleur` theme utilisé.


* `dashboardHeader(title = "titre", titleWidth = largeur)` entête.
* `dashboardSidebar(width = largeur, title = titre)` menu à gauche.
* `dashboardBody()` corps de la page.

#### Les onglets

* `sidebarMenu(menuItem(text = "onglet", tabName = "onglet"))` ajouter dans le menu.
* `tabItems(tabItems(tabName = onglet, contenuOnglet))` ajouter dans le corps.
Parametres :

	* `badgeLabel = nom, badgeColor = couleur` Ajouter un badge
	* `disable = TRUE` desactiver la barre.


##### Agencement

* `fluidRow(contenu)` 

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
`modalDialog()`						| fenêtre pop up (ajouter un bouton `modalButton("Dismiss")`)
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
`fileInput(nomFicher, text, multiple = FALSE)`    | importer un fichier
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

``` R
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

* `variable = reactive(valeur)` actualiser la rapport en fonction de la variable.
* `variable()` utiliser une variable réactive.
* `eventReactive(input$action, {variable})` réactive variable à la suite d'un évènement.

#### Liste interactive utilisant une variable réactive

``` R
ui :
  uiOutput("interaction_slider")
```

server :

``` R
  filterGenre <- reactive(genre)
  output$interaction_slider <- renderUI({
    selectInput("select", label = "Select box", 
                choices = as.list(genre)$genre_label, selected = 1)
```

### Dataframe

#### DT

`library(DT)`

* `DT::renderDataTable({instruction})`
* `input$tableau_rows_selected` indice des lignes selectionnées.

#### Flextable

## Shinyapps

`library(rsconnect)`

1. Découper le projet en deux fichiers : sever.R et ui.R.
2. Générer un jeton depuis le site [shinyapps](https://www.shinyapps.io) : Token. 

### Données sessions

* `session$clientData$url_protocol`

## Inserer fichier 

* `ui = htmlTemplate(filename = "page.html", sortie1, entree1)` insérer un html.
* `includeMarkdown("fichier.md")` insérer un fichier markdown (`library(htmltools)`).

-------------------

## Flexdashboard

Flexdasboard permet de créer des tableaux de bord site web dynamique à partir d'un fichie Rmarkdown

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

``` R
Column {data-width=600}` préciser la largeur de la colonne.
-------------------------------------
``` 
séparateur de colonnes/lignes. Lorsque l'on spécifie une largeur il faut 

``` R
Page 4 {data-navmenu="Menu B"}
=====================================
```
 Ajouter des pages de naviguations.

* `.tabset .tabset-fade` ajouter des onglets à une box.

### Afficher tableau et valeur box

* `knitr::kable(data)` Afficher une table
* `valueBox(comments, icon = "fa-comments")` ajouter une valeur box.

## Golem

`library(golem)`

La philosophie de Golem est de créer et organiser en appelant des fonctions :

Méthodes alternatives pour appeler un module en lui fournissant un paramètre : `callModule(mod_bars_echarts_server, "bars_echarts_ui_1")`.