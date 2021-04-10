# Modèle `math/complex`

Le modèle `math/complex` est un modèle dérivé du modèle `math/input` pour des exercices où la réponse est unique et de type nombre complexe. Le script d'évaluation y est prédéfini.

## Clés du modèle

* `imaginary_unit` (chaîne, valeur par défaut : `i`). Nom de l'unité imaginaire.
* `complex_form`

## Exemples

#### Multiplier deux nombres complexes

```
extends = /model/math/complex.pl

title = Multiplier deux nombres complexes

before ==
z1 = randint(-5, 5, [0]) + randint(-5, 5, [0])*I
z2 = randint(-5, 5, [0]) + randint(-5, 5, [0])*I
sol = (z1 * z2).expand()
==

text ==
On considère les nombres complexes $! z_1 = {{ z1|latex }} !$ et $! z_2 = {{ z2|latex }} !$. 

Calculer $! z_1 \times z_2 !$ (sous forme algébrique).
==

complex_form = cartesian
```
