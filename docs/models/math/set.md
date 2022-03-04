# Modèle `math/set`

Le modèle `math/set` est un modèle dérivé du modèle `math/input`. Le script d'évaluation `evaluator` y est prédéfini. Il compare la réponse de l'élève à une solution attendue de type ensemble.

## Clés spécifiques

<table class="table">
<thead>
<tr>
<th scope="col">Clé</th>
<th scope="col">Description</th>
<th scope="col">Type</th>
<th scope="col">Défaut</th>
</tr>
</thead>
<tbody>

<tr>
<th scope="row"> sol </th>
<td> Bonne réponse. Elle doit être définie dans le script `before` comme un objet SymPy de type FiniteSet. </td>
<td> FiniteSet </td>
<td>  </td>
</tr>

<tr>
<th scope="row"> wobracket </th>
<td> Valeur indiquant si l'ensemble doit être saisi entre accolades. </td>
<td> bool </td>
<td> 'False </td>
</tr>

</tbody>
</table>

## Exemples

### Exemple 1 : Déterminer l'intersection de deux ensembles

Adresse : `/demo/math/set/intersection.pl`

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
$! A \cap B = !$
==

keypad = ["emptyset"]
```
