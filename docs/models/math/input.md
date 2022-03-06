## Détails

### `evaluator`

Ce script est exécuté après la validation de l'exercice et permet d'évaluer la réponse saisie. Le script doit définir un score dans une variable `score`. Le score est une valeur entière comprise entre -1 et 100. La valeur -1 indique une erreur de syntaxe dans la saisie. Le script peut également définir un message d'avertissement ou d'erreur dans une variable `feedback`. 


## Exemples

```
extends = /model/math/input.pl

title = Transformer une somme de logarithmes en un logarithme

before ==
p = randint(2, 5)
q = randint(2, 5)
expr = f"\ln({p}) + \ln({q})"
sol = ln(p*q)
==

text ==
Ecrire $! {{ expr }} !$ sous la forme  $! \ln(a) !$, où $! a !$ est un nombre.
==

evaluator ==
from latex2sympy import latex2sympy
from evalsympy import equal
from sympy import log

def eval_ans(strans, sol):
    try:
        ans = latex2sympy(strans)
    except:
        return (-1, "NotExpr")
    if ans.func != log:
        return (-1, "WrongForm")
    if not equal(ans, sol):
        return (0, "NotEqual")
    return (100, "Success")

score, error = eval_ans(answers['math'], sol)
feedback = message[error]
==

solution ==
La solution est $! {{ sol|latex}} !$.
==
```
