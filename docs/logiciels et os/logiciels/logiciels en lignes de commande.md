## Pandoc

Convertir du markdown en word, html, pdf.

`pandoc fichier -o sortie.docx` Paramètres :

* `-t markdown-multiline_tables-grid_tables` eliminer des extensison dans les convertions.

!!! warning 
	NE FONCTIONNE PAS A CAUSE DES EXPRESSIONS MATHEMATIQUE Pour Ubuntu, pour convertir en pdf, installer texlive-latex-base, texlive-fonts-extra,texlive-fonts-recommended, texlive-latex-extra.
## Nbconvert

`jupyter nbconvert --to pdf --no-input fichier.ipynb` expoter un fichier ipynl en hmtl ou en pdf. Paramètres :

* `--to html` en html.
* `--no-input` masquer le code.
* `--template theme` avec un thème.
## Documentation en markdown

#### Installation 

Zensical(https://zensical.org/docs/) nouveau projet de la team de mkdocs material après les évolutions de Mkdocs.

- `zensical new` create a new project
- `zensical serve` start local web server
- `zensical build` build your site

Installer les packages Python [mkdocs](https://www.mkdocs.org/) et [mkdocs material](https://squidfunk.github.io/mkdocs-material/), sur le dernier site il y a tout, de l'installation à la personnalisation. L'installation se fait via Python. 

Il y a notamment en modules utiles : `mkdocstrings-python, mkdocs-glightbox, mkdocs-git-revision-date-localized-plugin`.

`mkdocs new my-project` créer un projet.

Le fichier de configuation est `mkdocs.yml` :

```
site_name: Mes notes

# mkdocs.yml
theme:
  name: "material"
  features:
    - content.tabs.link

plugins:
  - search
  - mkdocstrings
  - glightbox #pour les images

markdown_extensions:
  - pymdownx.superfences
  - pymdownx.tabbed:
      alternate_style: true
  - admonition
  - pymdownx.details
  - pymdownx.superfences


nav:
  - Méthodes : 
    - Lyse : methodes/lyse.md
    - Précipitation : methodes/precipitation.md
  - Cahier de laboratoire: 
    - FMRP : cahier-laboratoire/FMRP.md
```

* `mkdocs serve` exécuter le serveur.

### Déployer sur github

1. Passer son répertoire en public : Settings > General > Danger zone > Change repository visibility
2. Settings > Actions > General > Workflow Permissions and select Read and write permissions.
3. Créer un fichier dans .github/workflows/ci.yml

```
name: ci 
on:
  push:
    branches:
      - master 
      - main
permissions:
  contents: write
jobs:
  deploy:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v3
      - uses: actions/setup-python@v4
        with:
          python-version: 3.x
      - uses: actions/cache@v3
        with:
          key: mkdocs-material-${{ github.ref }} 
          path: .cache
          restore-keys: |
            mkdocs-material-
      - run: pip install \
                mkdocs-material \
                mkdocstrings \
                mkdocs-glightbox \
                mkdocs-git-revision-date-localized-plugin \

      - run: mkdocs gh-deploy --force
```

4. Settings > Pages et mettre Branch :`gh-pages`

### Le contenu 

Les fichiers de documentation sont à mettre dans le dossier `docs`.

### Markdown langage

### Les boites

Attention, il faut que la tabulation mesure 4 espaces.

* `!!!` pour une box afficher
* `???` pour une box retrécie.

Type `note`, `info`, `quote`, `example`, `bug`, `danger`, `failure`, `warning`, `question`, `success`, `tip`, `info`, `abstract`, `note`.

### Les listes

1. element1
2. element2

* _texte_ italique
* __texte__ gras

* [ ] élément 1
* [X] élément 2
### Tableau

colonne1	| colonne2
------------|-----
val1 		| val2

### Chrome

Pour recherher directement sur un site internet, dans `Moteur de recherche`

| Requête  | Raccourci |
|---|---|
| `https://www.youtube.com/results?search_query=%s&page={startPage?}&utm_source=opensearch` | yt |

### Android

Dans TWRP

1.  Supprimer les données de cache`Wipe`.
2. Installer `Install`
3. Installer  Gapps avec `Install`

### Virtualisation
[Quickmu](https://github.com/quickemu-project/quickemu) logiciel de vm. Il permet de virtualiser MacOS, Windows et Linux.
