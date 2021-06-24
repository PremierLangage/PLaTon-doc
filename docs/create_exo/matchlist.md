# Correspondances

Le modèle `basic/matchlist` permet de fabriquer des exercices de correspondances. 

![](matchlist.png)

Les clés de base de ce modèle sont :

  * `question` : l'énoncé de l'exercice ;
  * `matches` : la liste des correspondances.

**Exemple**

```
extends = /model/basic/matchlist.pl

question ==
Relier chaque pays à sa capitale.
==

matches ==
France,Paris
Italie,Rome
Allemagne,Berlin
Espagne,Madrid
==
```
