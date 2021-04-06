# Modèle `math/input`

Le modèle `math/input` permet de créer des exercices dont la réponse est une expression mathématique.


## Clés du modèle

#### Clés de base
* `title` (chaîne). Titre de l'exercice.
    Le titre doit décrire la tâche à effectuer dans l'exercice. Il est destiné au référencement de l'exercice.
* `before` (script Python). Script de génération des données et de la solution.
   Ce script est exécuté au lancement de l'exercice et permet de générer les données de l'exercice.  
   Pour alléger l'écriture de ce script, un certain nombre de fonctions sont importées automatiquement :
   * les principales classes et fonctions du module de calcul symbolique SymPy (https://docs.sympy.org) ;
   * des fonctions de génération aléatoire ;
   * des fonctions de génération aléatoire d'objets SymPy ;
   * des fonctions de conversion des objets SymPy en LateX.
* `text` (chaîne). Enoncé de l'exercice. 
    * L'insertion de formules mathématiques s'effectue avec du code LaTeX dans les balises `$!...!$` (mode en ligne) ou `$$...$$` (mode équation).
    * L'insertion dynamique de données produites par le script `before` s'effectue à l'aide des balises `{{...}}`. Par exemple, si la variable `var` a été définie dans le script `before`, la commande `{{ var }}` permet d'insérer sa représentation textuelle dans l'énoncé.
    * Par ailleurs, un filtre `latex` permet d'insérer la représentation LaTeX d'un objet SymPy. Par exemple, si l'objet SymPy `obj` a été défini dans le script `before`, la commande `{{ obj|latex }}` permet d'insérer sa représentation LaTeX dans l'énoncé.
    * La mise en forme avancée du texte s'effectue avec des balises Markdown ou HTML.


* `evaluator` (script Python). Script d'évaluation de la réponse.

    Ce script est exécuté après la validation de l'exercice et permet d'évaluer la réponse de l'élève.
        * La réponse de l'élève est contenue dans la variable `answers['math']` sous forme d'une chaîne LaTeX.
        * Le script doit définir un score dans une variable `score`.
        * Le script peut également définir un message d'avertissement ou d'erreur dans une variable `feedback`.

    Pour faciliter l'analyse de la réponse :
        * Fonctions de conversion LaTeX vers SymPy
        * Fonctions avancées de manipulation des objets SymPy : https://docs.sympy.org/latest/tutorial/manipulation.html

    


#### Interface de réponse
* `input_prefix` (chaîne). Chaîne placée avant le champ de réponse. 

    Par défaut, cette clé contient la chaîne `Réponse :`. Elle offre les mêmes possibilités de mise en forme que la clé `text`.

#### Messages
* `solution` (chaîne). Message de correction de l'exercice.

    Cette clé offre les mêmes possibilités de mise en forme que la clé `text`.

* `hint` (chaîne). Message(s) d'indication.

    Cette clé offre les mêmes possibilités de mise en forme que la clé `text`.

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
