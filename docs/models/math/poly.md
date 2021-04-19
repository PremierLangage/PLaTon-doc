# Modèle `math/poly`

Le modèle `math/poly` est un modèle dérivé du modèle `math/input`. Le script d'évaluation `evaluator` y est prédéfini. Il compare la réponse de l'élève à une solution attendue de type polynôme.

## Clés du modèle

* `poly_form` (chaîne). Forme attendue de la réponse de l'élève.
    * Les 3 valeurs possibles sont : chaîne vide (pas de forme particulière), `expanded` (forme développée) et `factorized` (forme factorisée).
    * Par défaut, la valeur de cette clé est une chaîne vide.


## Exemples

#### Développer une expression polynomiale

~~~
extends = /model/math/poly.pl

title = Développer une expression polynomiale

before ==
from randsympy import randint_poly
P = randint_poly(1, 2, 2)
Q = randint_poly(1, 2, 2)
expr = P * Q
sol = expr.expand()
==

text ==
Développer l'expression suivante :

$$ {{ expr|latex }}. $$
==

poly_form = expanded
~~~
