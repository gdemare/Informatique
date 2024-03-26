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

#### Affichage

!!! note
	Le contenu non modifiable est basé sur les balises hmtl.

Code           		| Type
--------------------|-----------------
`p("texte simple)`  | Texte simple.
`h1("titre 1")`     | Titre de hiéarchie 1.

#### Zone de saisie

* `type(inputId = id, ....)`
* `input$id` récuperer l'entré. Utile notamment dans la partie server.

Les différentes méthodes pour :

Option :

* `inputId = id` id qui permet de récupérer la valeur.
* `label = 'titre'` texte a afficher.

Les méthodes :

* `actionButton()` bouton
* `checkboxInput()`
* `checkboxGoupInput()` 
* `dateInput()`
* `dateRangeInput()`
* `fileInput(nomFicher, text, multiple = FALSE)` importer un fichier. Paramètres du :

	* `$name` nom du fichier.
	* `$datapath` chemin du fichier.
	* `$size` taille en octets.

* `numericInput()`
* `paswordInput()` 
* `colourInput()` (package `colourpicker`) 
* `radioButtons()` 
* `selectInput(choices = liste)` liste à choix multiples (liste de liste pour avoir des groupes).
* `sliderInput()` barre de défilement.
* `textInput()` .
* `textAreaInput()` zone de saisie de texte.

### Interface 

Il existe deux princiapaux packages pour l'interface sont :

* shinydashboardplus le package le plus populaire.
* bslib qui s'appuie sur bootstrap et qui est plus moderne que shynidashboard.

#### Shinydashboardplus

`library(shinydashboardPlus)`

##### Panneau de saisie

* `mainPanel()` principale
* `sidebarPanel()` saisie

#### Bootstrap

`library(bslib)`

!!! example
    Exemple de tableau de bord [chicago flights](https://bslib.shinyapps.io/flights/).

##### Les cartes

`card(...)`

* `card_header("Datatable loaded")` entête
* `card_body()` corps
* `card_footer` pied de page.

##### Les icones

`library(bsicons)`

* `bs_icon("music-note-beamed")` ajouter un icon.

### UI

Paramètres :

* `title = titre` titrer l'application
* `skin = couleur` theme utilisé.

* `dashboardHeader(title = "titre", titleWidth = largeur)` entête.
* `dashboardSidebar(width = largeur, title = titre)` menu à gauche.
* `dashboardBody()` corps de la page.

#### Les onglets

* `sidebarMenu(menuItem(text = "onglet", tabName = "onglet"))` ajouter dans le menu.
* `tabItems(tabItems(tabName = onglet, contenuOnglet))` ajouter dans le corps. Paramètres :

	* `badgeLabel = nom, badgeColor = couleur` Ajouter un badge
	* `disable = TRUE` desactiver la barre.

##### Agencement

* `fluidRow(contenu)` 

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
	``` r
	tabBox(
	  title = titre,
	  tabPanel(title = "titre", tableOutput("nomTable"))
	) 
	```

!!! note
	Pour rendre une valeur dynamique avec valueBox sur server.
	``` r
	output$nom <- renderValueBox({  
	    valueBox(a completer)
	})
	```

### Server

``` r
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

``` r
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

1. Créer une variable réactive `r <- reactiveValues()` dans le fichier server.
2. Màj de la valeur `observe({r$data <- input$dt_kluster})`.
3. Déclarer la variable réactive dans le module :

``` r
mod_select_view_server <- function(id, r){
    ns <- session$ns
    moduleServer(id, function(input, output, session){...}
}
```

4. Appeler le module dans la partie server `mod_example_server("example_1", r = r)`.

* `observe({r$data <- input$dt_kluster})`
* `observeEvent()`

* `eventReactive(input$bouton, {...})` mettre à jour une valeur en fonction d'un événement.
* `observeEvent(input$bouton, {...})` mettre à jour des instructions en fonction d'un événement.

Mettre les parenthèses lorsque l'on utilise une variable réactive.

!!! warning
    `ns("id_output")` pour appeler une sortie utiliser les fonctions qui renvoie les identifiants.


[Blog](https://www.charlesbordet.com/fr/reactive-shiny/#la-fonction-observeevent) avec un bon article sur les variables réactives.

Shiny fonction `req`

eventReact
`ignoreNULL = FALSE` ne déclenche pas le calcul si l'élément est Null.


### Dataframe

#### DT

`library(DT)`

* `DT::renderDataTable({instruction})`
* `input$tableau_rows_selected` indice des lignes selectionnées.

#### Flextable

* `flextable(dataframe)` afficher un tableau comme une image.

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

Flexdasboard permet de créer des tableaux de bord site web dynamique à partir d'un fichie Rmarkdown. L'avantage principal est qu'il est facile à exporter dans un seul fichier.

`library(flexdashboard)`

[Flexdashboard](https://rmarkdown.rstudio.com/flexdashboard/)

``` r
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

### Les tableaux

`library(knitr)`

* `knitr::kable(data)` afficher un tableau en markdown. Paramètres :

	* `caption="Example dosing data extracted from theophylline data set"` ajouter un titre.


####  gt : faire de beau tableau.

`libary(gt)`

[gtsummary](https://www.danieldsjoberg.com/gtsummary/) permet de ganger du temps dans certaines mise en forme. 

Comparaison des différents packages pour le faire des tableaux https://hughjonesd.github.io/huxtable/design-principles.html par le créateur de huxtable

[gtExtras](https://jthomasmock.github.io/gtExtras/index.html) pour ajoute rdes graphiques ou des images dans le tabelau.

### Valeur box

* `valueBox(comments, icon = "fa-comments")` ajouter une valeur box.
