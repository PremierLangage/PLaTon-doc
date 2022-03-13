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

### Exemple 1

```
extends = /model/math/interval.pl

keypad = ["-infty", "+infty"]

before ==
a = choice([0, 1, -oo])
b = choice([3, 5, oo])
left_open = choice([True, False])
right_open = choice([True, False])
sol = Interval(a, b, left_open, right_open)
==

question ==
Entrer l'intervalle $! {{ sol|latex }} !$.
==
```

