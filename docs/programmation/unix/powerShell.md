Extension `fichier.ps1`.

Actvier l'exécution de scripts PowerShell dans Windows (admin) : `set-executionpolicy unrestricted`

## Opérateur 

`instruction1 | instruction2` rediriger la sortie de l'instruction 1 vers la 2.

## Les boucles et les conditions

### Pour

```
For ($i=0 ; $i -le 10 ; $i++) {
	echo $i
}
```

```
foreach ($i in liste) {
	echo $i
}
```

### Si

``` 
If (condition1) { 

} elseif (condition2) { 

} else { 

}
```

## Les variables

### Les variables systèmes

* `$PSCommandPath` chemin du script en cours.

### Déclarer une variable

* `$variable=valeur` créer une variable.
* `$variable` appeler une variable.

### Information sur les variables

* `variable.Lenght` taille de la chaine de caractères.
* `liste.Count` nombre d'éléments d'une liste.

## Les commentaires

* `<#commentaire#>`
* `#commantaire`

### Les chaines de caractères

* `texte.LastIndexOf("\")` position du dernier symbole.
* `$test.Substring(position)` extrait les caractères de la chaine situés après la position.

## Fichiers et dossier 

* `Set-Location "chemin"` modifier le chemin par défaut.
* `gci` liste des fichiers. Paramètre : 

	* `-fi` lister uniquement les fichiers.
	* `-r` lister en plus les fichiers des sous dossiers.

* `Get-Item fichier` 
* `select fichier` Paramètre :
	
	* ` -Property` récupérer les propriétés d'un fichier. Lorsqu'il y en a plusieurs, il faut les séparer par un `,` (`fullName`, ` LastWriteTime`).

* `ri chemin` supprimer des fichiers.

	* `dossier -Recurse` supprime les fichiers et les dossiers.
	* `-Force` suppimer de façon récursive.

* `gci -r -fi *psm*.xlsx | ri -Force` trouver des fichiers et les supprimer de façon récursive.
* `Invoke-Expression comande` exécuter une commande.
* `Read-Host "message"` récupérer une entré utilisateur.