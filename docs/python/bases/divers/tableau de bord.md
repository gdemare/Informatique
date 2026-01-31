# Streamlit

Package `streamlit`

## Exécuter streamlite

* `streamlit hello` première excution de steamlit.
* `streamlit run fichier` exécuter un projet streamlit.

`import streamlit as st`

## Titre et texte

* `st.divider()` ajouter run barre horizontale.
* `st.subheader('Raw data')` ajouter un sous titre.
* `st.header('Raw data')` ajouter un sous titre.
* `st.title('ACP')` titre.
* `st.write(data)` afficher un tableau de données.
* `st.markdown(texte)` afficher du markdown.
* `st.text(texte)` afficher du texte.

## Elements de strucutres (boites, menu dépliants)

#### importer un fichier 

* `file = st.file_uploader("Please choose a file")` Paramètre : 
    * `accept_multiple_files=True` importer plusieurs fichiers à la fois. 

#### Panneau dépliant

Ajouter un panneau qui se déplit :
```
with st.expander("See explanation"):
    st.image("https://static.streamlit.io/examples/dice.jpg")
```

#### Module pour créer un bouton pour afficher les données 

* `if st.checkbox('Show raw data'):` case à cocher.
* 

### Input 

* `st.multiselect(text, valeur possible, valeur par défaut)` zone de sélection multiples (plusieurs choix).
* `st.text_input(text, value ='')` zone de saisie.
* `st.selectbox( 'Columns', (data.columns), )` zone de saisie simple.

### Graphique plotly

```
acp_fig = px.scatter(acp, x = acp.columns.values[0], y = acp.columns.values[1], color = acp.index.values.astype(str), title="PCA Graphics")
```
Il faut charge le graphique dans une variable.

`st.plotly_chart( acp_fig )` Afficher un graphique. Paramètres :
    * `theme=None` 
    * `use_container_width=True` 

### Boutons download

`st.download_button(label = 'Download data', data = prc_common_mat.to_csv(), file_name = 'common-percentage.csv')` bouton de téléchargement de ficher.

```
buffer = io.BytesIO()
with pd.ExcelWriter(buffer, engine='xlsxwriter') as writer:
    # Write each dataframe to a different worksheet.
    prc_common_mat.to_excel(writer, sheet_name='Sheet1', index=False)

download2 = st.download_button(label="Download data as Excel", data=buffer, file_name='large_df.xlsx', mime='application/vnd.ms-excel')
```
Bouton pour télécharger un fichier excel.

## Instructions spécials à mettre avant les fonctions

* `@st.cache_data` prévenir de la fuite de données.

# Plotly : les graphiques interactifs

`import plotly.express as px`

* `px.scatter(df, x=, y="sepal_length", color="species")`
* `px.bar(data_canada, x='year', y='pop')` diagramme en barre la fonction counte le nombre de lignes.
* `px.imshow(table)` heatmap. Paramètres :
    * `zmin=0, zmax=100` changer le min et le max de la légende.
    * `color_continuous_scale='Greens'` changer la palette de couleur 

* `px.histogram(data, x= data[var_ind], log_y=True )` histogramme.

## Ajouter des éléments

* `fig.add_vline(y=0.9)` ajouter une ligne verticale, horizontale.
   * `line_color = "red"` changer la couleur de la ligne.
* `fig.update_layout( xaxis_title = 'axe x' )` modifier les axes.

Paramètres généraux :

* `title = 'titre'`
* `color = variable_groupe`
  `log_y=True` pour passer en echelle logarithmique.

### Modifier les axes 

`common_heatmap.update_xaxes( tickangle = 50)` changer l'orientation des étiquettes.
