# Modèle `basic/dropgroup`

Le modèle `basic/dropgroup.pl` permet de fabriquer des exercices avec des étiquettes à placer. Le placement des étiquettes et des zones de dépôt dans l'énoncé se fait par un système de balises.

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
<th scope="row"> nbdrops </th>
<td> Nombre de zones de dépôt créées. Si cette clé vaut None, le nombre de zones créées est le nombre d&#39;items de la clé `sol` </td>
<td> (int, None) </td>
<td> None </td>
</tr>

<tr>
<th scope="row"> sol </th>
<td> Liste des valeurs attendues dans les zones de dépôt. Elle peut être saisie comme une liste ou comme une chaîne multilignes (chaque ligne correspondant à un item). </td>
<td> (str, list[str]) </td>
<td> [] </td>
</tr>

<tr>
<th scope="row"> labels </th>
<td> Liste d&#39;étiquettes supplémentaires. Elle peut être saisie comme une liste ou comme une chaîne multilignes (chaque ligne correspondant à un item). </td>
<td> (str, list[str]) </td>
<td> [] </td>
</tr>

<tr>
<th scope="row"> shuffled </th>
<td> Valeur indiquant si les étiquettes seront mélangées. </td>
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


## Exemples

```
extends = /model/basic/dropgroup.pl

question ==
Compléter les phrases suivantes avec les étiquettes proposées.
==

sol ==
ces
c'est
ces
==

inputblock == #|html|
* Je voudrais {{ input.drops[0]|component }} chausures pour mon anniversaire.
* Tu est toujours en retard, {{ input.drops[1]|component }} agaçant !
* Je n'aime pas {{ input.drops[2]|component }} méthodes.

{% for label in input.labels %} {{ label|component }} {% endfor %}
==
```
