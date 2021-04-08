# Modèle `math/expr`

Le modèle `math/expr` est un modèle dérivé du modèle `math/input` pour des exercices où la réponse est unique et de type expression algébrique ou analytique (expression impliquant des nombres, des variables, des opérations algébriques et des fonctions). Le script d'évaluation y est prédéfini.

## Clés du modèle

#### Clés de base
* `title` (chaîne). Titre de l'exercice.
* `before` (script Python). Script de génération des données et de la solution. 
    * La solution doit être une [expression SymPy](https://docs.sympy.org/latest/modules/core.html?#module-sympy.core.expr). et doit être stockée dans la variable `sol`.
* `text` (chaîne). Enoncé de l'exercice. 

#### Interface de réponse
* `input_prefix` (chaîne). Chaîne placée avant le champ de réponse. Par défaut, cette chaîne est `Réponse :`.

#### Evaluation de la réponse
* `checkratsimp` (booléen Python, ). 
    * Si cette clé vaut `True`, l'exercice vérifie que les valeurs rationnelles sont simplifiées dans la réponse de l'élève. Des réponses du type $4+3$, $1+\fra{1}{2}$, $\sqrt{4+3}$, $\sqrt{4}$, etc. déclencheront un message d'avertissement.
    * Valeur par défaut : `True`.
* `unauthorized_func` (liste de chaînes Python). 
    * Cette clé contient les noms des fonctions non autorisées.
    * Valeur par défaut : `[]`.
* `symbol_dict` (dictionnaire Sympy). 
    * Cette clé contient le dictionnaire des symboles utilisé pour convertir la réponse de l'élève en expression SymPy.
    * Valeur par défaut : `{'e': E}`. Le symbole `e` est alors interprété comme le nombre d'Euler (objet SymPy `E`).

#### Messages
* `solution` (chaîne). Solution de l'exercice.
* `hint` (chaîne). Indication.
* `message` (dictionnaire de chaînes). Messages d'erreur.
    * Par défaut, les messages d'erreur sont :
         message.Success = 
         message.NotEqual = 
         message.NotExpr = La réponse doit être une expression mathématique.
         message.NotRatSimp = L'expression peut encore être simplifiée.  

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
