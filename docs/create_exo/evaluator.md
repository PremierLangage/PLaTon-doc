# Evaluer la réponse

Jusqu'à maintent, dans les exemples d'exercices, l'évaluation de la réponse a été complètement prise en charge par les modèles. Il est possible de programmer l'évaluation de la réponse.

La réponse de l'élève est contenue dans la variable `ans`

**Exemple**

```
extends = /model/basic/numeric.pl

before ==
k = randint(3, 6)
a = randint(25, 75)
b = a + randint(6, 10)
==

question ==
Donner un entier multiple de {{k}}, compris entre {{ a }} et {{ b }} (inclus).
==

evaluator ==
if ans % k != 0:
    score = 0
    feedback = f"Ce nombre n'est pas un multiple de {k}."
elif ans < a or ans > b:
    score = 0
    feedback = f"Ce nombre n'est pas compris entre {a} et {b}."
else:
    score = 100
==
```
