## Télécharger

### Depuis Youtube

Library `yt-dlp` (`youtube-dl`en python sinon c'est en power shell) avec `yt-dlp 'id_youtube'` télécharger dans la meilleur qualité.

* `--merge-output-format mkv --remux mkv` convertir le fichier en mkv. Cela nécessite de télécharger ffmpeg et de déclarer la variable environnement /bin.
* `--extract-audio --audio-format mp3 <video URL>` télécharger le son d'une vidéo en mp3.
### Spotdl

Installation : `pip install spotdl`

[Spotify downloader](https://github.com/spotDL/spotify-downloader) pour télécharger depuis spotify.

Nécessite : `sudo apt install ffmpeg`

* `spotdl web` ouvrir la spotdl avec une interface web.
* `spotdl download [song] ou [playlistUrl]` télécharger une chanson ou plusieurs.
* `pip install --upgrade spotdl` màj spotdl.

Il suffit ensuite d'utiliser la commande dans le prompt Conda.
## Navigation Web automatique

Library `selenium`

Chromedriver à télécharger `https://chromedriver.chromium.org/downloads`

``` py
from selenium import webdriver
from selenium.webdriver.common.by import By
from selenium.webdriver.chrome.service import Service
from selenium.webdriver.chrome.options import Options
import time

options = Options()
options.binary_location = "C:\\Program Files (x86)\\BraveSoftware\\Brave-Browser\\Application\\brave.exe"
s = Service('C:\\Users\\Guigui\\Downloads\\chromedriver.exe')
driver = webdriver.Chrome(chrome_options=options, service=s) #ouvrir le navigateur
```

* `driver.get(url)` charger une page web.
* `driver.find_element('balise', 'valeur')` sélectionner un élément sur la page.

`from selenium.webdriver.common.by import By` 

Référence				| Définition
------------------------|----------------
`CLASS_NAME` 			| Nom de la classe
`CSS_SELECTOR` 			| CSS selector
`ID` 					| Identifiant de la balise
`LINK_TEXT` 			| Texte
`PARTIAL_LINK_TEXT`		| Morceau de texte
`NAME`					| Nom de la balise
`TAG_NAME` 				| Balise
`XPATH` 				| Xpath

Action sur l'élément sélectionner :

* `.send_keys(valeur)` remplir les valeurs.
* `.click` cliquer sur la sélection.
## Importer un script python

Library `subprocess`

* `call([sys.executable, 'C:\\temp\\hello2.py'], shell=True)` importer un script python.
* `['java', '-jar', 'temp.jar' param1, param2]` exécuter un script java.
## Documentation

Packages pour générer de la documentation :

* [Read the docs](https://docs.readthedocs.io/en/stable/tutorial)
* [Sphinx - python doc generator](https://www.sphinx-doc.org/en/master/#)
## Base de données

### Sqlite 3

Package `sqlite3`
#### Connexion à la database

``` py
conn = sqlite3.connect('base de donnees.db')
c = conn.cursor()
```

`conn.close()` deconnection de la dbb.
#### Soumettre une requête

* `c.execute('''requete''')`
* `c.executemany('''requete''', liste)`

Les variables à utiliser dans la requête doivent etre declarées par un `?`.
S'il y en a plusieurs, il faut les organiser sous la forme d'une liste.

!!! note
	Penser à convertir le résultat en liste.

* `conn.commit()` écrire ou modifier la bdd en exécutant la requête.
### Convertir un dictionnaire en mdx

!!! note
    C'est le format géré par DictTango.

* [dict2mdx](https://github.com/sobaee/dict2mdx) convertir un dictionnnaire en mdx.
* [dict2mdx](https://github.com/vpnry/dict2mdx) fait par un autre type que j'ai réussi à faire fonctionner en suivant le tuto mais j'ai rencontré des galères pour l'intallation des prérequis.

Je suis passé par la machine virtuel Ubuntu.

Code pour installer le prérequis [pyicu](https://gitlab.pyicu.org/main/pyicu#installing-pyicu)

``` bash
# EITHER - from apt directly https://packages.debian.org/source/stable/pyicu
apt-get install python3-icu
# OR - from source
apt-get install pkg-config libicu-dev
pip install --no-binary=:pyicu: pyicu
``` 

!!! note
    Pour le dictionnaire il est possible de spécifier le chemin vers les fichiers.