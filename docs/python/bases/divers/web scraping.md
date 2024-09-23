Package `bs4` et `requests`

## Charger les library

```
import requests
from bs4 import BeautifulSoup
```

## Récupérer la page

```
page = requests.get("https://www.")
soup = BeautifulSoup(page, 'html.parser')
```

Obtenir le code html d'une page web. Dans le cas où l'url ne se termine par pas .html ajouter `page.text`.

## Filtrer les elements

* `find(filtre)` trouver le premier élément. Le résultat est une variable.
* `findAll(filtre)` ou `find_all()` trouver tous les éléments. Le résultat est une liste.

### Condition possible

Code 									| Elément 					| Exemple
----------------------------------------|---------------------------|----------------
`id='id'` ou `class_='classe'`			| id ou classe				| 
`'baliseHtml'` 							| balise Html				| `'section'`
`'baliseHtml', {'class' : 'classe'}`	| balise avec la classe		| 

Plusieurs éléments :

* `[element1, element2]` ou 
* `{element1, elelemt 2}` unique

!!! example
    ```
    sommaire.find('a', {'class' : 'teaser__link'}, href=True)
    lien['href']
    ```

* `element.get_text()` récupérer le contenu de la balise.
