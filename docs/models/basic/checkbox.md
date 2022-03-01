# Modèle `basic/checkbox`

Le modèle `basic/checkbox` permet de fabriquer des exercices à choix multiple (avec plusieurs items à sélectionner).

## Clés spécifiques du modèle

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
<th scope="row"> items </th>
<td> Liste des items. Elle peut être saisie comme une liste ou comme une chaîne multilignes (chaque ligne correspondant à un item). </td>
<td> (str, list[str]) </td>
<td> [] </td>
</tr>

<tr>
<th scope="row"> indsol </th>
<td> Indice des solutions dans la liste des items (la numérotation commence à 0). </td>
<td> list[int] </td>
<td> [] </td>
</tr>

<tr>
<th scope="row"> shuffled </th>
<td> Valeur indiquant si les items seront mélangés. </td>
<td> bool </td>
<td> True </td>
</tr>

<tr>
<th scope="row"> scoring </th>
<td> Barème de l&#39;exercice. </td>
<td> (&#39;AllOrNothing&#39;, &#39;RightMinusWrong&#39;, &#39;CorrectItems&#39;) </td>
<td> &#39;RightMinusWrong&#39; </td>
</tr>

</tbody>
</table>

## Exemples (avec déclaration explicite des items)

```
extends = /model/basic/checkbox.pl

question ==
Parmi ces villes, lesquelles ne sont pas des capitales ?
==

items ==
Barcelone
Milan
Paris
Berlin
==

indsol = [0, 1]
```
