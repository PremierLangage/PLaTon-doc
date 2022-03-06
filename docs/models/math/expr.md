# Modèle `math/expr`

Le modèle `math/expr` permet de fabriquer des exercices aléatoires où la réponse est une expression mathématique (expression impliquant des nombres, des variables, des opérations algébriques et des fonctions).

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
<td> Bonne réponse. Elle doit être définie dans le script `before` comme un objet SymPy de type Expr. </td>
<td> Expr </td>
<td>  </td>
</tr>

<tr>
<th scope="row"> equality </th>
<td> Type d'égalitée utilisé : égalité stricte (''), égalité à une constante près ('UpToConstant'), égalité modulo un nombre ('Modulo'). </td>
<td> ('', 'UpToConstant', 'Modulo') </td>
<td> '' </td>
</tr>

<tr>
<th scope="row"> modulo </th>
<td> Nombre utilisé dans le cas d'une égalité modulo un nombre. </td>
<td> (int, float) </td>
<td> 0 </td>
</tr>

</tbody>
</table>


## Exemples

#### Calculer la distance entre deux points du plan

```
extends = /model/math/expr.pl

title = Calculer la distance entre deux points du plan

before ==
xA = randint(-5, 5)
yA = randint(-5, 5)
xB = randint(-5, 5)
yB = randint(-5, 5)
sol = sqrt((xA-xB)**2 + (yA-yB)**2)
==

question ==
Dans le plan muni d'un repère orthonormé on considère les points de coordonnées 
$! ( {{ xA }}, {{ yA }} ) !$ et $! ( {{ xB }}, {{ yB }} ) !$.

Quelle est la distance entre ces deux points ?
==
```

#### Exprimer une inconnue en fonction d'une autre

```
extends = /model/math/expr.pl

title = Exprimer une inconnue en fonction d'une autre

before ==
var('x y')
a = randint(-5, 5, [0])
b = randint(-5, 5, [0])
expr = a*y+b
sol = (x-b)/a
==

text ==
Soit deux nombres $! x !$ et $! y !$ tels que :
$$ x = {{ expr|latex }}.$$

Exprimer $! y !$ en fonction $! x !$.
==

input_prefix = $! y = !$
```

#### Valeurs remarquables de sinus et cosinus

```
extends = /model/math/expr.pl

title = Valeurs remarquables de sinus et cosinus

before ==
x = choice([pi/6, pi/4, pi/3, 3*pi/4, 2*pi/3, 5*pi/6])
f = choice([sin, cos]) 
sol = f(x)
==

text ==
Quelle est la valeur de la fonction $! {{ f|latex }} !$ en $!\displaystyle {{ x|latex }} !$ ?
==

unauthorized_func = ['sin', 'cos']
```

#### Calculer la dérivée d'une fonction


#### Déterminer l'équation d'une droite

```
extends = /model/math/expr.pl

title = Déterminer l'équation d'une droite

before ==
from mplsympy import plotsvg
var('x')
a = choice([-1, 1]) * sympify(choice(['1/2', 1, '3/2', 2]))
b = randint(-3, 3)
sol = a*x + b
image = plotsvg(sol)
==

text ==
Déterminer l'équation de la droite tracée ci-dessous (en notant $! x !$ la variable d'abscisse et $! y !$ la variable d'ordonnée).

<div class="img-container">
{{ image }}
</div>
==

input_prefix = $! y = !$

solution ==
L'équation de la droite est :
$$ y = {{ sol|latex }}. $$
==
```
