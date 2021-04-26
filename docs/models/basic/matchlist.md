# Modèle `basic/matchlist`

Le modèle `basic/matchlist` permet de fabriquer des exercices de correspondances La liste des correspondances peut être déclarée explicitement ou générée par un script Python.

## Clés du modèle

* `title` (chaîne). Titre de l'exercice.
    * Le titre doit décrire la tâche à effectuer dans l'exercice. Il est destiné au référencement de l'exercice.
* `text` (chaîne). Enoncé de l'exercice. 
* `matches` (chaîne). Correspondances. 
    * Chaque ligne correspond à une correspondance. Les deux éléments en correspondance sont séparés par un délimiteur.
* `nbmatches` (entier ou null). 
    * Si la clé `nbitems` contient un entier, la liste à ordonner par l'élève sera un échantillon aléatoire de `nbmatches` items de `sortedlist`. 
    * Si la clé `nbitems` vaut `null`, la liste des correspondances sera égale à `matches`.
    * Par défaut la clé `nbmatches` vaut `null`.
* `scoring` (chaîne). Barème de l'exercice. 
    * Barèmes proposés :
* `before` (script Python). Script de génération des clés.
    * Le script doit définir une variable `matches` contenant les correspondances, sous forme d'une liste de listes de deux chaînes. 

## Exemples (avec une liste déclarée explicitement)

#### Capitales

~~~
extends = /model/basic/matchlist.pl

title = Capitales

text ==
Relier chaque pays à sa capitale.
==

matches ==
France,Paris
Italie,Rome
Allemagne,Berlin
Espagne,Madrid
==
~~~

## Exemples (avec une liste générée par un script)

```
extends = /model/basic/matchlist.pl

title = Décomposition de nombres

text ==
Relier chaque nombre à la décomposition qui lui est égale.
==

before ==
from random import randint, sample
matches = []
for a in sample(range(10, 20), 4) :
    b = randint(1, a-1)
    c = a - b
    matches.append([str(a), f"{b} + {c}"])
==
```
