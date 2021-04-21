# Modèle `math/set`

Le modèle `math/set` est un modèle dérivé du modèle `math/input`. Le script d'évaluation `evaluator` y est prédéfini. Il compare la réponse de l'élève à une solution attendue de type ensemble.

## Clés du modèle

* `before` (script Python). Script de génération des données et de la solution.
    * Le script doit définir une variable `sol` contenant la solution. Cette solution doit être un objet SymPy de type `FiniteSet`.

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
