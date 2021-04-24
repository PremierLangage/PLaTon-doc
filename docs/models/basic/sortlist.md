# Modèle `basic/sortlist`

Le modèle `basic/sortlist` permet de fabriquer des exercices où l'élève doit ordonner des items. La liste des items peut être déclarée explicitement ou générée par un script Python.

## Clés du modèle

* `title` (chaîne). Titre de l'exercice.
    * Le titre doit décrire la tâche à effectuer dans l'exercice. Il est destiné au référencement de l'exercice.
* `text` (chaîne). Enoncé de l'exercice. 
* `sortedlist` (chaîne multiligne). Items à ordonner. 
    * Chaque ligne correspond à un item. Les items doivent y être entrés dans selon l'ordre que l'élève devra retrouver (l'exercice se chargeant de les mélanger).
* `nbitems` (entier). 
    * Si la clé `nbitems` contient un entier, la liste à ordonner par l'élève sera un échantillon aléatoire de `nbitems` items de `sortedlist`. 
    * Si la clé `nbitems` vaut `null`, la liste à ordonner par l'élève contiendra tous les items de `sortedlist`.
    * Par défaut la clé `nbitems` vaut `null`.
* `scoring` (chaîne). Barème de l'exercice. 
    * Deux barèmes sont proposés : "ExactOrder" (défaut) ou "KendallTau".
* `before` (script Python). Script de génération des clés.
    * Le script doit définir une variable `sortedlist`, de type liste, contenant la liste des items (dans l'ordre souhaité). 

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
Classer ces premiers ministres de la Ve République du plus ancien 
au plus récent (selon la date d'entrée en fonction).
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
