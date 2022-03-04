# Modèle `math/interval`

Le modèle `math/interval` est un modèle dérivé du modèle `math/input`. Le script d'évaluation `evaluator` y est prédéfini. Il compare la réponse de l'élève à une solution attendue de type intervalle ou réunion d'intervalles.

Attention : Les intervalles doivent, pour l'instant, être saisis en utilisant la notation parenthèse pour les bornes ouvertes.

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
<td> Bonne réponse. Elle doit être définie dans le script `before` comme un objet SymPy de type Interval ou Union. </td>
<td> (Interval, Union) </td>
<td>  </td>
</tr>

</tbody>
</table>

## Exemples

```
extends = /model/math/interval.pl

before ==
a = randint(1, 3)
b = randint(-3, 3)
sol = Interval(-oo, b - a)
==

question ==
Ecrire sous forme d'intervalle l'ensemble des réels $! x  + {{ a }} \le {{ b }}  !$.
==

keypad = ["-infty", "+infty"]
```
