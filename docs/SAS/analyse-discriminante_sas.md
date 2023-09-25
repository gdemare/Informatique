```
PROC DISCRIM <option>; 
    CLASS variableId;
    <VAR variables;>
RUN;
```

## Option

* `TESTDATA=data` jeu de test.
* `POOL=yes/no` variance égale.
* `METHOD=normal/npar` considère que les variables suivent une loi normale (sinon non paramétrique).
* `CROSSLISTERR` afficher les observations ou le modèle s'est trompé.

```
PROC FACTOR <option>;
RUN;
```

## Option

### Affichage

* `CORR` afficher la mactrice de corrélation de

### Selection des axes

* `MINEIGEN=valeur` valeur propre minimum pour retenir le facteur.
* `NFACTORS=nombre` nombre d'axes à conserver.
* `PROPORTION=proportion` proportion minimum de variance à retenir.
