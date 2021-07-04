# Réponse numérique

Le modèle `basic/numeric` permet de fabriquer des exercices avec un champ de réponse numérique.

Les clés de base de ce modèle sont :

  * `question` : l'énoncé de l'exercice ;
  * `sol` : la valeur de la solution.

```
extends = /model/basic/numeric.pl

question ==
Calculer 15 + 7.
==

sol = 22
```
