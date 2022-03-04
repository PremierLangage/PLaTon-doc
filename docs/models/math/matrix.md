# Modèle `math/matrix`

Le modèle `math/matrix` permet de créer des exercices dont la réponse est une matrice.

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
<td> Bonne réponse. Elle doit être définie dans le script `before` comme un objet SymPy de type Matrix. </td>
<td> Matrix </td>
<td>  </td>
</tr>

<tr>
<th scope="row"> resizable </th>
<td> Valeur indiquant si le champ de réponse est redimensionnable. </td>
<td> bool </td>
<td> 'False </td>
</tr>

<tr>
<th scope="row"> initsize </th>
<td> Dimention initiale du champ de réponse. Cette clé n'est utile que si le champ de réponse est redimensionnable. Autrement, la dimension du champ de réponse matrice est automatiquement égale à la dimension de sol. </td>
<td> lst[int, int] </td>
<td> [2, 2] </td>
</tr>

</tbody>
</table>

## Exemples

### Exemple 1 : Multiplication de deux matrices

Adresse : `/demo/math/matrix/multiplication.pl`

```
extends = /model/math/matrix.pl


before ==
from randsympy import randint_matrix
n = 2
coeffbound = 3
A = randint_matrix(n, n, coeffbound)
B = randint_matrix(n, n, coeffbound)
sol = A*B
==

question ==
Soit les matrices
$$ A = {{ A|latex }} \text{ et } B = {{ B|latex }} $$ 
Calculer $! A B !$.
==

resizable = False
```
