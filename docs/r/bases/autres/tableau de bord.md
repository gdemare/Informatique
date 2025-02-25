``` R
library(shiny)
library(shinydashboard)

ui <- fluidPage(
  interface
)

server <- function(input, output) {
    contenu
  }

#executer l'application
shinyApp(ui = ui, server = server) 
```

* `page_fillable(...)` page qui occupe tout l'écran.
* `page_fluid(...)` page scrollable.

## Eléments d'interface

!!! note
	Le contenu non modifiable est basé sur les balises html.

Code           		| Type
--------------------|-----------------
`p("texte simple)`  | Texte simple.
`h1("titre 1")`     | Titre de hiéarchie 1.

#### Saisie

* `type(inputId = id, ....)`
* `input$id` récuperer l'entré. Utile notamment dans la partie server.

Les différentes méthodes pour :

Option :

* `inputId = id` id qui permet de récupérer la valeur.
* `label = 'titre'` texte a afficher.

Les méthodes :

* `actionButton("id",...)` bouton.
* `checkboxInput("id",...)` liste à cocher à un seul élément.
* `checkboxGroupInput("id",...)` liste à cocher à plsuieurs éléments.

  * `inline = T` sur la même ligne.

* `dateInput()` calendrier de saisi de date.
* `dateRangeInput()` calendrier avec période.
* `fileInput(nomFicher, text, multiple = FALSE)` importer un fichier. Paramètres du :

	* `$name` nom du fichier.
	* `$datapath` chemin du fichier.
	* `$size` taille en octets.

* `numericInput()` valeur numérique.
* `paswordInput()` 
* `colourInput()` (package `colourpicker`) 
* `radioButtons()` 
* `sliderInput()` barre de défilement.
* `textInput()` petite zone de saisie textuelle.
* `textAreaInput()` grande zone de saisie de texte.

#### Les listes selectionnbles

* `selectInput(choices = liste)` liste à choix multiples (liste de liste pour avoir des groupes).
* `varSelectizeInput()` selectionner les colonnes d'un df.
* `updateSelectInput(session, id, choices = c("A", "B"), selected = "A")` mettre a jour un select (dans le `server`).


Paramètres :

* ` multiple = TRUE` autoriser de multiples saisies.


### Interface 

Il existe deux princiapaux packages pour l'interface sont :

* `shinydashboardplus` le package le plus populaire.
* `bslib` qui s'appuie sur bootstrap et qui est plus moderne que shynidashboard.

#### Shinydashboardplus

`library(shinydashboardPlus)`

##### Panneau de saisie

* `mainPanel()` principale.
* `sidebarPanel()` saisie.

Les boîtes :
``` R
box(title = "New",
	fluidRow(
	        column(width=4, objet),
	        column(width=4, objet)
		)
)
```

* `sidebarMenu(menuItem(text = "onglet", tabName = "onglet"))` ajouter dans le menu.
* `tabItems(tabName = onglet, contenuOnglet))` ajouter dans le corps. Paramètres :

	* `badgeLabel = nom, badgeColor = couleur` Ajouter un badge
	* `disable = TRUE` desactiver la barre.

Paramètres :

* `title = titre` titrer l'application
* `skin = couleur` thème utilisé.

* `dashboardHeader(title = "titre", titleWidth = largeur)` entête.
* `dashboardSidebar(width = largeur, title = titre)` menu à gauche.
* `dashboardBody()` corps de la page.

#### Bootstrap

`library(bslib)`

!!! example
	Exemple de tableau de bord [chicago flights](https://bslib.shinyapps.io/flights/).

##### Structure de la page

* `hr()` ajouter une ligne horizontale.

* `layout_columns(...)` créer une ligne avec 12 colonnes responsives. Paramètres :

  * `col_widths =` largeur de chaque colonne (max = 12).
  * `style = css(grid_template_columns = "5fr 3fr")` pour avoir des éléments avec des tailles différentes.
  * `row_heights =` hauteurs.

* `layout_column_wrap()` colonnes avec retour à la ligne des éléments lorsque la taille est insuffisante.


* `page_fillable(...)` remplir l'ensemble de la page.
* `page_navbar(titre, ...)` barre horizontal en haut. Elements ajouter :

	* `title = "PKE"`
 	* `footer =`

  * `nav_panel(titre, contenu)` ajouter un ongler
  * `nav_menu(titre, nav_item("ele1"), nav_item("ele2"))` ajouter une liste avec les onglets.
  * `nav_spacer()` espace dans le menu.

  Options :

  * `underline = T` souligner l'onglet actuel.

* `page_sidebar(...)` menu à gauche.

  * `sidebar = sidebar(...)` ajouter des élements au menu.

!!! note 
	Il faut ajouter `page_X(fluidPage(...))` pour pouvoir interagir avec les DT.

* `layout_sidebar()` ajouter le menu à gauche.


`style = css(grid_template_columns = "2fr 1fr")` largeur des relatives des éléments.

##### Les cartes

`card(...)`

* `card_header("Datatable loaded")` entête
* `card_header("Datatable loaded")` titre.
* `card_body()` corps.
* `card_footer()` pied de page.

Paramètres :

* `full_screen = T` autoriser la mise en pleine écran.
* `class = "class boostrap"` ajouter une classe bootstrap (exemple  `bg-light`).

``` R
value_box(
  title = "I got",
  value = "99 problems",
  showcase = bs_icon("music-note-beamed"),
  p("bslib ain't one", bs_icon("emoji-smile")),
  p("hit me", bs_icon("suit-spade"))
)
```

##### Accordéon

* `accordion(accordion_panel(...))` Menu en accordéons. Paramètres :

  * `open = T ou id` panneau ouvert par défaut.

* `accordion_panel(title, "les éléments", value = title, icon = NULL)` ajouter un panneau.

##### Icônes

`library(bsicons)` basée sur les [icones bootstrap](https://icons.getbootstrap.com/) 

* `bs_icon("music-note-beamed")` ajouter un icone.

### Eléments d'interface

* `fluidRow(contenu)` 

Code            					| Type
------------------------------------|-----------------
`br()`         					    | saut de ligne
`hr()`         					    | ligne horizontale
`box()`         					| classique
`infoBox()`     					| texte statique
`tabBox()`      					| valeur
`valueBox()`   						| valeur dynamique
`modalDialog()`						| fenêtre pop up (ajouter un bouton `modalButton("Dismiss")`)
`HTML("## markdown")`               | afficher du code html.
`renderMarkdown(fichier)`         	| afficher du texte markdown (`library(markdown)`).

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
`renderText({texte})`             | texte                     | `textOutput('variable')`, `htmlOutput("id")` 
`renderPrint(variable)`           | variable                  |
`renderPlot({graphique})`         | graphique                 | `plotOutput('variable')`
`renderTable({tableau})`          | tableau                   | `tableOutput('variable')`
`renderPlotly({graphique})`       | données                   | `plotlyOutput('variable')`
`renderUI("summary")`             | html et dans server       | `uiOutput(id)`

* `tagAppendAttributes(style= 'color:green;')` ajouter un attribut.

#### DataFrame

##### DT

`library(DT)`

* `renderDT()` server (à éviter `renderDataTable({dataFrame})`). Paramètres :

    * `editable = TRUE` rendre la table éditable.
    * `filter = list(position = 'top', clear = FALSE)` filtrer chaque colonne.

* `datatable(df)`

    * `rownames= FALSE` cacher le nom des lignes.
    * `options = list(...)`
        
        * `scrollX = TRUE` scrollable.
        * `autoWidth = T` prendre toute la largeur.
        * `dom = 't'` cacher la barre de recherche.

  * `selection = "single"/"multiple/none"` doesn't work with `list()` :
  
    * `target=row/column/cell` définir le type de sélection.
    * `selected = matrix(c(1, 3, 2, 4), nrow = 2, ncol = 2)` préselectionner des cellules (matrice à deux colonnes).
  

* `DTOutput()` (à éviter `dataTableOutput('variable')`). Paramètres :  

Valeurs récupérables à partir d'un dataframe :

Par exemple, avec `target = 'cell'`, les valeurs sont présentes dans `input$id_table`+ `_cells_selected`.

* id_table + `_row_last`
* id_table + `_cell_clicked`
* id_table + `_last_clicked`
* id_table + `_selected`

``` R
observeEvent(input$table1_cell_edit, {
  row  <- input$table1_cell_edit$row
  clmn <- input$table1_cell_edit$col
  rv$data[row, clmn] <- input$table1_cell_edit$value
})
```

##### Reactable

`library(reactable)`

* `reactable(dataframe)` créer un reactable. Paramètres :

  * `bordered = T` bordures.
  * `highlight = T` afficher un fond sur la ligne ou se trouve la souris.
  * `selection = "multiple"` selectionner des lignes. `defaultSelected = c(1)` ajouter une sélection par défaut. 
  * `onClick = "select"` selectionner une ligne au click.
  * `filterable = TRUE` zone de recherche pour chaque colonne.
  * `searchable = TRUE` zone de recherche unique.
  * Créer des groupes de colonnes :
  
  ``` R
  columnGroups = list(
          colGroup("Subject id", columns = grp_label_subject_id),
          colGroup("Statistics", columns = grp_label_statistics)
          )
  ```

* `resizable = T` colonne redimensionable.
* `rownames = T` afficher le nom des lignes.

!!! note
	`selection = "multiple"` et `onClick = "select"` pour ajouter une colonne de checkboxes.

* `renderReactable({reactable(iris)})`
* `reactableOutput("table")`
* `getReactableState("tab_pk", "selected")` renvoie tous les numéros des lignes sélectionnées.

```
colonne = colDef()
```

* `name = "Sepal Length"` nom de la colonne à afficher
* `show = T` afficher la colonne.

Colorer les cellules `library(reactablefmtr)`  

 are option for `reactable()`

* `columns = list()` colorer une colonne en fonciton des valeurs.

  * `colonne = colDef(style = color_scales(data, color_by = 'colonne'))` colorer la colonne en fonction des valeurs. 
    * `colors = c("#f0f0f0", "#519de9")` personnaliser les couleurs utilisées.

Ajouter des paramètres de modifications `library(reactable.extras)`

```r
 columns = list(
            unit_to = colDef(cell = text_extra("text")) 
            )
```

* `text_extra("text")` zone de texte libre.
* `dropdown_extra(id = "dropdown", vecteur, class = "dropdown-extra")` liste à choix.

#### Download file

* `downloadButton(outputId = "download_kluster", label = "Kluster export")` bouton de téléchargement d'un fichier dans UI.

Code du server :

``` R
output$downloadBPR <- downloadHandler(
    filename = function(){nom_fichier},
    content = function(file){file.copy(paste0(workDir, "BPR.xlsx"), file)
      }
  )
```

* `shinyjs::runjs("$('#download_summary')[0].click();") ` télécharger sans utiliser le bouton.download.

## Variable réactive

Deux manières de rendre un objet réactif :

* une entrée : ...Input 
* une sortie : ...Ouput ou output$...
* les deux : reactive()

``` R
variable = reactive({
    return(valeur)
})
```

créer une variable réactive celle ci à les mêmes propriétés qu'une fonction.

* `variable()` utiliser une variable réactive qui n'est pas modifiable.
* `eventReactive(input$action, {variable})` réactive variable à la suite d'un évènement. Paramètres :

  * `ignoreNULL = T` déclencher le calcul uniquement si la valeur n'est pas nulle.
  * `ignoreInit = F` déclencher le calcul uniquement si la variable réactive existe.

!!! note
    Lorsqu'il y a plusieurs filtres il est préférable d'utiliser un bouton pour déclencher le calcul.

## Contexte réactif

* `reactiveValues()` créer une variable réactive modifiable. La variable créée est une liste.
* `observe({r$data <- input$data})` déclarer un contexte réactif. L'instruction est lue dès le lancement de l'application.
* `observeEvent(input$bouton, {...})` mettre à jour des instructions en fonction d'un événement.

!!! warning
    `reactiveValues()` fonctionne avec observeEvent et non pas avec eventReactive.

!!! note 
    Possibilité de définir des `output$...` au sein du contexte.

* `{input$submit1, input$submit2}` si aucun élément n'est NULL.
* `c(input$submit1, input$submit2)` au moins un des éléments n'est pas nul.

#### Liste interactive utilisant une variable réactive

``` R
ui :
  uiOutput("interaction_slider")
```

Server :

``` R
  filterGenre <- reactive(genre)
  output$interaction_slider <- renderUI({
    selectInput("select", label = "Select box", 
                choices = as.list(genre)$genre_label, selected = 1)})
```

1. Créer une variable réactive `r <- reactiveValues()` dans le fichier server.
2. Màj de la valeur `observe({r$data <- input$dt_kluster})`.
3. Déclarer la variable réactive dans le module :

``` r
mod_nom_ui <- function(id){

  ns <- NS(id)

  tagList(
    element1(ns("id1")),
    element2(ns("id2"))
  )

}


mod_nom_server <- function(id, r){
    moduleServer(id, function(input, output, session){

      ns <- session$ns # parfois utiles

      code server
    }
}
```

4. Appeler le module dans la partie server `mod_example_server("example_1", r = r)`.

!!! warning
    `ns("id_output/id_input")` pour appeler une sortie utiliser les fonctions qui renvoie les identifiants.


[Blog](https://www.charlesbordet.com/fr/reactive-shiny/#la-fonction-observeevent) avec un bon article sur les variables réactives.

`req(variable)` le code est stopé si les variables requises ne sont pas disponibles.

`eventReact()`

* `ignoreNULL = FALSE` ne déclenche pas le calcul si l'élément est Null.

----------------------------

### Datamods

-----------------------------

## Shinyapps

`library(rsconnect)`

1. Découper le projet en deux fichiers : server.R et ui.R.
2. Générer un jeton depuis le site [shinyapps](https://www.shinyapps.io) : Token. 

### Données sessions

* `session$clientData$url_protocol`
* `session$ns` récupérer l'identifiant de session.

## Insérer fichier 

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

### Valeur box

* `valueBox(comments, icon = "fa-comments")` ajouter une valeur box.

### Barre de progression et animations de chargement

```r
withProgress(message = 'Compute parameters PK', style = "notification", value = 0, {

       # incProgress(percentage_by_group, detail = paste("Group", name_grp))
      })
```

* `shinycssloaders::withSpinner(ui)` animation de chargement d'un élément. 
