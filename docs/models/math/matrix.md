# Modèle `math/matrix`

Le modèle `math/matrix` permet de créer des exercices dont la réponse est une matrice.

* Le champ de réponse permet de saisir facilement une matrice. 

## Clés du modèle

* `before` (script Python). Script de génération des données et de la solution.
    * Le script doit définir une variable `sol` contenant la solution. Cette solution doit être un objet SymPy de type `Matrix`.
* `resizable`
* `size`

## Exemples

####

```
extends = /model/math/matrix.pl

title = Multiplier des matrices $! 2 \times 2 !$

before ==
from randsympy import rand_int_matrix
n = 2
coeffbound = 3
A = rand_int_matrix(n, n, coeffbound)
B = rand_int_matrix(n, n, coeffbound)
sol = A*B
==

text ==
Soit les matrices
$$ A = \left( {{ A|latex }} \right) \text{ et } B = \left( {{ B|latex }} \right) $$ 
Calculer $! A B !$.
==

resizable % false
```
