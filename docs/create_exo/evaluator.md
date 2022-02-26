# Evaluer la réponse

Jusqu'ici, dans les exemples d'exercices, l'évaluation de la réponse a été complètement prise en charge par les modèles. Il est en fait possible de programmer soi-même l'évaluation de la réponse grâce à un script Python.

Ce script, à placer dans la clé `evaluator`, est exécuté après chaque validation de l'exercice par l'élève. Le script a accès à la réponse de l'élève dans la variable `input.value` et, comme le script `before`, il a accès à toutes les clés de l'exercice. Il doit produire une clé `score` (un score pour la tentative) et éventuellement une clé `feedback` (un message d'erreur).

**Exemple**

```
extends = /model/basic/numinput.pl

before ==
k = randint(3, 6)
a = randint(25, 75)
b = a + randint(6, 10)
==

question ==
Donner un entier multiple de {{ k }}, compris entre {{ a }} et {{ b }}.
==

evaluator ==
if input.value % k != 0:
    score = 0
    feedback = f"Ce nombre n'est pas un multiple de {k}."
elif input.value < a or ans > b:
    score = 0
    feedback = f"Ce nombre n'est pas compris entre {a} et {b}."
else:
    score = 100
==
```
