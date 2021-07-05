# Nombres complexes

Le modèle `math/complex` permet de fabriquer des exercices où la réponse est de type nombre complexe.

Par défaut, le modèle contrôle que la réponse saisie est un nombre complexe, mais il n'impose aucune forme particulière pour ce nombre. La clé `complex_form` permet d'imposer une forme cartésienne (`cartesian`) ou exponentielle (`exponential`).

**Exemple**

```
extends = /model/math/complex.pl

before ==
z1 = randint(-3, 3, [0]) + randint(-3, 3, [0])*I
z2 = randint(-3, 3, [0]) + randint(-3, 3, [0])*I
sol = (z1 * z2).expand()
==

question ==
On considère les nombres complexes $! z_1 = {{ z1|latex }} !$ et $! z_2 = {{ z2|latex }} !$. 
Calculer $! z_1 \times z_2 !$ (sous forme algébrique).
==

complex_form = cartesian
```
