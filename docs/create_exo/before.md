# Génération des données

Dans les exemples précédents, les clés des modèles ont toujours été définies de façon explicite. Mais il est également possible de générer dynamiquement ces clés à l'aide d'un script Python. Cela permet en particulier de générer des données aléatoires pour l'exercice.

Ce script Python doit être écrit dans la clé `before`. Pour définir une clé dans ce script, il suffit de créer une variable du nom de cette clé.

Par exemple, dans un fichier PL, il est équivalent d'écrire :

```
key1 = 3

key2 = [0, 1, 2]
```

ou

```
before ==
key1 = 3
key2 = [0, 1, 2]
==
```

Voyons maintenant comment écrire un exercice aléatoire en utilisant ce script `before`. Prenons l'exemple d'un exercice où il faut trouver le plus petit nombre parmi une liste de nombres. Pour ce type d'exercice, le modèle approprié est le modèle `basic\radio`.

On rappelle que dans ce modèle la liste des propositions est à entrer dans la clé `items` sous forme d'une chaîne multilignes ou d'une liste de chaînes. Avec une génération par un script Python, il est plus naturel d'utiliser le second format.

```
extends = /model/basic/radio.pl

question ==
Sélectionner le plus petit nombre de la liste suivante.
==

before ==
items = [str(x) for x in sorted(sample(range(50), 4))]
==
```
