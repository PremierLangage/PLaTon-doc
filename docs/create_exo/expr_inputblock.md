# Modifier l'interface de réponse

Il est possible de modifier le texte placé avant le champ de réponse grâce à la clé `prefix`.

```
extends = /model/math/expr.pl

before ==
x, y = symbols('x y')
a = randint(-5, 5, [0])
b = randint(-5, 5, [0])
expr = a*y + b
sol = (x - b)/a
==

question ==
Soit deux nombres $! x !$ et $! y !$ tels que $! x = {{ expr|latex }}. !$ 
Exprimer $! y !$ en fonction $! x !$.
==

prefix ==
$! y = !$
==
```

Quand la réponse nécessite des caractères spéciaux, il est conseillé d'adjoindre au champ de réponse un mini-clavier contenant ces caractères. On définit ce mini-clavier dans la clé `keypad` en fournissant une liste de mots-clés.

```
extends = /model/math/expr.pl

before ==
from sympy import Limit
x = Symbol('x')
f, g = sample([2*x+1, x+2, 2*x**2+1, x**2+1], 2)
lim = Limit(f/g, x, oo)
sol = lim.doit()
==

question ==
Déterminer la limite suivante.
==

prefix ==
$! \displaystyle {{ lim|latex }} = !$
==

keypad = ["+infty", "-infty"]
```

Enfin, il est possible d'incorporer le champ de réponse mathématique dans une expression LaTeX grâce à la clé `embed`.

```
extends = /model/math/expr.pl

before ==
p = randint(2, 5)
q = randint(2, 7, [4])
sol = p**2*q
==

question ==
Ecrire l'expression suivante sous la forme  $% \sqrt{a} %$, où $% a %$ est un entier.
==

prefix ==
$! {{ p }} \sqrt{ {{ q }} } = !$
==

embed ==
\sqrt{#}
==
```
