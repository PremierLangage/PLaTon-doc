# Modèle `math/input_eval`

Le modèle `math/input_eval` permet de fabriquer un exercice avec un champ de réponse mathématique et une évaluation personnalisée de la réponse. Cette évaluation personnalisée doit être définie par un script Python.

## Clés spécifiques

<table class="table">
<thead>
<tr>
<th scope="col">Clé</th>
<th scope="col">Description</th>
<th scope="col">Type</th>
<th scope="col">Défaut</th>
</tr>
</thead>
<tbody>

<tr>
<th scope="row"> evaluator </th>
<td> Script Python permettant d'évaluer la réponse de l'exercice. </td>
<td> str </td>
<td>  </td>
</tr>

<tr>
<th scope="row"> score </th>
<td> Score de l'exercice. Il doit être produit par le script evaluator. </td>
<td> int </td>
<td>  </td>
</tr>

<tr>
<th scope="row"> feedback </th>
<td> Message d'avertissement ou d'erreur. Il doit être produit par le script evaluator. </td>
<td> str </td>
<td>  </td>
</tr>

</tbody>
</table>

## Détails

### `evaluator`

Ce script est exécuté après la validation de l'exercice et permet d'évaluer la réponse saisie. Le script doit définir un score dans une variable `score`. Le score est une valeur entière comprise entre -1 et 100. La valeur -1 indique une erreur de syntaxe dans la saisie. Le script doit également définir un message d'avertissement ou d'erreur dans une variable `feedback`.

Toutes les clés définies dans le fichier `pl` et toutes les variables sérialisables créées dans le script `before` sont accessibles dans le script `evaluator`. Les variables sérialisables sont les variables de type `int`, `float`, `bool`, `str`, `list`, `dict` et les variables de type SymPy `Basic` ou `Matrix`.

Un certain nombre de fonctions utiles sont importées automatiquement.

La réponse saisie est récupérable par la méthode `get_value` du champ de réponse (nommé `input` dans le modèle).

```
ans = input.get_value()
```

Cette réponse est une chaîne LaTeX. Il est donc en général nécessaire de la convertir en objet SymPy pour l'analyser. La fonction `latex2sympy` du module `latex2sympy` permet d'effectuer cette conversion. Pour prendre en compte les échecs de conversion (syntaxe incorrecte de la réponse), il est nécessaire d'utiliser une structure du type `try...except...else`. Le plus souvent, le script d'évaluation prend donc la forme suivante.

```
evaluator ==
try:
    ans = latex2sympy(input.get_value())
except:
    score = -1
    feedback = "La réponse n'est pas syntaxiquement correcte."
else:
    # analyse de la variable ans
==
```

## Exemples

### Exemple 1

```
extends = /model/math/input_eval.pl

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
    ans = latex2sympy(input.get_value())
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
        feedback = ""
==
```
