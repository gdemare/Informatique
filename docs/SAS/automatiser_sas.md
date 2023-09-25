## Les macro-variables

* `%PUT &var. ;` afficher une macro variable.
* `%LET nomVariable = valeur ;` déclarer une macro-variable.

Pour les opérations sur les nombres utiliser la fonction `%EVAL(formule)`.

Stocker plusieurs variables :

* `%LET semaine = lundi - mardi - mercredi - jeudi - vendredi - samedi - dimanche;`
* `%LET jour2 = %SCAN(&semaine,2,’-’) ;`

Résultat :

* `INTO :variable <option>` mettre les résultat dans une macro dans une PROC SQL).
  * `SEPARATED 'symbole'` stocker plusieurs valeurs.
* `CALL SYMPUT` mettre les résultat dans une macro pour les étapes DATA.

## Les macro-programmes
```
%MACRO nomMacro (param1, param2);
corps ;
%MEND nomMacro;
```

```
Appeler un macro-programme : %nomMacro ( ¡param1 =¿ val1, ¡param2 =¿
val2 )
```

## Les macro-instructions

```
%IF condition %THEN %DO ; instruction ; %END ;
<%ELSE %IF condition2 %THEN %DO ; instruction2 ; %END ;>
<%ELSE %DO ; instruction ; %END ;>
```


```
%DO i=1 %TO 5;
  instruction;
 %END;
```

## Les macro-fonctions

* `%EVAL(calcul)` calculer une variable numérique.
* `%SYSFUNC(fonction)` utiliser une fonction dans les macro variables.
