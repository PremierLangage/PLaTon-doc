# Fonction aléatoires

Cette page résume les commandes aléatoires les plus utiles sur la plateforme. La plupart sont issues du module standard `random`. Certaines sont propres à la plateforme. Pour alléger l'écriture du script `before`, elles sont toutes importées par défaut.

## Tirer aléatoirement des entiers

**Tirer aléatoirement un entier**

La commande `randint(a, b)` renvoie un entier aléatoire compris entre `æ` et `b` inclus.

```python
>>> from random import randint
>>> randint(1, 9)
8
>>> randint(1, 9)
3
```

La commande `randint(a, b, xval)` renvoie un entier aléatoire compris entre `æ` et `b` inclus, en excluant les valeurs de la liste `xval`.

```
before ==
n = randint(-5, 5, [0, 1])
==
```

**Tirer aléatoirement plusieurs entiers (avec remise)**

Pour tirer plusieurs entiers 

```
before ==
n1, n2, n3 = [randint(1, 99) for x in range(3)]
==
```

**Tirer aléatoirement plusieurs entiers (sans remise)**

Pour tirer plusieurs entiers 

```
before ==
n1, n2, n3 = sampleint(1, 99, 3)
==
```

## Tirer aléatoirement dans une liste

**Tirer un élément dans une liste**

```python
>>> from random import choice
>>> choice(["AA", "AB", "AC", "AD"])
'AD'
>>> choice(["AA", "AB", "AC", "AD"])
'AC'
```

**Tirer plusieurs éléments dans une liste (avec remise)**



**Tirer plusieurs éléments dans une liste (sans remise)**

```python
>>> from random import sample
>>> sample(["AA", "AB", "AC", "AD"], 3)
['AC', 'AB', 'AA']
>>> sample(["AA", "AB", "AC", "AD"], 3)
['AB', 'AA', 'AD']
```

## Mélanger une liste

```python
>>> from random import shuffle
>>> lst = ["AA", "AB", "AC", "AD"]
>>> shuffle(lst)
>>> lst
['AD', 'AA', 'AC', 'AB']
```
