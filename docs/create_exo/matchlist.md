# Correspondances

Le modèle `basic/matchlist` permet de fabriquer des exercices de correspondances. 

![](matchlist.png)

Les clés de base de ce modèle sont :

  * `question` : l'énoncé de l'exercice ;
  * `matches` : la liste des correspondances.

La liste des correspondances `matches` peut être saisie comme une liste de couples source-cible ou, ce qui est plus pratique, comme une chaîne multilignes (chaque ligne correspondant à un couple, les éléments du couple étant séparés par une virgule).

**Exemple 1**

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

Pour introduire de l'aléa dans l'exercice, on peut entrer une liste longue dans `matches` et fixer un nombre de couples à tirer dans cette liste grâce à la clé `nbmatches`.

**Exemple 2**

```
extends = /model/basic/matchlist.pl

question ==
Relier chaque pays à sa capitale.
==

nbmatches = 4

matches ==
France,Paris
Italie,Rome
Allemagne,Berlin
Espagne,Madrid
==
```

Par défaut, il n'est pas possible d'attacher deux items sources à la même cible. Pour rendre cela possible, il faut mettre la clé `multiple` à `True`.

Par ailleurs, la clé `targets` permet d'introduire des items cibles distracteurs, en plus des items cibles des correspondances.

**Exemple 3**

```
extends = /model/basic/matchlist.pl

question ==
Relier chaque ville à son pays.
==

multiple = True

matches ==
Paris,France
Marseille,France
Milan,Italie
Barcelone,Espagne
==

targets ==
Allemagne
Portugal
==
```

Par défaut, le barème est `RightMinusWrong` : l'exercice renvoie le nombre d'items sources bien attribués moins le nombre d'items sources mal attribués, le tout divisé par le nombre total d'items sources et ramené entre 0 et 100.

L'autre barème est `AllOrNothing` : l'exercice renvoie un score de 100 si tous les items sources sont bien attribués; il renvoie un score de 0 sinon.

Le barème est modifiable grâce à la clé `scoring`.
