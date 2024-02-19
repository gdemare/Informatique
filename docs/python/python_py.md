### Utile pour les notebooks

 * `%pip install package` installer un package directement dans python.
 * `%matplotlib inline` afficher les graphiques dans le code.

### Extension fichier Python

* `.pyw` fichier python exécutable.

### Conda

Conda est un logiciel qui permet de gérer les environnements en Python. Cela permet par exmeple d'installer plusieurs versions différentes sur la même machine.

* `conda create -n python_env` créer un environnement conda.

	* `python=3.9` préciser la version de python.

* `conda env list` lister les environnements.
* `conda activate python_env` activer l'environnement.
* `conda deactivate` quitter l'environnement.
* `conda update` mettre a jour tous les packages.

Dans pour choisir le noyau d'un envrionnement Visual Code ctrl+shift+P, sélectionner, `Pyhon : select Interpreter`. Sinon, dans le Terminal :

1. `conda activate ppoulain-python` activer l'environnement.
2. `code .` lancer Visual Code.

#### Installer un module

* `pip install package` installer une bibliothèque. Paramètre :

	* `-r package1, package2` installer plusieurs librarys en une seule fois. Pour créer l'installation d'un programme python, il est possible de créer un fichier `requirements.txt` qui contient la liste des library. Il suffit d'exécuter `pip install -r requirements.txt` pour installer tous les modules.



!!! note
	Il est possible de stocker le nom des library à utiliser dans un fichier. Les library sont accessibles `c:\users\guigui\anaconda3\envs\python_env\lib\site-packages`

##### Générer un fichier requirements.txt

* `pip freeze > requirements.txt` 	
* [old] package `pipreqs` avec `pipreqs /path/to/project` générer le fichier requirements.

##### MàJ des packages

* `pip list --outdated` liste des packages avec des màj disponibles.
* `pip freeze | %{$_.split('==')[0]} | %{pip install --upgrade $_}` maj en passant par le PowerShell.

#### Cloner un dossier github : 

``` bash
git clone https://github.com/jkbr/httpie.git
sudo python setup.py install
```

## Créer un module et l'impoter

* attribut ou propriété associé à un élément. Elles sont accessibles par `objet.propriété` et elles peuvent être lister avec `dir()`.
* méthode est un objet de type fonction. `objet.fonction()`.

Strucutre du dossier : `dossier/module1.py`,`dossier/module2.py` 

Pour importer les fichiers class dans python :

``` python
sys.path.append('chemin/dossier')
from fichier import class
```

### Environnement en python

* `python3 -m venv nom_environnement` créer un environnement python.
* `source python_env/bin/activate` activer l'environnement.
* `deactivate` désactiver l'environnement.

`code > .` ajouter l'environement à Visual Code.

### Convertir un python en application

Library `pyinstaller`

`pyinstaller script.py`

Paramètres :

* `--noconsole`
* `--w`
* `--onefile`

## Instructions de bases

### Les matrices

library : `NumPy`

* `a = np.array([[11,12,13], [21,22,23]])` déclarer une matrice.
* `np.shape(a)` dimension d'une matrice .

Opérateur 	| Définition
----------------|--------------
`a*b` 		| multiplication
`np.dot(a,b)`	| produit matriciel (NxM et MxO)|
`a.T` 		| transposition

### Importer des fonctions

* `import package` charger un package complet. Les fonctions sont accessibles par `package.fonction`
* `from package import module` charger un module.
* `module.fonction()` utiliser une fonction d'un module.
* `help(module)`afficher les informations sur un module.
* `from module import partieModule` importer uniquement un sous module.
* `*` importer toutes les fonctions.

### Les instructions

Les instuctions peuvent être séparées par `;` ou par un saut de ligne.

### Commenter le code

* `# commentaire` commentaire sur une seule ligne.
* `"""commentaire"""` commentaire sur plusieurs lignes.
* `début \ suite` d'écrire une instruction sur plusieurs lignes

## Les variables 

* `a = valeur` créer et affecter une valeur à une variable.
* `a, b = val1, val2` affecter plusieurs variables en même temps.
* `input("afficher")` saisie utilisateur (convertir en nombre la saisie `int(...)`).
* `del variable` supprimer une variable.
 
Liste des variables par défaut :
* `%pwd` dossier par défaut.

### Format de données

* `type(variable)` renvoie le type de variable.

Fonction		| Définition 
------------------------|-------------
`list(variable)` 	| convertir en liste
`int()`			| convertir en entier
`float()` 		| convertir en float 
`str()` 		| convertir en texte

* `format( nombre, '.2f' )` ou `f"{3.4562:.2f}"` format des chiffres le 2 correspond à 2 nbre après la virgule. Attention, converti en texte.
* `dir(element)` lister toutes les méthodes associées à une variable.

## Les listes

Tableau récapitulatif des types de listes :

Type de listes		| Eléments uniques 	| Doublons
--------------------|-------------------|----------------
Modifiable			| liste				| set
Non modifiable		| tupple			| frozenset

### Les listes modifiables

`[] = vecteur` et `() = liste` (appelé tupple).

!!! note
	Les listes ne sont pas modifiables.

* `var[nbre]` extraire une valeur.
* `['valeur']*n` créer une liste à n élément
* `del liste[numéro]` supprimer une valeur.
* `(a,b) = (1,3)` donner un nom aux élements de la liste pour pouvoir les appeller comme des variables.
* `liste1 + liste2` concaténer deux listes.
* `liste1 * nb` dupliquer les éléments d'une liste.
* `liste = [ val1, val2]` déclarer une liste.
* `liste[pos1][pos2]` afficher un élément.
* `liste[4:]` sélectionner tous les éléments à partir du 4ème. Attention dans le cas de `4:7` prend l'élément 4, 5 et 6. 

* `sorted(liste, reverse=false)` trier une liste sans l'enregistrer.
* `set(liste)` renvoie les valeurs uniques pour une liste.
* `len(liste)` taille de la liste.

* `liste.append('texte')` ajouter une valeur à un vecteur à la dernière position.
* `liste.insert(position, valeur)` inserer une valeur à une position.
* `liste.pop()` supprimer le dernier élément d'un vecteur.
* `liste.remove('valeur')` supprime une valeur du vecteur.
* `liste.replace(ancien, nouveau)` remplacer une valeur.
* `separateur.join(liste)` joindre les éléments d'une liste
* `liste.sort(reverse=False)` trier un vecteur. Le résultat est automatiquement enregistré.
* `liste.reverse()` inverser une liste.
* `liste.count('valeur')` compter la valeur d'un vecteur.

!!! warning
	`x = y` créer une référence ie si `y` est modifié alors `x` l'est aussi.
	Pour copier
	
	* `x = y[:]`
	* `x = list(y)`
	* `copy.deepcopy(y)` copie avec la library `copy`.

### Les dictionnaires

Le dictionnaire est un objet particulier. L'accés aux valeurs fait par l'id.

* `dict = {'id' : [val1, val2, val3]}` Déclarer un dictionnaire.
* `dict['id']` ou `dict.id` pour connaitre une information.
* `dict["ajout"] = "valeur"` ajouter une valeur dans le dictionnaire.

!!! note
	Pour ajouter un nouveau champs à un existant. Il faut s'assurer que la position ou l'on ajoute l'information soit un dictionnaire  `dict[clé]["nouveau"] = ajout`.

* `.get(id)` renvoie la colonne si l'id existe sinon `None`.
* `.values()` renvoie les valeurs sous forme de liste.
* `.items()` renvoie (id, valeur).
* `.keys()` renvoie la liste des id.
* `record_dict["sp"] = record_dict.pop("id")` modifier la clé d'une entrée.
* `.update(reference)` ajouter une nouvelle valeur.
* `sorted(dico)` trier un dictionnaire par la clé.

	* `key=dic.get` trier par valeur.shuffle.
	
!!! example
	Trier un dictionnaire par valeur : `{word : seq_nb_words[word] for word in sorted(seq_nb_words, key=seq_nb_words.get, reverse = True)}`. 	

* `dict(liste)` convertir en dictionnaire.
* `for key in dico:` itérer un dictionnaire renvoie la clé (pour renvoyer la clé et la valeur, itérer sur `dico.items()`).

### Les tupples (les listes non modifiables)

* `tupple(list)` convertir en tupple.
* `t = t + (2,)`ajouter un élément.

compte un nombre de valeurs

`dic.get(valeur, 0) + 1` ajoute la valeur si elle n'est pas présente et ajoute 0+1 sion ajoute +1.

### Set et frozenset

Liste d'éléments uniques. Elles sont utiles pour éliminer les doublons. La différence entre les set et les frozenset est que ce dernier n'est pas modifiable.

* `{}` déclarer un set.
* `set()`convertir en set.
* `.add(valeur)` ajouter une valeur.
* `.discard(valeur)` supprimer une valeur.

Opérations ensemblistes sur les sets

Python			| Définition
----------------|---
`.union()`		| dans s1 et pas dans s2
`.issubset`		| s1 est un sous ensemble de s2
`.isdisjoint`	| est disjoint

`{base : seq.count(base) for base in set(sequence):}` compter le nb de bases dans une séquence.

### Les collections

Pas mal de trucs. Elles permettent de compter le nombre d'éléments via `collections.Counter(seq)`

## Les types de variables

### Texte

* `r"texte /n"` les caractères spéciaux ne sont pas interprétés.

Fonction 		| Définition
----------------|-----------------
`chr(nbre)`		| convertie un nombre en sa lettre correspondante.
`len(texte)`	| nombre de caractère de la chaine.
`.lower()`		| mettre un texte en minuscule.
`.upper()`		| mettre un texte en majuscule.
`.capitalize()`	| premier lettre de chaque mot en majuscule.

```
''' texte sur 
	pluisieurs ligne
'''
```

* `texte.find("a trouver")` renvoie la position de la première occurence (sinon -1).
* `startswith("debut")` renvoie un booléen si la chaîne commence par début.
* `texte.strip()` supprimer les espace au début et à la fin.

#### Expression régulière (regex)

Library `re`. Une expression régulière est déclarée comme `r"expr"`.

* `re.search( a_rechercher, texte )` rechercher une expression regex ou un mot.
* `re.sub(r'[^a-zA-Z]', '', s)` transformer une chaine de caractère.

Variable de sortie :

* `.group(0)` pour accéder aux résultat de la recherche.
* `.span()` les positions.
* `.start()` la première position.
* `.end()` la dernière position. 

Symbole 		| Définition (négation)
----------------|--------------
`\s` (`\S`) 	| espace
`\d` 			| chiffre
`\` 			| caractère d'échappement
`.` 			| jocker tous les caractères
`*` 			| n'importe quel symbole plusieurs fois `[2-6]` séq de 2 à 6
`[]` 			| ecrite l'expression à l'intérieur
`^` 			| position du début
`$` 			| en fin de chaîne
`[0-9]{4}`		| nbre de fois qu'apparait un chiffre
`\w`			| équivalent à [a-zA-Z0-9]
`?`				| négation

Exemples :

* `"[^.?-]*"` tous les caractères avant `-`.

### Les dates

Package : `datetime`

Fonction 			| Définition
--------------------|----------------
`date.today()`		| aujourd'hui
`date.weekday()`	| numéro du jour de la semaine

* `datetime.strptime(texte, '%d.%m.%Y')` convertir en date et time.
* `variable.strftime('%Y-%m-%d')` avec un affichage particulier.

### Condition 

```
if condition:
	instruction
elif condition:
	instruction
else:
	instruction
```

#### Les opérateurs logiques (booléens)

Symbole 				| Opération
------------------------|------------------------
`and` ou `&` 			| et
`or` ou `|` 			| ou
`not condition` ou `~` 	| négation
`is None` 				| null
`in` 					| vérifier la présence d'un caractère (appartient)
`.endswith("fin")` 		| se termine par
`pd.isna()` ou `np.isnan()` 	| vérifier si c'est une valeur manquante
`np.nan` 				| valeur manquante
`np.invert(vecteur)` 	| transforme vrai en faux

Condition : `==`, `>=`, `>`, `!=`

### Les boucles

* `break` permet de sortir des deux types de boucles.

#### La boucle for

```
for i in séquence:
	instruction
```

* `output_list = [print(a, b) for a, b in list( comparaison.columns )]` appliquer une fonction à une liste en une ligne.
* `[i for i in l if i != val]` avec un if.

Séquence peut etre :

* une liste ou une chaîne de caractères (cela parcourt les lettres).
* `range(début, fin, pas)` une liste d'entier.
* `for index, val in enumerate(liste)` renvoie l'indice et la valeur.

Library : `from itertools import combinations`

* `combinations( [1, 2, 3], 2)`  combinaison d'éléments d'une liste sans redondance (il n'y aura pas la valeur '2, 2').
* `combinations_with_replacement( [1, 2, 3], 2)` combinaison avec redondance (il y aura la valeur '2, 2').

#### La boucle tant que

Les instructions sont répétées jusqu'a que ce soit la condition devienne fausse.

```
while condition:
	instruction
```

## Fonction et classe

### Déclarer une fonction 

```
def fonction (param1, param2=10):
	instruction
	return valeur
```

`=10` valeur par défaut de la variable.

!!! warning
	Les fonctions peuvent modifier des listes de type global. Il faut faire une copie avant de la donnée en argument à la fonction.

#### Fonctions récursives

Fonction qui s'appelle à elle-même.

``` python
def fct(nb):
	if nb == 0 :
		n == 0
	else :
		return nb + fct(nb)
```

### Déclarer une classe

``` python
class classe:	
	def __init__ (self):
		self.var1
	def fonction1 (self):
declarer = classe() # invoquer la classe.
```

## Le texte

* `print( message1, message2)` afficher un message. Paramètre :

	* `sep=séparateur` ajouter un séparateur. 
	* `end=text_fin` bloquer le retour à la ligne.
	* `f'texte {variable} texte {var2}'` f rend interprétable la chaine de caractère (remplacement des variables).

* `print(f"texte {variable}")` afficher un message en interprétant une variable.
* `texte[1:4]` extraire des caracètres d'une chaîne.
* `texte1 + texte2` concaténer du texte.
* `texte.strip()` supprimer les espaces au début et à la fin.
* `texte.replace('ancien', 'nouveau')` remplacer un caractère.
* `re.split('\n', texte )` transformer une chaine de caractères en liste.

Caractère 		| Définition
----------------|---------------
`\'` 			| Apostrophe
`\n` 			| Retour à la ligne
`\\` 			| backlash (\)
`\t`			| Tabulation

#### Formatage des variables en f-string 

Exemple 		| Formatage		|	 Résultat 
----------------|-----------------------|---------------
`{3.14872:.3f}` | nbre de décimale		| `3.148`
`{314872:e}`	| en puissance			| `3.148720e+05`
`{1_314_872}`	| en puissance			| `1314872`
`3:3d`			| décale les entiers	| `   3`

Example 		| Position			| Résultat
------------------------|-------------------------------|---------------
`{'texte':10}`			| décalle de 10					| `    314872`
`f"{314872:^10} mots`	| centre						| `   313     mots`
`f"{313:*^10} mots"`	| centre avec symbole			| `***313**** mots`
`f"{314872:<10} mots"`	| décalle le texte gauche		| `314872     mots`
`f"{313:>10} mots"`		| décalle à droite				| `       313 mots`

## ASCII

* `ord('Lettre')` renvoie le code ASCII.
* `chr('ASCII')` renvoie le caractère.

## Autres fonctions utiles

Fonction 		| Définition
----------------|----------------
`texte.strip()`	| supprimer les espaces
`len(texte)`	| nombre de caractères

## Les fichiers

`urllib.request.urlretrieve(url, variable)` récupérer un fichier depuis une url (`import urllib`).

### Manipuler les fichiers

`import os` 

Fonction 				| Définition
------------------------|-----------------
`remove(fichier)` 		| supprimer un fichier
`getcwd()` 				| dossier actuel
`chdir(dossier)` 		| changer le dossier par défaut
`listdir()` 			| liste des dossiers et fichiers d'une répertoire
`mkdir(nom)` 			| créer un dossier
`rmdir(dossier)` 		| supprimer un dossier
`name`					| renvoie le nom de l'os actuel
`path.exists(chemin)` 	| existence d'un répertoire ou d'un fichier
`path.basename(chemin/fichier)`	| renvoie le nom du fichier sans le chemin
`path.isfile(fichier)` 	| vérifier l'existence d'un fichier

library : `shutil`

Fonction										| Définition
------------------------------------------------|----------------------
`shutil.copy(fichier, dossier ou fichier)` 		| copier un fichier
`shutil.move( fichier, dossier_destination )`	| renommer un fichier
`shutil.rename( ancien, nouveau)` 				| renommer un fichier 

* `glob('*.extension')` lister les fichiers (`import glob`).

#### Sys

* `sys.arv` liste des arguments donner au scipt Attention `sys.argv[0]` contient le nom du script.
* `sys.exist("message")` écrire un message et arrêter du script.

### Enregistrer un fichier

``` python
open('national geographic/index.html', 'w').close()
fichier = open('journal Le Monde/index.html', "a")
fichier.write(index)
fichier.close()
```

### Alternative

```
with open("fichier.md", 'w', encoding='UTF8') as file:
	file.write(i)
```

`\n` est le séparateur entre les lignes. Attention il n'y à pas de saut à la ligne par défaut.

### Importer un fichier 

* `open('fichier.txt', 'w', encoding = 'utf-8')` ouvrir un fichier. _Rmq :_ `open` permet de créer un fichier.
L'encoding est généralement ISO-Latin-1 ou utf-8.
Paramètre :

	* `w` (write) pour écrire.
	* `a` ajouter à la fin d'un fichier.
	* `r` (read) lire.

* `fichier.write('text')` ajouter des lignes au fichier (on créer le fichier avec open).
* `fichier.close()` fermer le fichier.

Pour lire ou écrire un fichier de façon proprement (cad pour éviter les erreurs) il est conseillé d'utiliser with :

```
with open("zoo.txt", 'r') as filin:
	 # type de fichiers
```

* `filin.read()` charge tout le contenu dans une variable texte.
* `filin.readlines()` créer un élément de liste par ligne.
* `filin.readline()` renvoyer une ligne à chaque appel.
* `[ligne for ligne in filin]`  renvoie les lignes du fichier (méthode à privilégier).

Avec `w` :

* `filin.write()` ecrire dans un fichier (plusieurs instruction font aller à la ligne).

Propriétés fichier :

* `.name` renvoie le nom du fichier.

Lire et écrire un fichier simultanément :

``` python
with open("zoo.txt", 'r') as fichier1, open("vincenne.txt", 'w') as fichier2:
	# type de fichiers
	for i in fichier1.readlines():
		fichier2.write( i )
```

### Ecrire une page html

`from yattag import Doc`

``` python
doc, tag, text = Doc().tagtext()

doc.asis('<!DOCTYPE html>')
	with tag('head'):
		doc.stag('link', id="pagestyle", href="css/style.css", rel="stylesheet")
	with tag('body'):
		text('afficher')
index = doc.getvalue()
```

* `with tag('baliseHTML'):` balise qui se ferme.
* `oc.stag('baliseHTML')` balise sans fermeture. Paramètres :

	* `id=identifiant` ajouter un identifiant.
	* `klass=classe` ajouter une classe.

!!! note
	Possibilite d'inclure des boucles et des conditions à l'interieur du doc.asis

### Les images

### Bibilothèque `skimage` (scikit-image)

Package `from skimage import io`

* `io.imread("chemin")` importer une image.
* `io.imshow(monImage) ` afficher l'image.

### Bibilothèque `pillow`
Coordonné et position des pixels (x, y) correspont à (largeur, hauteur).

* `Image.open('fichier.jpg')` ouvrir une image.
* `var_img.height` récupérer la hauteur.
* `var_img.width` récupérer la largeur.
* `var_img.getpixel((x,y))` récuperer la valeur des coordonnées rgb du pixel.
* `var_img.putpixel((x,y), (r,g,b))` changer la couleur d'un pixel.
* `afficher_image(image)` afficher l'image.
* `Image.new(mode='RGB', size=(x,y))` créer une nouvelle image.

### Excel

Library `import openpyxl`

* `fichier = openpyxl.load_workbook('fichier.xlsx')` charger un fichier excel.
* `mywb = openpyxl.Workbook()` créer un workbook.
* `mywb.get_sheet_names()` afficher les noms des feuilles.
* `mywb.save('NewExcelFile.xlsx')` enregistrer le fichier.
* `wb.create_sheet(index=0, title='1st Sheet')` créer une feuille.
* `mysheet = mywb.get_sheet_by_name('feuill')` sélectionner une feuille.
* `mysheet['F6'] = 'Writing new Value!'` écrire une valeur dans une feuille donnée.

### Fichier audio

`from scipy.io import wavfile`

* `samplerate, data = wavfile.read('data/machining_sound.wav')` importer un ficier audio.

### Créer un fichier Word

Library : `from docx import Document`

* `.add_heading('Titre 1', level=1)`
* `.add_paragraph('blabla...')`
* 
	* `style='List Bullet` liste en puce.
	* `style='List Number'` liste numérotée.

* `.add_picture('monty-truth.png')` ajouter une image.

	* `width=Inches(1.25)` taille de l'image

* `.add_page_break()` saut de page.
* `paragraphe.add_run(text) = True`
  
    * `.italic`, `.bold` italique, gras.
      
* `.save('word.docx')` enregistrer le document.
* `convert("fichier.docx", destination)` convertir docx en pdf (library `docx2pdf`)

#### Ajouter un tableau

``` python
table = document.add_table(rows=1, cols=2)
hdr_cells = table.rows[0].cells
hdr_cells[0].text = 'quantité'
hdr_cells[1].text = 'Id'

for qty in records.itertuples():
    row_cells = table.add_row().cells
    for j in range(1, len(qty)) :
        row_cells[j-1].text = str( qty[j] )
```

## Interface graphique

### Déclarer une fenêtre 

`import tkinter as tk`

``` python
root = tk.Tk()
## éléments de la fenêtre 
root.mainloop()
```

* `root.title('Lanceur web')` ajouter un titre.
* `root.geometry("200x500")` préciser les dimensions de la fenêtre.

### Element de la fenêtre

`from tkinter import ttk`

1. Déclarer l'élément `bouton = ...`
2. Afficher l'élément `bouton.pack()`

Liste des éléments :

* `ttk.Button(root, text='Unice', command=fonction)` bouton.
* `ttk.Label(root, text="texte")` ajouter du texte.
* `ttk.Entry(root)` zone de saisie.

* `.grid(row=, column=)` position de l'élément.

Paramètres : 
* `width=30` largeur.

### Choisir un dossier par une fenêtre

Library : `from tkinter import Tk, filedialog`

Fonctionne hors interface tKinter

``` python
root = Tk()
root.withdraw()
root.attributes('-topmost', True)
open_file = filedialog.askdirectory()
print(open_file)
```

ou `.askopenfilename()`
* `fichier = re.search(r'((?!(/|\\)).)*$' , open_file).group(0)` le fichier.
* `dossier = open_file.replace(fichier, "")` le dossier.

### Développer avec Jupyter notebook

Recharger automatiquement un module à chaque exécution du code. Utile pour développer un module. Ne fonctionne qu'avec jupyternotebook?

```
%load_ext autoreload
%autoreload 2
```

* `%%time` renvoie le cout d'éxécution.
* `%%timeit` exécute une boucle pour mesurer en moyenne le temps d'exécution.

* `jupyter nbconvert --to html my-notebook.ipynb` exporter un jupyter en html. Nécessite `nbconvert` à installer via Pip. Paramètres :

	* `--no-input` masquer le code. 



## Configurer Python

### Déclarer une variable python dans Windows

* Copier le chemin de la licence et des programmes python.
* `Panneau de configuration\Système et sécurité\Système > Paramètre système avancé > Variable d'environnement`
* Ajouter une variable système 

	* nom : `PYTHON_HOME`
	* valeur : `chemin copié`

* Modifier la variable `Path`
* Ajouter `%PYTHON_HOME%` 

Répéter l'opération pour le sous dossier library/bin et scripts

`python` démarrer une session python.

### Jupyter notebook

!!! note
	Les chemins s'écrivent avec le `/`.

Environement de développement : Jupyter
Changer la couleur de l'environnement jupyter.

```
pip install jupyterthemes
pip install --upgrade jupyterthemes
jt -t chesterish
```
