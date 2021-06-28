
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
