## Smartphone
### Android
### Play store

* Ankidroid, application de fiches mémoire open source (disponible également sur Windows,...) avec synchronisation entre les différents appareils.
* K-9 Mail, gestionnaire d'email open source.
* Lecteurs musiques :
	* Musicolet, le meilleur lecteur de musique local, open source.
	* Oto music gratuit et open source.  
* Notic, application pour bloquer les notifications de certaines applications.
### F-droid

Installer [Droid-ify](https://f-droid.org/en/packages/com.looker.droidify/) pour accéder à [F-droid](https://f-droid.org/).

* Anysoftkeyboard, un bon clavier.
* Auxio (ne fonctionne plus), un super lecteur audio.
* Vinyl, lecteur musique avec une interface un peu datée.
* Breezy, une bonne application pour la météo avec la possibilité de définir MétéoFrance comme fournisseur de données (Attention ne pas prendre la version FREENET qui ne contient que les open sources).
* Launcher :

    * Lawnchair laucher, launcher android open source et moderne (+ icones avec LauwnIcons). Le projet a été mis à l'arrêt.
    * Kvaesitso, launcher vertical avec deux panneaux et avec une personnalisation assez poussée (le BEST).

* LibreTube ou NewPipe, deux applications YouTube sans pub.
* Read you, lecteur de flux RSS.

## Google TV

* [SmartTubeNext](https://github.com/yuliskov/SmartTubeNext#readme) youtube sans pub.

----
# PC
## Windows

### L'essentiel

Disponible sur le Window Store :

* Brave, navigateur internet basé sur Chrome avec un bloqueur de pub intégré.
* Discord
* Firefox.
* Visual Studio Code, environnement de programmation.
* VLC, lecteur media.

Logiciels Windows :

* [Adguard](https://adguard.com/en/download.html), bloqueur de pubs indispensables.
* [Cryptomator](https://cryptomator.org/downloads/), pour chiffrer ses données numériques sur les cloud.
* [Calibre](https://calibre-ebook.com/download), gérer sa bibliothèque numérique.
* [Deluge](https://deluge-torrent.org/), gestionnaire de torrents.
* [Dropbox](https://www.dropbox.com/)
* [Keeweb](https://keeweb.info/), gestionnaire de mots de passe pour Keep.
* [Mail spring](https://github.com/Foundry376/Mailspring), boite mail local.
* [Noi](https://github.com/lencx/noi) ui pour les chats et consor.
* [Nora](https://github.com/Sandakan/Nora) lecteur musique au top.
* [UpdateHub](https://github.com/NexovaDev/UpdateHub) vérifier les mises à jours des logiciels.
### Le relatif

Sur le store :

* Simplenote.
* [Anki](https://apps.ankiweb.net/), cartes pour l'apprentissage par répétition.
* [Deemix](https://deemix.app/gui) - [Reddit Deemix](https://www.reddit.com/r/deemix/), télécharger des musiques depuis deezer.
* [FreeFileSync](https://freefilesync.org/download.php), synchroniser des répertoires et des fichiers.
* [Fluent reader](https://github.com/yang991178/fluent-reader/releases), aggrégateur de flux rss.
* [Harmonoid Music](https://harmonoid.com/), lecteur audio avec une interface agréable.
* [Google drive](https://www.google.com/drive/download/)
* [Miktex (latex)](https://miktex.org/) latex.
* [pCloud](https://www.pcloud.com/fr/download-free-online-cloud-file-storage.html)
* [pandoc](https://pandoc.org/) convertir des fichiers en word, markdown, html.
* Zotero, références bibliographiques.
## Ubuntu
## Logiciels

Disponibles dans la logitèque Ubuntu :

* Brave, navigateur internet sans pub.
* Dessin de Romain F T, logiciel de dessins très simple.
* Mailspring, client email.
* Visual code
* Vlc, lecteur multi média.

Disponible sur le site internet de l'entreprise :

* Crytpomator
* [dropbox](https://www.dropbox.com/install-linux)
# Disponible sur GitHub

Projet github intéressant :

* [NOI](https://github.com/lencx/Noi) client desktop pour les modèles d'IA (chat GPT...).
* [kobo ebook reader dict](https://github.com/BoboTiG/ebook-reader-dict), dictionnaires pour les liseuses Kobo.
* [SpotX](https://github.com/SpotX-Official/SpotX), bloqueur de pub sur la version desktop de spotify.
## Les meilleurs applications 

* [Cryptomator](https://cryptomator.org/), logicel de cryptage spécialisé pour le cloud.
* [Simplenote](https://simplenote.com/), logiciels de prises de notes en markdown avec synhcronisation entre les plateformes (android, windows,...).
* [Obsidian](https://obsidian.md/) ou [Logseq](https://logseq.com/) application de gestion de connaissances.
* [Mixx](https://mixxx.org/), logiciel de dj.
* [OnlyOffice](https://www.onlyoffice.com) et [FreeOffice](https://www.freeoffice.com/fr/) suite bureautique.

### Thunderbird

Exporter ses emails dans un fichier :

* sélectionner le dossier (ou l'email)
* outils > exporter
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

