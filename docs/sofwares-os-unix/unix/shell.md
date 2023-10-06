Les types de shell les plus répandus :

* sh : Bourne Shell. L'ancêtre de tous les shells.
* bash : Bourne Again Shell. Une amélioration du Bourne Shell, disponible par défaut sous Linux et Mac OS X.
* ksh : Korn Shell. Un shell puissant assez présent sur les Unix propriétaires, mais aussi disponible en version libre, compatible avec bash.
* csh : C Shell. Un shell utilisant une syntaxe proche du langage C.
* tcsh : Tenex C Shell. Amélioration du C Shell.
* zsh : Z Shell. Shell assez récent reprenant les meilleures idées de bash, ksh et tcsh.

* `#!/bin/bash` indique quel shell utiliser (ligne indispensable).
* `# commentaire` ajouter des commentaires.
* `/*commentaire*/` commentaire sur plusieurs lignes.

## Créer & Exécuter un script
	  
* `chmod +x script` donner les droits d'éxcution.
* `./script` exécuter un script.
* `bash -x sccript` afficher les détails de l'exécution.

Pour appeler un script depuis n'importe ou : déplacer le script dans un dossier "PATH". Pour afficher la liste de ces dossiers : `echo $PATH`

## Variable type texte
	  
¡Attention le Bash est trés pointieux sur les accents, espaces,...etc.!
	  
* `variable='texte'` déclarer une variable de type texte.
* `echo $variable` afficher ou appeler une variable, renvoie les paramètres qu'elle reçoit. Paramètres:
  
	* `e` activer les retours à la ligne `\n`.
	* `n nombre` coupe le message au bout d'un nombre de lettres.
	* `t nombre` limiter le temps de la saisie (en seconde).
 	*  `s` ne pas afficher le texte saisi. 

Types de quotes:

Symbole | Action
---|---
`''` | (apostrophes) affiche ce qui est contenu tel quel
`""` | (guillemets) analyse et exécute le contenu reconnu
`''` | (back quotes) demande à bash d'exécuter ce qui se trouve à l'intérieur

* `read variable variable2` demander une saisie et la stock (NB : stock un mot par variable jusqu'a la dernière qui va garder le reste). Paramètres :
  
	* `p texte variable` afficher un message pour l'utilisateur.
	
* `${#variable}` afficher la longueur d'une variable.
	
## Variable type nombre

!!! warning 
	bash ne gére pas les nombres, il faut donc utiliser la commande "let" pour les nombres entiers et "bc" pour les nombres décimaux! C'est `let "variable = valeur"` qui permet affecter à une variable un nombre.

Operateur | Défintion
---|---
`+` | addition
`-` | soustraction
`*` | multiplication
`/` | division
`**` | puissance
`%.`| modulo

## Les variables d'environnement

* `env` afficher toutes les variables d'environnement que vous avez actuellement en mémoire.
* `export` Pour définir sa propre variable ( approfondir ).

## Variables paramètres

Elles sont automatiquement créées
```
./script.sh param1 param2 param3 . 
```

Elles se nomment:

Paramétre | valeur
---|---
`$#` | Nombre de paramètres
`$0` | Nom du script exécuté
`$1` | premier paramètre
... | ... paramètre
`$9` | 9ème paramètre

## Les tableaux

* `tableau=('valeur0' 'valeur1' 'valeur2')` définir un tableau.
* `${tableau[num]}` appeler la variable d'une case d'un tableau. PS : la 1ère case est zèro.
* `tableau[num]='valeur'` définir une valeur d'une case.
* `${tableau[*]}` appeler l'ensemble d'un tableau.

## Les tests

### sur les chaînes de caractères

Opérateur | Définition
---|---
`$chaine1 = $chaine2` | identique
`$chaine1 != $chaine2` | différent ?
`-z $chaine` | chaine vide
`-n $chaine` | chaine non vide

### sur les nombres

Opérateur | Définition
---|---
`$num1 -eq $num2` | = (equal)
`$num1 -ne $num2` | = (no equal)
`$num1 -lt $num2` | < (lower than)
`$num1 -le $num2` | <= (lower or equal)
`$num1 -gt $num2` | > (greater than)
`$num1 -ge $num2` | >= (greater or equal)
 
### Sur les fichier

N'oubliez pas que sous Linux, tout est considéré comme un fichier, même un répertoire !

Opérateur | définition |
---|---|
`-e $nomfichier` | existance du fichier
`-d $nomfichier` | être un répertoire
`-f $nomfichier` | être un vrai fichier
`-L $nomfichier` | être un lien symbolique (raccourci)
`-r $nomfichier` | être lisible (r)
`-w $nomfichier` | être modifiable (w)
`-x $nomfichier` | être exécutable (x)
`$fichier1 -nt $fichier2` | plus récent (newer than)
`$fichier1 -ot $fichier2` | plus vieux  (older than)

### Les opérateurs ensemblistes

Opérateur logique | définition
---|---
`&&` | ET 
`||` | OU
`[! test]` | négation

### if : la condition la plus simple

¡ Attention, les espaces dans les crochets sont importants !
```
if [ condition1 ]; then
	instructions
elif [ condition2 ]; then
	instructions
else
	instruction
fi
```

```
case variable in
	condition1) instruction1;;
	condition2) instruction2;;
	*) instruction3;;
esac	
``` 

## Les Boucles

### Tant que c'est vrai

```
while [test] do
	instructions
done
``` 
"tant que" répéte une action jusqu'a ce que la condition ne soit plus VRAI.


### Tant que c'est  faux

```
until [test]; do
	instructions
done
``` 

### Boucle For

```
for variable in 'valeur1' 'valeur2' 'valeur3'; do
	instruction
done
```
parcourir la liste de valeurs et de boucler autant de fois qu'il y a de valeur. La liste des valeurs n'a pas besoin d'être définie dans le code.

* `seq debut pas fin` créer un vecteur a parcourrir
* `(( i = 0; i < «nbre»; i++ ))` for classique
