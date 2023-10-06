Les bonnes pratiques de programmations doivent permettre d'obtenir un code fiable, évolutif et maintenable (pérennité). 

!!! note
    Un code est plus souvent lu que modifié.

## Nommer les fichiers 

* Pas d'espace mais `_`
* Des noms explicts et court.

!!! examples 
    `00_download.R`, `01_explore.R`
    
## Organsation du script

* `# Load data ---------------------------` utiliser pour séparer le code.
* Pas d'espace entre pour les éléments entre parenthèse
* Un espace uniquement après les virgules.
* Se limiter à 80 caractères par ligne.
* Nommer des variables. Choisir un nom explicit :

    * Pour les variables booléennes : `is_fraise`
    * Pour les constantes utiliser des majuscule : `CSTE`
    * Pour les fonctions employer des verbes : `import_data_fct()`
