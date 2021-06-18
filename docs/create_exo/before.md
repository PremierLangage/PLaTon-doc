# Génération des données

Dans les exemples précédents, les clés des modèles ont toujours été définies de façon explicite. Il est également possible de générer dynamiquement ces clés à l'aide d'un script Python. Cela permet notamment de générer des données aléatoires pour l'exercice.

## Clé `before`

La clé `before`peut contenir un script Python qui est exécuté après le chargement des clés. Ce script permet de modfier ou de créer des clés. Pour modfier ou créer la clé `key`, il suffit de modifier ou créer la variable `key` dans ce script.

Par exemple, dans un fichier PL, il est équivalent d'écrire :

```
key1 = 3
key2 = [0, 1, 2]
key3 = [0, 1, 2, 3, 4, 5, 6, 7]
```

ou

```
before ==
key1 = 3
key2 = [0, 1, 2]
key3 = list(range(8))
==
```

## Insertion dynamique dans la clé `question`


## Exemple

```
extends = /model/basic/numeric.pl

before ==
from random import randint
a = randint(10, 50)
b = randint(10, 50)
sol = a + b
==

question ==
Calculer {{ a }} + {{ b }}.
==
```

## Autres exemples

Prenons l'exemple d'un exercice où il faut trouver le plus petit nombre parmi une liste de nombres. Pour ce type d'exercice, le modèle approprié est le modèle `basic\radio`.

On rappelle que dans ce modèle la liste des propositions est à entrer dans la clé `items` sous forme d'une chaîne multilignes ou d'une liste de chaînes. Avec une génération par un script Python, il est plus naturel d'utiliser le second format.

```
extends = /model/basic/radio.pl

question ==
Sélectionner le plus petit nombre de la liste suivante.
==

before ==
items = [str(x) for x in sorted(sample(range(50), 4))]
==
```
