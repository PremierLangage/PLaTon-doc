# Modèle `math/poly`

Le modèle `math/poly` est un modèle dérivé du modèle `math/input`. Le script d'évaluation `evaluator` y est prédéfini. Il compare la réponse de l'élève à une solution attendue de type polynôme.

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
<td> Bonne réponse. Elle doit être définie dans le script `before` comme un objet SymPy de type Expr ou Poly. </td>
<td> (Expr, Poly) </td>
<td>  </td>
</tr>

<tr>
<th scope="row"> poly_form </th>
<td> Forme attendue de la réponse : pas de forme particulière (''), forme développée ('Expanded'), forme factorisée ('Factorized'). </td>
<td> ('', 'Expanded', 'Factorized') </td>
<td> '' </td>
</tr>

<tr>
<th scope="row"> poly_domain </th>
<td> Domaine du polynôme : réels ('R'), complexes ('C'). </td>
<td> ('R', 'C') </td>
<td> 'R' </td>
</tr>

<tr>
<th scope="row"> poly_var </th>
<td> Variable du polynôme. Si cette clé vaut None, la variable est détectée automatiquement. </td>
<td> (str, None) </td>
<td> None </td>
</tr>

</tbody>
</table>
            

## Exemples

### Exemple 1 : Développer une expression polynomiale

Adresse : `/demo/math/poly/expansion.pl`

~~~
extends = /model/math/poly.pl

before ==
x = Symbol('x')
P = randint(-3, 3, [0])*x + randint(-3, 3, [0])
Q = randint(-3, 3, [0])*x + randint(-3, 3, [0])
expr = P * Q
sol = expr.expand()
==

question ==
Développer l'expression suivante :
$$ {{ expr|latex }}. $$
==

poly_form = "Expanded"
~~~

### Exemple 2 : Factoriser une expression polynomiale

Adresse : `/demo/math/poly/factorization.pl`

```
extends = /model/math/poly.pl

before ==
x = Symbol('x')
P = x + randint(-2, 2)
Q = x + randint(-2, 2)
sol = P * Q
expr = sol.expand()
==

question ==
Factoriser l'expression suivante :
$$ {{ expr|latex }}. $$
==

poly_form = "Factorized"
```
