# Ensembles

Le modèle `math/set` permet de fabriquer des exercices où la réponse est de type ensemble fini.

Les clés de base de ce modèles sont :

  * `question` : l'énoncé de l'exercice ;
  * `sol` : la solution.

La solution `sol` doit être un objet SymPy de type ensemble fini.

Le modèle contrôle que la réponse saisie est bien un ensemble (sans doublons). 

```
extends = /model/math/set.pl

before ==
from sympy import Intersection
A = FiniteSet(*sampleint(1, 9, randint(3, 5)))
B = FiniteSet(*sampleint(1, 9, randint(3, 5)))
sol = Intersection(A, B)
==

question ==
On considère les ensembles $! A= {{ A|latex }} !$ et $! B={{ B|latex }} !$. 
Déterminer l'ensemble suivant.
==

prefix ==
$! A \cap B =!$
==

keypad = ["emptyset"]
```

