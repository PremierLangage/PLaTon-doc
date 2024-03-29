# Premier exemple

Le modèle `math/expr` permet de fabriquer des exercices aléatoires où la réponse est une expression mathématique (expression impliquant des nombres, des variables, des opérations algébriques et des fonctions).

Les clés de base de ce modèle sont :

  * `question` : l'énoncé de l'exercice ;
  * `sol` : la solution.

La solution `sol` doit être un objet SymPy de type expression mathématique. Elle ne peut donc être produite que dans le script `before`.

```
extends = /model/math/expr.pl

before ==
from sympy import diff
var('x')
f = x**2 * sin(x)
sol = diff(f, x)
==

question ==
Calculer la dérivée de la fonction 
$$ f : x \mapsto {{ f|latex }} .$$
==
```
