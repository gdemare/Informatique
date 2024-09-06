## Les modes d'édition

* mode intéractif : mode par défaut qui permet de se déplacer dans le texte, de supprimer une ligne, copier-coller du texte, rejoindre une ligne précise, annuler ses actions, etc.
* mode insertion : insérer, copier,... etc.
* mode commande : mode qui permet de "enregistrer", "quitter", etc; pour y accéder taper : «:».

## Opérations basiques (mode intéractif)

* `vim fichier` créer un fichier texte.
* la navigation dans vim 

```
    ^
    k
< j   h >
    l 
    v
```

## Les commandes basiques

* `q` Quitter.
* `q!` Quitter sans enregistrer.
* `w` Enregistrer le fichier.
* `wq` Enregistrer et quitter.
* `x` Enregistrer (seulement en cas de modification) et quitter.
* `set paste` Passer en mode "collage".

## commande manipulation du text

* `i` passer en mode insertion (Echap pour quitter).
 
## Fenêtrage

* `sp` Découper l'écran horizontalement.
* `vsp` découper l'écran verticalement.

`ctrl + w` donne accès aux actions suivante :

| Touche | action |
|---|---|
| `s` | diviser horizontalement. | 
| `v` | diviser verticalement. |
| `w` | passer à la fenêtre suivante. |
| `n` | Ouvrir un fichier vierge dans une nouvelle fenêtre. |
| `q` | Fermer la fenêtre. |
| `+` | agrandit le viewport actuel. |
| `-` | réduit le viewport actuel. |
| `=` | égalise à nouveau la taille des viewports. |
| `r` | échange la position des viewports. Fonctionne aussi avec « R » majuscule pour échanger en sens inverse. |
| `j` | déplace le curseur pour aller au viewport juste en dessous. La même chose fonctionne avec les touches h, k et l que l'on utilise traditionnellement pour se déplacer dans Vim. |
