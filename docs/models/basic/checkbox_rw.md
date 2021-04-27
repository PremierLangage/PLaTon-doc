# Modèle `basic/checkbox_rw`

Le modèle `basic/checkbox_rw` permet de fabriquer des exercices à choix multiples (avec plusieurs réponses possibles). Les données de l'exercices sont fournies sous la forme d'une liste de bonnes réponses et d'une liste de mauvaises réponses.

## Clés du modèle

Les clés `title`, `text` et `before` ont leur signification et leur syntaxe usuelles.

* `right` (chaîne ou liste). Liste de bonnes réponses.
    * Cette clé contient une liste de bonnes réponses sous la forme d'une chaîne multilignes (chaque ligne correspondant à une réponse) ou d'une liste de chaînes.
* `wrong` (chaîne ou liste). Liste de mauvaises réponses.
    * Cette clé contient une liste de mauvaises réponses sous la forme d'une chaîne multilignes (chaque ligne correspondant à une réponse) ou d'une liste de chaînes.
* `nbitems` (entier). Nombre de choix proposés.
* `maxright` (entier). Nombre maximum de bonnes réponses parmi les choix.
* `minright` (entier). Nombre minimum de bonnes réponses parmi les choix.
* `scoring` (chaîne). Barème de l'exercice.
    * `AllOrNothing` : renvoie un score de 100 si toutes les bonnes réponses sont sélectionnées et aucune mauvaise réponse n'est sélectionnée ; renvoie un score de 0 sinon.
    * `RightMinusWrong` : renvoie le nombre de bonnes réponses sélectionnés moins le nombre de mauvaises réponses sélectionnées, le tout divisé par le nombre total de bonnes réponses et ramené entre 0 et 100.
    * Par défaut, le barème est `RightMinusWrong`.

## Exemples (avec déclaration explicite des listes de réponses)

```
extends = /model/basic/checkbox_rw.pl

text ==
Indiquer parmi les noms suivants ceux qui sont des noms valides pour une variable en Python.
==

nbitems % 5
minright % 2
maxright % 3

right ==
bonjour
abc
oui
NON
Ciao
good_morning
byeBye7
\_UGE\_
==

wrong ==
Hi!
au revoir
6hello6
def
for
good-afternoon
f()
==
```

## Exemples (avec génération des listes de réponses)

```
extends = /model/basic/checkbox_rw.pl

title = Multiples de 3

nbitems % 5
minright % 1
maxright % 4

before ==
right = [str(n) for n in range(50, 100) if n % 3 == 0]
wrong = [str(n) for n in range(50, 100) if n % 3 != 0]
==

text ==
Parmi les nombres suivants, lesquels sont des multiples de 3 ?
==
```
