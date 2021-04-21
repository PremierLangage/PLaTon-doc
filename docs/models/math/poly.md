# Modèle `math/poly`

Le modèle `math/poly` est un modèle dérivé du modèle `math/input`. Le script d'évaluation `evaluator` y est prédéfini. Il compare la réponse de l'élève à une solution attendue de type polynôme.

## Clés du modèle

Les clés `title`, `text`, `input_prefix`, `solution`, `hint`, `latexsettings` ont la même signification et la même syntaxe que dans le modèle `math/input`.

* `before` (script Python). Script de génération des données et de la solution. 
    * Le script doit définir une variable `sol` contenant la solution. Cette solution doit être un objet SymPy de type `Poly` ou un objet SymPy de type `Expr` convertible en polynôme.
* `poly_var` (chaîne). Variable du polynôme
    * Par défaut, la valeur de cette clé est `x`.
* `poly_form` (chaîne). Forme attendue de la réponse de l'élève.
    * Les 3 valeurs possibles sont : chaîne vide (pas de forme particulière), `expanded` (forme développée) et `factorized` (forme factorisée).
    * Par défaut, la valeur de cette clé est une chaîne vide.
* `poly_domain` (chaîne). Domaine du polynôme.
    * Cette clé est utilisée lorsque la forme attendue est une forme factorisée. Les valeurs possibles sont `R` (domaine réel) et `C` (domaine complexe).
    * Par défaut, la valeur de cette clé est `R`.

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
