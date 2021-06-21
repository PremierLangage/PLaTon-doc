# Fonction aléatoires

Cette page résume les commandes aléatoires les plus utiles sur la plateforme. La plupart sont issues du module standard `random`. Certaines sont propres à la plateforme. Pour alléger l'écriture du script `before`, elles sont toutes importées par défaut.

## Tirer aléatoirement des entiers

**Tirer aléatoirement un entier**

La commande `randint(a, b)` renvoie un entier aléatoire compris entre `æ` et `b` inclus.

```
before ==
n = randint(1, 9)
==
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

```
before ==
lst = ["AA", "AB", "AC", "AD"]
val = choice(lst)
==
```

**Tirer plusieurs éléments dans une liste (avec remise)**



**Tirer plusieurs éléments dans une liste (sans remise)**

## Mélanger une liste
