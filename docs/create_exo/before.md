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

La version de Python utilisée est la version 3.7. Tous les modules de la [bibliothèque standard](https://docs.python.org/fr/3/library/index.html) peuvent être importés. D'autres modules usuels, ainsi que des modules propres à la plateforme, sont également disponibles.

**Exemple**
```
before ==
from random import uniform
from math import pi, sin, cos
angle = uniform(0, pi/2)
x = cos(angle)
y = sin(angle)
==
```


## Insertion dynamique dans la clé `question`

Pour insérer dynamiquement les données générées par le script `before` dans l'énoncé de l'exercice, la clé `question` admet un système de **template**. Le contenu d'une clé `key`, définie explicitement ou dynamiquement dans le script `before`, peut être inséré dans la clé `question` en utilisant l'expression `{{ key }}`.


**Exemple**

```
before ==
from random import choice
capitale = choice(["Paris", "Berlin", "Rome"])
==

question ==
Quel pays a pours capitale {{ capitale }} ?
==
```

## Un exemple d'exercice aléatoire

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
