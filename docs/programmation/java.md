`import bibliothéque;` importer une bibliothèque 

## Installer les outils de développement

* `System.out.println('texte');` afficher du texte . 

| Symbole | Action |
|---|---|
| `\n` | retour à la ligne | 
| `\t` | tabulation |

* `print("text" + variable)` afficher la valeur d'une variable.
 
 ## Les variables et les opérateurs

```
type variable ;
``` 

`variable = valeur<type>`  
`type variable=valeur <, var2=val2>`
déclarer un variable.

Type de variables :

| Type | définition | Type |
|---|---|---|
| byte | entiers entre -128 et +127 | |
| short | entiers entre -32768 et +32767 | |
| int | entiers entre -2*10^9 et 2*10^9 | |
| long | entiers entre -9*10^18 et 9*10^18 | L |
| float |  nombres décimaux | f |
| double | nombres décimaux plus grand que float | d |
| char | caractère `'chaine'` | |
| boolean | boléen `true` ou `false` | |
| String | chaîne de caractère |

## Opérateurs

| Opérateur arithmétique | |
|---|---|
| `+` | addition |
| `-` | soustraction |
| `*` | multiplication |
| `/` | division |
| `%` | modulo |

* `type variable = nv_type variable` convertir de variable dans un autre type. 
						
## Lire les entrées clavier 

 Bibliothèque `java.util.Scanner` 

* `sc = new Scanner(System.in);` lire l'entré clavier.
* `sc.nextLine()` résultat de la saisie.
* `sc.nextLine()` vider la variable.

## Les conditions

```
if(condition){
	instruction;
}
else if(){
	instruction;
}
 else {
	instruction; 
 }
```
 
```
switch (variable)
{
	case valeur: 
		instruction;
	break;
	default:
		instruction;
}
```

Appliquer des régles selon les différentes valeurs de la variable (NB les variables de type float, double ne sont pas acceptés).

## Opérateurs
 
| Opérateurs | |
|---|---|
| `==` | égalité |
| `!=` | inégatilé |
| `<` | strictement inférieur |
| `=<` | inférieur ou égal |

| Opérateur logique | |
|---|---|
| `&&` | et|
| `||` | ou |
| `?` | temaire |

## Déclarer un tableau

* `type tableau[] = new int[nbre]` déclarer une variable-tableau vide avec nbre de colonnes.
* `type tableau[][] = { {ligne1} , {ligne2} }` déclarer un tableau à 2 lignes, N colonnes.

## Fonction chaîne de caractères
```
variable.fonction()
```

| Fonction | Action |
|---|---|
| `.toLower.Case()` | transformer une chaîne de caractères en minuscule |
| `.toUpper.Case()` | transformer une chaîne de caractères en majuscule |
| `.length()` | compter le nombre de caractères |
| `.equals(chaine)` | comparer les 2 chaînes de caractéres |
| `.substring(nbre1,nbre2)` | extraire les caractéres contenu en le caractére nombre1 et nombre2 |
| `.indexOf('chaine')` | renvoyer la position de la chaîne |
| `.indexOf('chaine')` | renvoyer la position de la chaîne |

## Fonctions mathématiques

Bibliothéque `java.lang`

| Fonction | Action |
|---|---|
| `Math.random()` | retourner un nombre alèatoire entre 0 et 1 |
| `Math.cos(nbre)` | cosinus |
| `Math.sin(nbre)` | sinus |
| `Math.tan(nbre)` | tangante |
| `Math.abs(nbre)` | valeur aboslue |
| `Math.pow(nbre,exposant)` | exposant |

```
9/ static «variable» «nom»(«variable1» «nom1»,«variable2» «nom2»){
«instructions»
return «variable» «résultat»;
} : déclarer une classe qui renvoie le résultat 


void «variable» «nom»(«variable1» «nom1»,«variable2» «nom2»){
«instructions»
}
```