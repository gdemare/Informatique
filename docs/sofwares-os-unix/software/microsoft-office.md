## Word

### Table des figures

#### Ajouter une table des figures

1. Insérer la table `Onglet Références > Insérer une Table des illustrations`.
2. Ajouter des éléments `Selectionner l'élément > insérer une légende`.

#### Actualiser la numérotation des légendes

1. Appuyez sur Ctrl-A pour sélectionner tout le texte du document.
2. Appuyez sur F9.

Ou sinon en passant par l'onglet référence.

### Sommaire 

#### Police du sommaire

1. Onglet Références du ruban, cliquez sur `Table des matières > Table des matières personnalisée`.
2. Dans la boîte de dialogue `Modifier`.

#### Accentuation des majuscules

1. `Fichier > options > vérification`.
2. Cocher `majuscules accentuée en francais`.

### Changer le début de la numérotation des pages 

Pour choisir à partir de quelle page commencer la numérotation, il faut :

1. Déclarer des sections : `Mise en Page > Sauts de page > Page suivante`
2. Faire débuter la numérotation à partir de la section concernée :
   
	1. Insérer le numéro des pages.
	2. Dans En-tête et pied de page.
	3. Dans `Numéro des pages` > `Format des numéros des pages`.
	4. `Numérotation des pages` > `à partir de` numéro de section.

### Bibliographie 

1. Lister les sources : `Référence` > `Gérer les sources`
2. Ajouter une référence dans le texte : `Référence` > `Insérer une citation`

Pour la numérotation, choisir :

* IEEE pour avoir [1].

## Outlook

### Ajouter une règle

`Accueil > Déplacer > Régle créer une régle` créer une régle.

### Changer la période des email hors ligne

1. `Fichier > Informations > Paramètre du compte`.
2. Selectionner l'adresse.
3. Modifier.
4. Changer la période des courriers à télécharger hors connexion.

### Exporter un dossier 

!!! note
	Penser à changer la période pour avoir tout les emails.

1. `Fichier > Ouvrir et exporter > Importer/exporter`
2. Exporter les données vers un fichier

### Message d'absence automatique

1. Créer un email.
2. L'enregistrer sous au format Modèle Outlook.
3. Créer une régle :

	* Répondre en utilisant le modèle.

## PowerPoint

### Barre de progression 

Afficher une barre de progression. 

1. Créer une macro.
2. Coller le code :
	```
	On Error Resume Next
	With ActivePresentation
	For X = 1 To .Slides.Count
	.Slides(X).Shapes("PB").Delete
	Set s = .Slides(X).Shapes.AddShape(msoShapeRectangle, _
	0, .PageSetup.SlideHeight - 12, _
	X * .PageSetup.SlideWidth / .Slides.Count, 12)
	s.Fill.ForeColor.RGB = RGB(0, 0, 0)
	s.Name = "PB"
	Next X:
	End With
	```
