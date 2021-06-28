# Fonction aléatoires

Cette page résume les commandes aléatoires les plus utiles. Elles sont issues du module standard `random` ou du module propre à la plateforme `plrandom`. Pour alléger l'écriture du script `before`, elles sont toutes importées par défaut.

## Tirer aléatoirement des entiers

La fonction `randint` du module `random` permet de tirer un entier aléatoire. Plus précisément, la commande `randint(a, b)` renvoie un entier aléatoire compris entre `a` et `b` inclus.

```python
>>> from random import randint
>>> randint(1, 9)
8
>>> randint(1, 9)
3
```

Il est souvent utile d'exclure certaines valeurs dans la plage de valeurs où l'on tire. C'est pour cela que le module `plrandom` propose une version modifiée de la fonction `randint`. Avec cette version, la commande `randint(a, b, xval)` renvoie un entier aléatoire compris entre `a` et `b` inclus, en excluant les valeurs de la liste `xval`.

```python
>>> from plrandom import randint
>>> randint(-3, 3, [0, 1])
-1
>>> randint(-3, 3, [0, 1])
3
```

C'est cette version qui est importée par défaut dans le script `before`.

Pour tirer plusieurs entiers avec remise, il suffit de créer une liste en compréhension avec la fonction `randint`.

```python
>>> [randint(1, 5) for x in range(3)]
[2, 4, 1]
>>> [randint(1, 5) for x in range(3)]
[2, 2, 5]
```

La fonction `sampleint` du module `plrandom` permet de tirer aléatoirement plusieurs entiers sans remise. Plus précisément, la commande `sampleint(a, b, k)` renvoie une liste de `k` entiers tirés aléatoirement (sans remise) entre `a` et `b` inclus.

```python
>>> from plrandom import sampleint
>>> sampleint(1, 5, 3)
[4, 5, 1]
>>> sampleint(1, 5, 3)
[1, 3, 5]
```

Pour tirer plusieurs éléments avec remise, il suffit de créer une liste en compréhension avec la fonction `randint`.

```python
>>> from random import choice
>>> choice(["AA", "AB", "AC", "AD"])
'AD'
>>> choice(["AA", "AB", "AC", "AD"])
'AC'
```

La fonction `sample` du module `random` permet de tirer aléatoirement plusieurs éléments sans remise. Plus précisément, la commande `sample(lst, k)` renvoie une liste de `k` entiers tirés aléatoirement (sans remise) dans la liste `lst`.

```python
>>> from random import sample
>>> sample(["AA", "AB", "AC", "AD"], 3)
['AC', 'AB', 'AA']
>>> sample(["AA", "AB", "AC", "AD"], 3)
['AB', 'AA', 'AD']
```

## Mélanger une liste

La fonction `shuffle` du module `random` permet de mélanger une liste. Attention : La commande `suffle(lst)` ne renvoie pas une nouvelle liste, elle modifie *sur place* la liste `lst`.

```python
>>> from random import shuffle
>>> lst = ["AA", "AB", "AC", "AD"]
>>> shuffle(lst)
>>> lst
['AD', 'AA', 'AC', 'AB']
```
