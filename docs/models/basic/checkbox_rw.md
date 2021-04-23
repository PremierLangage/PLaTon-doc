# Modèle `basic/checkbox_rw`

Le modèle `basic/checkbox_rw` permet de fabriquer des exercices à choix multiples (avec plusieurs réponses possibles).

Dans ce modèle, une liste de bonnes réponses et une liste de mauvaises réponses doivent être fournies. Ces listes peuvent être déclarées explicitement ou générées par un script Python.

## Clés du modèle

* `title` (chaîne). Titre de l'exercice.
    * Le titre doit décrire la tâche à effectuer dans l'exercice. Il est destiné au référencement de l'exercice.
* `text` (chaîne). Enoncé de l'exercice. 
    * La mise en forme avancée du texte s'effectue avec des balises Markdown ou HTML.
* `right` (chaîne multilignes). 
    * Cette clé contient une liste de bonnes réponses (chaque ligne correspondant à une réponse).
* `wrong` (chaîne multilignes). 
    * Cette clé contient une liste de mauvaises réponses (chaque ligne correspondant à une réponse).
* `before` (script Python). Script de génération des données et de la solution.
    * Ce script est facultatif. Il sert à générer les listes `right` et `wrong` si celles-ci ne sont pas déclarées explicitement.
* `nbitems` (entier). Nombre de choix.
* `maxright` (entier). Nombre maximum de bonnes réponses.
* `maxright` (entier). Nombre minimum de bonnes réponses.
* `scoring` (chaîne). Barème.

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
