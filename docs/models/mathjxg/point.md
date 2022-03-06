# Modèle `jxg/point`

Le modèle `jxg/point` permet de fabriquer des exercices où il faut placer un point dans un panneau graphique interactif (JSXGraph).

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
<th scope="row"> xsol </th>
<td> Abscisse du point solution. </td>
<td> float </td>
<td>  </td>
</tr>

<tr>
<th scope="row"> ysol </th>
<td> Ordonnée du point solution. </td>
<td> float </td>
<td>  </td>
</tr>

<tr>
<th scope="row"> attributes </th>
<td> Paramètres du panneau graphiqe interactif. </td>
<td> dict </td>
<td> {} </td>
</tr>

<tr>
<th scope="row"> jxgscript </th>
<td> Script JSXGraph. </td>
<td> str </td>
<td>  </td>
</tr>

<tr>
<th scope="row"> pointname </th>
<td> Nom du point à placer. </td>
<td> str </td>
<td>  </td>
</tr>

<tr>
<th scope="row"> tol </th>
<td> Erreur maximum (en distance euclidienne) pour considérer une réponse comme correcte. </td>
<td> float </td>
<td> 0.1 </td>
</tr>

</tbody>
</table>

## Exemples

### Exemple 1 : Nombre complexe

Adresse : ``

```
extends = /model/jxg/point.pl

before ==
xsol = randint(-4, 4, [0])
ysol = randint(-4, 4, [0])
z = xsol + ysol*I
==

question ==
Placer le point $! M !$ d'affixe $! {{ z|latex }} !$ dans le plan ci-dessous.
==

attributes = {"showNavigation": False, "boundingbox":[-6, 6, 6, -6]}

jxgscript == #|js|
board.create('grid', [], {gridX: 1, gridY: 1});
board.create('axis', [[0, 0], [1, 0]], {name: 'Re', withLabel: true, label: {position:'urt', offset: [-5, 10]}, ticks:{visible: false}});
board.create('axis', [[0, 0], [0, 1]], {name: 'Im', withLabel: true, label: {position: 'urt', offset: [10, 0]}, ticks:{visible: false}});
var psol = board.create('point', [0, 0], {size: 2, name: 'M', color: 'blue'});
==
```
