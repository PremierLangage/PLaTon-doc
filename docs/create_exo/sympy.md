# Bibliothèque SymPy

La [bibliothèque SymPy](https://www.sympy.org) est une bibliothèque Python de calcul symbolique. Elle permet de représenter et de manipuler :

  * des fractions
  * des nombres complexes
  * des expressions algébriques
  * des expressions analytiques
  * des ensembles
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
>>> x+y
8/3
```


## Nombres complexes

```python
>>> from sympy import I
>>> x = 3 + I
>>> y = 1 - 2*I
>>> x*y
(1 - 2*I)*(3 + I)
>>> (x*y).expand()
5 - 5*I
```

```python
>>> from sympy import re, im, conjugate
>>> re(x)
3
>>> im(x)
1
>>> conjugate(x)
3 - I
```

## Polynômes

## Matrices
