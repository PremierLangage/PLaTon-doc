# Modèle `math/input`

Le modèle `math/input` permet de créer des exercices dont la réponse est une expression mathématique.

* Le champ de réponse permet de saisir facilement une expression mathématique avec un rendu de type TeX. 
* La génération des données de l'exercice et l'évaluation de la réponse de l'élève est effectuée par des scripts Python.

## Clés du modèle

#### Clés de base
* `title` (chaîne). Titre de l'exercice.
    * Le titre doit décrire la tâche à effectuer dans l'exercice. Il est destiné au référencement de l'exercice.
* `before` (script Python). Script de génération des données et de la solution.
    * Ce script est exécuté au lancement de l'exercice et permet de générer les données de l'exercice.
    * Pour faciliter cette tâche, en plus de la [bibliothèque Python standard](https://docs.python.org/fr/3/library/index.html), un certain nombre de paquets et de modules sont disponibles. En particulier :
        * `sympy` : calcul symbolique (https://docs.sympy.org)
        * `plrandom` : fonctions aléatoires (bibliothèque locale)
        * `randsympy` : génération aléatoire d'objets SymPy (bibliothèque locale)
        * `sympy2latex` : conversion d'objets SymPy en LateX (bibliothèque locale)
        * `latex2sympy` : conversion d'expressions LateX en objets SymPy (bibliothèque locale)
        * `mplsympy` : génération d'objets graphiques à partir d'objets SymPy (bibliothèque locale)
    * Pour alléger l'écriture du script, les fonctions les plus courantes de ces bibliothèques sont automatiquement importées (voir annexe ci-après).
* `text` (chaîne). Enoncé de l'exercice. 
    * L'insertion de formules mathématiques s'effectue avec du code LaTeX dans les balises `$!...!$` (mode en ligne) ou `$$...$$` (mode équation).
    * L'insertion dynamique de données produites par le script `before` s'effectue à l'aide des balises `{{...}}`. Par exemple, si la variable `var` a été définie dans le script `before`, la commande `{{ var }}` permet d'insérer sa représentation textuelle dans l'énoncé.
    * Par ailleurs, un filtre `latex` permet d'insérer la représentation LaTeX d'un objet SymPy. Par exemple, si l'objet SymPy `obj` a été défini dans le script `before`, la commande `{{ obj|latex }}` permet d'insérer sa représentation LaTeX dans l'énoncé.
    * La mise en forme avancée du texte s'effectue avec des balises Markdown ou HTML.
* `evaluator` (script Python). Script d'évaluation de la réponse.
    * Ce script est exécuté après la validation de l'exercice et permet d'évaluer la réponse de l'élève.
    * La réponse de l'élève est contenue dans la variable `answers['math']` sous forme d'une chaîne LaTeX.
    * Le script doit définir un score dans une variable `score`. Le score est une valeur entière comprise entre -1 et 100. La valeur -1 indique à l'activité qui exécute l'exercice que cette tentative ne doit pas être prise en compte (dans le cas, par exemple, d'une erreur de syntaxe dans la saisie).
    * Le script peut également définir un message d'avertissement ou d'erreur dans une variable `feedback`. 

#### Interface de réponse
* `input_prefix` (chaîne). Chaîne placée avant le champ de réponse. 
    * Par défaut, cette clé contient la chaîne `Réponse :`. 
    * Elle offre les mêmes possibilités de mise en forme que la clé `text`.
* `keypad` (liste de dictionnaires). Clavier virtuel. 
    * Par défaut, cette clé contient une lsite vide. 
    * Les éléments de la liste sont des dictionnaires représentant les boutons du clavier. Les clés de ces dictionnaires sont `label`, `action` et `value`. 

#### Messages
* `solution` (chaîne). Message de correction de l'exercice.
    * Cette clé offre les mêmes possibilités de mise en forme que la clé `text`.
* `hint` (chaîne). Message(s) d'indication.
    * Cette clé offre les mêmes possibilités de mise en forme que la clé `text`.

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

## Annexes

### Importations automatiques du `before`

```
from sympy import E, I, pi, oo
from sympy import sqrt, Abs, sin, cos, tan, exp, ln
from sympy import var, symbols, Symbol
from sympy import sympify, simplify
from sympy import Integer, Rational, Poly, FiniteSet, Tuple
from random import choice, choices, sample, shuffle
from plrandom import randint
from sympy2latex import latex
from latex2sympy import latex2sympy
```
