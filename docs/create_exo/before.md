# Génération dynamique des clés

Dans les exemples précédents, les clés des modèles ont toujours été définies de façon explicite. Il est également possible de générer dynamiquement des clés à l'aide d'un script Python (à placer dans la clé `before`). Cela permet en particulier de générer des données aléatoires pour l'exercice.

## Clé `before`

La clé `before` est facultative. Si un script est entré dans cette clé, il est exécuté après le chargement des clés du fichier PL et avant la construction de la page de l'exercice. Toutes les clés du fichier PL sont utilisables et modifiables dans le script (une clé correspond simplement à la variable de même nom dans le script). Toute variable créée dans le script est ensuite convertie en clé de l'exercice (avec le même nom).

**Exemple**. Les deux codes PL suivants aboutissent à la création des mêmes clés :

```
n1 = 3
n2 = 5
lst1 = [0, 1, 2]
lst2 = [0, 1, 2, 3, 4, 5, 6, 7]
```

ou

```
n1 = 3
n2 = 2

before ==
n2 = key1 + key2
lst1 = [0, 1, 2]
lst2 = list(range(8))
==
```

La version de Python utilisée est la version 3.8.

## Insertion dynamique dans la clé `question`


## Exemple

L'exemple que nous allons considérer est un exercice très simple d'addition. On demande de calculer la somme de deux entiers tirés aléatoirement (entre 10 et 49). La réponse doit être rentrée dans un champ de réponse numérique.

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
