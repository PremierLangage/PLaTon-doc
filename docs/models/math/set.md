# Modèle `math/set`

Le modèle `math/set` permet de créer des exercices dont la réponse est un ensemble fini.

## Clés du modèle

## Exemples

#### Déterminer l'intersection de deux ensembles

```
extends = /model/math/set.pl

title = Déterminer l'intersection de deux ensembles

before ==
from sympy import Intersection
A = FiniteSet(*sample(range(10), randint(3, 5)))
B = FiniteSet(*sample(range(10), randint(3, 5)))
sol = Intersection(A, B)
==

text ==
On considère les ensembles suivants :
$$ A=\\{ {{A|latex}} \\},\ B=\\{ {{B|latex}} \\}.$$

Déterminer $! A \cap B !$.
==
```
