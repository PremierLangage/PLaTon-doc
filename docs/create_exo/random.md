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



## Autres exemples

Prenons l'exemple d'un exercice où il faut trouver le plus petit nombre parmi une liste de nombres. Pour ce type d'exercice, le modèle approprié est le modèle `basic\radio`.

On rappelle que dans ce modèle la liste des propositions est à entrer dans la clé `items` sous forme d'une chaîne multilignes ou d'une liste de chaînes. Avec une génération par un script Python, il est plus naturel d'utiliser le second format.

```
extends = /model/basic/radio.pl

question ==
Sélectionner le plus petit nombre de la liste suivante.
==

before ==
items = sorted(sampleint(4, 1, 50))
==
```
