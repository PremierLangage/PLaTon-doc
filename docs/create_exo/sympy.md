# Bibliothèque SymPy

La [bibliothèque SymPy](https://www.sympy.org) est une bibliothèque Python de calcul symbolique. Elle permet de représenter et de manipuler :

  * des fractions
  * des expressions algébriques/analytiques
  * des nombres complexes
  * des ensembles finis
  * des intervalles
  * des polynômes
  * des matrices
  * etc.

Les modèles d'exercices mathématiques s'appuient sur la bibliothèque SymPy. En particulier, les données mathématiques et les solutions doivent être fournies sous forme d'objets SymPy.

## Fractions

```python
>>> from sympy import Rational
>>> x = Rational(2, 3)
>>> y = Rational(2)
>>> x + y
8/3
```

## Expressions

```python
>>> from sympy import sqrt, simplify
>>> x = sqrt(2) + sqrt(3)
>>> x**2
(sqrt(2) + sqrt(3))**2
>>> simplify(x**2)
2*sqrt(6) + 5
```

```python
>>> from sympy import Symbol
>>> a = Symbol('a')
>>> expr = (1 + a)**2
>>> expr
(a + 1)**2
>>> expr.expand()
a**2 + 2*a + 1
```

```python
>>> from sympy import Symbol, ln, diff
>>> x = Symbol('x')
>>> f = ln(x + 1)
>>> diff(f, x)
1/(x + 1)
```

## Nombres complexes

```python
>>> from sympy import I
>>> x = 3 + I
>>> y = 1 - 2*I
>>> z = x*y
>>> z
(1 - 2*I)*(3 + I)
>>> z.expand()
5 - 5*I
```

## Polynômes

## Ensembles finis

## Matrices
