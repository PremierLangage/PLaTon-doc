# LaTeX

Le langage [LaTeX](https://fr.wikipedia.org/wiki/LaTeX) est le langage de référence pour produire des expressions mathématiques dans un texte.

## Insérer des expressions LaTeX dans l'énoncé

Les balises pour intégrer du code LaTeX dans l'énoncé sont `$!...!$` (mode en ligne) et `$$...$$` (mode équation).

```
question ==
Soit la fonction $! f : \mathbb{R} \rightarrow \mathbb{R} !$ telle que
$$ f(x) = \frac{1}{1+x^2}. $$
==
```

## Convertir des objets SymPy en LaTeX

Dans les exercices, les données mathématiques sont généralement produites sous forme d'objets SymPy. Il est alors nécessaire de convertir ces objets SymPy en chaîne LaTeX pour les insérer dans l'énoncé. La commande `latex` permet cette conversion.

```
before ==
from sympy import Symbol
from sympy2latex import latex
x = Symbol('x')
expr = 1/(1 + x**2)
expr_latex = latex(expr)
==

question ==
Soit la fonction $! f : \mathbb{R} \rightarrow \mathbb{R} !$ telle que
$$ f(x) = {{ expr_latex }} . $$
==
```

Un système de **filtre** permet de simplifier encore cette conversion.

```
before ==
from sympy import Symbol
x = Symbol('x')
expr = 1/(1 + x**2)
==

question ==
Soit la fonction $! f : \mathbb{R} \rightarrow \mathbb{R} !$ telle que
$$ f(x) = {{ expr|latex }} . $$
==
```

## Paramètres du convertisseur LaTeX

TODO
