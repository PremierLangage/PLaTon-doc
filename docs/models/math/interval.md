# Modèle `math/interval`

Le modèle `math/interval` est un modèle dérivé du modèle `math/input`. Le script d'évaluation `evaluator` y est prédéfini. Il compare la réponse de l'élève à une solution attendue de type intervalle ou réunion d'intervalles.

Attention : Les intervalles doivent, pour l'instant, être saisis en utilisant la notation parenthèse pour les bornes ouvertes.

## Clés du modèle

Les clés `title`, `text`, `input_prefix`, `solution`, `hint`, `latexsettings` ont la même signification et la même syntaxe que dans le modèle `math/input`.

* `before` (script Python). Script de génération des données et de la solution. 
    * Le script doit définir une variable `sol` contenant la solution. Cette solution doit être un objet SymPy de type `Interval` ou `Union` d'objets `Interval`.


## Exemples

```
extends = /model/math/interval.pl

title = Résoudre une inéquation produit

before ==
from sympy import solveset, S
var('x')
a, b = sample(range(-6, 6), k=2)
expr = (x + a) * (x + b)
ineq = choice([expr >= 0, expr > 0, expr <= 0,expr < 0])
sol = solveset(ineq, x, domain=S.Reals)
==

text ==
Déterminer l'ensemble des réels $! x !$ tels que $$ {{ ineq|latex }}. $$ Ecrire cet ensemble sous la forme d'un intervalle ou d'une réunion d'intervalles.
==
```
