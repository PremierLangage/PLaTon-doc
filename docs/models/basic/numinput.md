# Modèle `basic/numinput`

Le modèle `basic/numinput` permet de fabriquer des exercices à réponse numérique (entier ou nombre décimal positif).

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
<td> Bonne réponse. </td>
<td> (int, float) </td>
<td> 0 </td>
</tr>

<tr>
<th scope="row"> diffmeasure </th>
<td> Mesure utilisée pour calculer l'écart entre la réponse saisie et la réponse acceptée. </td>
<td> ('AbsError', 'RelError') </td>
<td> 'AbsError' </td>
</tr>

<tr>
<th scope="row"> tol </th>
<td> Ecart maximum (par rapport à la mesure définie dans `diffmeasure`) pour considérer une réponse comme correcte. </td>
<td> (int, float) </td>
<td> 0 </td>
</tr>

<tr>
<th scope="row"> prefix </th>
<td> Texte affiché à gauche du champ de réponse. </td>
<td> str </td>
<td> 'Réponse :' </td>
</tr>

</tbody>
</table>

## Exemples

### Exemple 1

```
extends = /model/basic/numinput.pl

question ==
Calculer la somme de 15 et 7.
==

sol = 22
```
