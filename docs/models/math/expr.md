# Modèle `math/expr`

Le modèle `math/expr` permet de créer des exercices dont la réponse est une expression faisant intervenir des nombres, des variables, des opérations algébriques et des fonctions.

## Clés du modèle

#### Clés de base
* `title` (chaîne). Titre de l'exercice.
* `before` (script Python). Script de génération des données et de la solution. 
    * La solution doit être une [expression SymPy](https://docs.sympy.org/latest/modules/core.html?#module-sympy.core.expr). et doit être stockée dans la variable `sol`.
* `text` (chaîne). Enoncé de l'exercice. 

#### Interface de réponse
* `input_prefix` (chaîne). Chaîne placée avant le champ de réponse. Par défaut, cette chaîne est `Réponse :`.

#### Evaluation de la réponse
* `checkratsimp` (booléen Python, valeur par défaut : `True`). 
    * Si cette clé vaut `True`, l'exercice vérifie que les valeurs rationnelles sont simplifiées dans la réponse de l'élève. Des réponses du type $4+3$, $1+\fra{1}{2}$, $\sqrt{4+3}$, $\sqrt{4}$, etc. déclencheront un message d'avertissement.
* `unauthorized_func` (liste de chaînes Python, valeur par défaut : `[]`). 
    Cette clé contient les noms des fonctions non autorisées.
* `symbol_dict` (dictionnaire Sympy). Dictionnaire des symboles utilisées pour interpréter la réponse de l'élève.

#### Messages
* `solution` (chaîne). Solution de l'exercice.
* `hint` (chaîne). Indication.

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

text ==
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
