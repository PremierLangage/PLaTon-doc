# LaTeX

Le langage [LaTeX](https://fr.wikipedia.org/wiki/LaTeX) est le langage de référence pour produire des expressions mathématiques dans un texte.

## Insérer des expressions LaTeX dans l'énoncé

```
question ==
Soit la fonction $! f : \mathbb{R} \rightarrow \mathbb{R} !$ telle que
$$ f(x) = \frac{1}{1+x^2}. $$
==
```


## Convertir des objets SymPy en LaTeX

```
before ==
x = Symbol('x')
expr = 1/(1 + x**2)
expr_latex = latex(expr)
==

question ==
Soit la fonction $! f : \mathbb{R} \rightarrow \mathbb{R} !$ telle que
$$ f(x) = {{ expr_latex }} . $$
==
```

```
before ==
x = Symbol('x')
expr = 1/(1 + x**2)
==

question ==
Soit la fonction $! f : \mathbb{R} \rightarrow \mathbb{R} !$ telle que
$$ f(x) = {{ expr|latex }} . $$
==
```
