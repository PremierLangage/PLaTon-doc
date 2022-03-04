# Modèle `math/complex`

Le modèle `math/complex` est un modèle dérivé du modèle `math/input`. Le script d'évaluation `evaluator` y est prédéfini. Il compare la réponse de l'élève à une solution attendue de type nombre complexe.

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
<td> Bonne réponse. Elle doit être définie dans le script `before` comme un objet SymPy de type Complex. </td>
<td> Complex </td>
<td>  </td>
</tr>

<tr>
<th scope="row"> complex_form </th>
<td> Forme attendue de la réponse de l'élève : pas de forme particulière (''), forme cartésienne ('Cartesian'), forme exponentielle ('Exponential'). </td>
<td> ('', 'Cartesian', 'Exponential') </td>
<td> '' </td>
</tr>

<tr>
<th scope="row"> imaginary_unit </th>
<td> Nom de l'unité imaginaire utilisée pour interpréter la réponse. </td>
<td> str </td>
<td> 'i' </td>
</tr>

</tbody>
</table>

## Exemples

### Exemple 1 : Multiplier deux nombres complexes

```
extends = /model/math/complex.pl

before ==
z1 = randint(-5, 5, [0]) + randint(-5, 5, [0])*I
z2 = randint(-5, 5, [0]) + randint(-5, 5, [0])*I
sol = (z1 * z2).expand()
==

question ==
On considère les nombres complexes $! z_1 = {{ z1|latex }} !$ et $! z_2 = {{ z2|latex }} !$. 

Calculer $! z_1 \times z_2 !$ (sous forme algébrique).
==

complex_form = "Cartesian"
```
