# Réponse numinput

Le modèle `basic/numinput` permet de fabriquer des exercices avec un champ de réponse numérique.

Les clés de base de ce modèle sont :

  * `question` : l'énoncé de l'exercice ;
  * `sol` : la valeur de la solution.

Le champ de réponse accepte les nombres entiers ou décimaux. Attention : le séparateur décimal est le point.

**Exemple 1**

```
extends = /model/basic/numinput.pl

question ==
Calculer 15 + 7.
==

sol = 22
```

**Exemple 2**

```
extends = /model/basic/numinput.pl

question ==
Donner l'écriture décimale de la fraction 7/4.
==

sol = 1.75
```
