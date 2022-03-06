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

## Détails

### `jxgscript`

Ce script permet de créer les objets graphiques du panneau JSXGraph. Ce panneau est déjà créé et porte le nom `board`. Le point à placer doit être créé sous la forme d'une variable `psol`.

## Exemples

### Exemple 1 : Nombre complexe

Adresse : `/demo/jxg/point/complex.pl`

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

tol = 0.2

pointname = "M"

jxgscript == #|js|
board.create('grid', [], {gridX: 1, gridY: 1});
board.create('axis', [[0, 0], [1, 0]], {name: 'Re', withLabel: true, label: {position:'urt', offset: [-5, 10]}, ticks:{visible: false}});
board.create('axis', [[0, 0], [0, 1]], {name: 'Im', withLabel: true, label: {position: 'urt', offset: [10, 0]}, ticks:{visible: false}});
var psol = board.create('point', [0, 0], {size: 2, name: 'M', color: 'blue'});
==
```

### Exemple 2 : Angle

Adresse : `/demo/jxg/point/angle.pl`

```
extends = /model/jxg/point.pl

before ==
angle = choice([pi/4, pi/2, 3*pi/4, pi, 3*pi/2])
xsol = cos(angle).evalf()
ysol = sin(angle).evalf()
==

question ==
Placer le point M de sorte que l'angle $! (\overrightarrow{OA},\overrightarrow{OM}) !$ ait une mesure égale à $! \displaystyle {{ angle|latex }} !$. 
==

attributes = {"showNavigation": False, "boundingbox":[-1.25, 1.25, 1.25, -1.25]}

tol = 0.05

pointname = "M"

jxgscript == #|js|
var circle = board.create('circle', [[0, 0], [0, 1]], {strokeColor: 'blue', fixed: true});
var O = board.create('point', [0, 0], {size: 1, name: 'O', color: 'black', fixed: true});
var A = board.create('point', [1, 0], {size: 1, name: 'A', color: 'black', fixed: true});
var psol = board.create('glider', [1, 0.5, circle], {size: 2, name: 'M', color: 'blue', fixed: false});
var secOAM = board.create('sector', [O, A, psol], {color: 'orange'});
==
```
