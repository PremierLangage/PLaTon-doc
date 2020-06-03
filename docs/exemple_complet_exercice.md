# Un exemple complet d'exercice

L'exemple que nous allons considérer est un exercice très simple d'addition. On demande de calculer la somme de deux entiers tirés aléatoirement (entre 10 et 20). La réponse doit être rentrée dans un champ de réponse numérique libre.

[Tester l'exercice](https://pl.u-pem.fr/filebrowser/demo/10859/)

```
@ /builder/before.py [builder.py]
@ /grader/evaluator.py [grader.py]

before ==
import random as rd
a = rd.randint(10, 20)
b = rd.randint(10, 20)
==

title = "Addition"

text ==
Calculer {{ a }} + {{ b }}.
==

input =: Input
input.type = number

form ==
{{ input|component }}
==

evaluator ==
if input.value == a + b:
    score = 100
else:
    score = 0
==
```
