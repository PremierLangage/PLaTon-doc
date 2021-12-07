# Générer des graphiques avec `matplotlib`

Dans le script `before`, il est possible de générer des graphiques avec `matplotlib` puis de les convertir en code source SVG, qui peut-être inséré directement dans la page de l'exercice.

## Premier exemple

```
extends = /model/basic/basic.pl
@ /utils/graphics/plmpl.py

before ==
import matplotlib.pyplot as plt
from plmpl import fig2svg
from numpy import linspace, cos, pi

t = linspace(0, 4, 100)
s = 1 + cos(pi*t)
plt.plot(t, s)

image = fig2svg(plt.gcf())
==

question ==
<div class="img w50">
{{ image }}
</div>
==
```

## Fonction `easyplot`

La fonction `easyplot` facilite le tracé d'une fonction mathématique dans une figure `matplotlib`. La fonction mathématique peut être fournie à `easyplot` comme une fonction Python ou une expression SymPy.

```
before ==
import matplotlib.pyplot as plt
from plmpl import fig2svg, easyplot
from numpy import cos, pi

f = lambda x : 1 + cos(pi*x)
easyplot(plt.gcf(), f, 0, 4)

image = fig2svg(plt.gcf())
==
```

```
before ==
import matplotlib.pyplot as plt
from plmpl import fig2svg, easyplot
from sympy import cos, pi, Symbol

x = Symbol('x')
expr = 1 + cos(pi*x)
easyplot(plt.gcf(), expr, 0, 4)

image = fig2svg(plt.gcf())
==
```

## Paramètres

De nombreux paramètres permettent de configurer l'aspect de la figure.

```
before ==
import matplotlib.pyplot as plt
from plmpl import fig2svg, easyplot

f = lambda x : x**2
easyplot(plt.gcf(), f, -2.5, 2.5, color='red')

plt.title('Parabole')
plt.xlim(-3, 3)
plt.ylim(0, 6)
plt.xticks(range(-3, 4))
plt.yticks(range(0, 7))
plt.grid(True)

image = fig2svg(plt.gcf())
==
```

## Multiples tracés

## Multiples figures
