Les bonnes pratiques de programmations doivent permettre d'obtenir un code fiable, évolutif et maintenable (pérennité). 

!!! note
    Un code est plus souvent lu que modifié.

## Nommer les fichiers 

* Pas d'espace mais `_` (éviter `moyenneAge`)
* Des noms explicts et court.

!!! examples 
    `00_download.R`, `01_explore.R`
    
## Organsation du script

* `# Load data ---------------------------` utiliser pour séparer le code.
* Pas d'espace entre pour les éléments entre parenthèse
* Un espace uniquement après les virgules.
* Se limiter à 80 caractères par ligne.
* Nommer des variables. Choisir un nom explicit :

    * Pour les variables booléennes : 

    Nom            | Type
    ---|---
    `is_fraise`    | booélen
    `bo_valide_annee` | vecteur booléen
    `chr_letters`  | texte
    `int_currency` | 1:10
    `dt_mtcars`    | dataframe
    `tbl_mtcar`    | tribble

    * Pour les constantes utiliser des majuscule : `CSTE`
 
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
    * Pour les fonctions employer des verbes : `import_data_fct()`
 
Théoriquement une fonction doit faire une seule chose. Cependant 

