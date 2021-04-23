# Modèle `basic/sortlist`

Le modèle `basic/sortlist` permet de fabriquer des exercices où l'élève doit ordonner des items.

La liste des items peut être déclarée explicitement ou générée par un script Python.

## Clés du modèle

* `text` (string). Enoncé de l'exercice.
* `sortedlist` (string). Liste ordonnée des items. 
    * Elle peut-être déclarée comme une chaîne multilignes (chaque ligne correspondant à un item) ou une liste. Les items doivent y être entrés dans selon l'ordre que l'élève devra retrouver (l'exercice se chargeant de les mélanger).
* `nbitems` (entier). 
    * Si la clé `nbitems` est déclarée, la liste à ordonner par l'élève sera un échantillon aléatoire de `nbsample` items de `sortedlist`. 
    * Si la clé `nbsample` n'est pas déclarée, la liste à ordonner par l'élève contiendra tous les items de `sortedlist`.
* `scoring`. Barème de l'exercice. 
    * Deux barèmes sont proposés : "ExactOrder" (défaut) ou "KendallTau".

## Exemples (avec une liste déclarée explicitement)

#### Ordre alphabétique

~~~
extends = model/basic/sortlist.pl

title ==
Ordre alphabétique
==

text ==
Classer les mots suivants dans l'ordre alphabétique.
==

sortedlist ==
Abricot
Avion
Ballon
Cartable
==
~~~

#### Premiers Ministres

~~~
extends = /model/basic/sortlist.pl

title = Premiers ministres

text ==
Classer ces premiers ministres de la Ve République du plus ancien au plus récent (selon la date d'entrée en fonction).
==

nbitems % 5

sortedlist ==
Édouard Balladur
Alain Juppé
Lionel Jospin
Jean-Pierre Raffarin
Dominique de Villepin
François Fillon
Jean-Marc Ayrault
Manuel Valls
Bernard Cazeneuve
Édouard Philippe
Jean Castex
==

scoring = KendallTau
~~~

## Exemples (avec une liste générée par un script)

```
extends = /model/basic/sortlist.pl

title = Nombres

text ==
Classer les nombres suivants du plus petit au plus grand.
==

before ==
sortedlist = list(range(1, 100))
==

nbitems % 5
```
