Les bonnes pratiques de programmations doivent permettre d'obtenir un code fiable, évolutif et maintenable (pérennité). 

!!! note
    Un code est plus souvent lu que modifié.

## Nommer les fichiers 

* Préférer avec la méthode snake (ma_fonction) à la place de camel (maFonction).
* Des noms explicites et courts.
* Ajouter un numéro pour les éléments ordonnés (`00_download.R`, `01_explore.R`).
    
## Organisation du script

* Utiliser des séparateurs dans le code pour distinguer les différentes parties (`#--------------`).
* Pas d'espace entre pour les éléments entre parenthèse.
* Un espace uniquement après les virgules.
* Se limiter à 80 caractères par ligne.
* Nommer avec la méthode snake (ma_fonction) à la place de camel (maFonction).

### Variable

Nommer des variables avec un nom explicite et en anglais :

Nom                | Type
-------------------|---
`is_fraise`        | booélen
`bo_valide_annee`  | vecteur booléen
`chr_letters`      | texte
`int_currency`     | 1:10
`df_mtcars`        | dataframe
`dt_iris`          | data

* Pour les constantes utiliser des majuscule : `CSTE`

### Foncions

* Employer des verbes : `import_data_fct()`.
* Pour les fichiers avec une seul fonction, nommer le fichier comme la fonction.

### R

* [Bonnes pratiques git R](https://inseefrlab.github.io/formation-bonnes-pratiques-git-R/) par l'INSEE.
* [Mastering Shiny](https://mastering-shiny.org/index.html) livre de référence sur le développement d'applations Shiny.
* [Les bonne pratiques de développement R](https://docs.sk8.inrae.fr/074-bonnespratiquesR.html) par l'INRAE.
* [Package Bookdown](https://bookdown.org/) ecrire des livres (et de la documentation avec R).
* [Golem](https://github.com/ThinkR-open/golem), optimise le développement des applications shiny.
* [roxygen2](https://github.com/r-lib/roxygen2), doc sur les fonctions R.
* [the Book of Apps for Statistics Teaching (BOAST)](https://educationshinyappteam.github.io/), bouquin portait sur le développement d'applications R Shiny qui semble assez complet.

Utilise # load data -------------------------
# =============================
Pour séparer le code et les rendre plus facilement lisibles
Package a charger au début du script
Max 80 caractère par ligne
Pour le texte utilisé " à la palce de '
Fonction sans argument = sans ()

Rmd first : Quand le developpement commence par la documentation - Rtask (thinkr.fr) (a lire)
Versioned via git
Documented via rmarkdown
Tester via test that

Éviter setwd()
Utiliser des chemins relatif avec la fonction here() du package here
Usethis::proj_sitrep() permet de vérifier que tous est installer correctement.

Comment nommer les choses explicitement : What They Forgot to Teach You About R - 5  How to name files (rstats.wtf)

Environnement reproductible https://thinkr.fr/dockeriser-application-shiny/

Histoorer les versions 

Sauvegarder et gérer les différentes versions (permet notamment de revenir en arrière en cas de pb).
Garder uentrace de l'historique des modif
Permet un travaill collaboratif en permettant de savoir qui a fait les modfi et pourquoi. Fusionner le travail de plusierus personnes sans perdre de l'information

A utiliser dans le cas de developpement de package R
Transformer un dossier en projet git synchronisé sur Github ou Gitlab - Rtask (thinkr.fr)
https://rtask.thinkr.fr/fr/quand-le-developpement-commence-par-la-documentation/

### Python

```
def multiplie_nombres(nombre1, nombre2):
"""Multiplication de deux nombres entiers.

Cette fonction ne sert pas à grand chose.

Parameters
----------
nombre1 : int
    Le premier nombre entier.
nombre2 : int
    Le second nombre entier.

    Avec une description plus longue.
    Sur plusieurs lignes.

Returns
-------
int
    Le produit des deux nombres.
"""
return nombre1 * nombre2
```

Controler la qualité de son code soit en ligne `pep8online` soit avec des library comme 

* `pycodestyle` pour le code.
* `pydocstyle` pour la doctring (documentaiton).
* `pylint` comprend le contexte du code et propose des éléments d'amélioration.


