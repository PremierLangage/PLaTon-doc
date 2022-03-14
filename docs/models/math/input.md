# Modèle `math/input`

## Détails

### `evaluator`

Ce script est exécuté après la validation de l'exercice et permet d'évaluer la réponse saisie. Le script doit définir un score dans une variable `score`. Le score est une valeur entière comprise entre -1 et 100. La valeur -1 indique une erreur de syntaxe dans la saisie. Le script peut également définir un message d'avertissement ou d'erreur dans une variable `feedback`. 


## Exemples

### Exemple 1

```
extends = /model/math/input.pl

before ==
a = randint(1, 30)
b = a + 10
==

question ==
Trouver un nombe premier compris entre {{ a }} et {{ b }} (au sens large).
==

evaluator ==
from latex2sympy import latex2sympy
from sympy import isprime

try:
    ans = latex2sympy(input.value)
except:
    score = -1
    feedback = "La réponse doit être un entier."
else:
    if not ans.is_Integer:
        score = -1
        feedback = "La réponse doit être un entier."
    elif not (a <= ans <= b):
        score = 0
        feedback = f"La réponse doit être comprise entre {a} et {b}."
    elif not isprime(ans):
        score = 0
        feedback = "La réponse doit être un nombre premier."
    else:
        score = 100
==
```
