# Modèle `math/expr`

Le modèle `math/expr` permet de fabriquer des exercices (aléatoires) où la réponse est une expression algébrique ou analytique (expression impliquant des nombres, des variables, des opérations algébriques et des fonctions). Les données et la solution de l'exercice doivent être générées par un script Python. L'évaluation de la réponse de l'élève est automatique.

## Clés du modèle

#### Clés de base
* `title` (chaîne). Titre de l'exercice.
    * Le titre doit décrire la tâche à effectuer dans l'exercice. Il est destiné au référencement de l'exercice.
* `before` (script Python). Script de génération des données et de la solution.
    * Ce script est exécuté au lancement de l'exercice et permet de générer les données et la solution de l'exercice.
    * Le script doit définir une variable `sol` contenant la solution. Cette solution doit être un objet SymPy de type `Expr`.
    * En plus de la [bibliothèque Python standard](https://docs.python.org/fr/3/library/index.html), un certain nombre de paquets et de modules sont disponibles. En particulier :
        * `sympy` : calcul symbolique (https://docs.sympy.org)
        * `plrandom` : fonctions aléatoires (bibliothèque locale)
        * `randsympy` : génération aléatoire d'objets SymPy (bibliothèque locale)
        * `sympy2latex` : conversion d'objets SymPy en LateX (bibliothèque locale)
        * `latex2sympy` : conversion d'expressions LateX en objets SymPy (bibliothèque locale)
        * `mplsympy` : génération d'objets graphiques à partir d'objets SymPy (bibliothèque locale)
    * Les fonctions les plus courantes de ces bibliothèques sont automatiquement importées (voir annexe ci-après).
* `question` (chaîne). Enoncé de l'exercice. 
    * L'insertion de formules mathématiques s'effectue avec du code LaTeX dans les balises `$!...!$` (mode en ligne) ou `$$...$$` (mode équation).
    * L'insertion dynamique de données produites par le script `before` s'effectue à l'aide des balises `{{...}}`. Par exemple, si la variable `var` a été définie dans le script `before`, la commande `{{ var }}` permet d'insérer sa représentation textuelle dans l'énoncé.
    * Par ailleurs, un filtre `latex` permet d'insérer la représentation LaTeX d'un objet SymPy. Par exemple, si l'objet SymPy `obj` a été défini dans le script `before`, la commande `{{ obj|latex }}` permet d'insérer sa représentation LaTeX dans l'énoncé.
    * La mise en forme avancée du texte s'effectue avec des balises Markdown ou HTML.

#### Interface de réponse
* `input_prefix` (chaîne). Chaîne placée avant le champ de réponse. 
    * Par défaut, cette clé contient la chaîne `Réponse :`. 
    * Elle offre les mêmes possibilités de mise en forme que la clé `text`.
* `input_keypad` (liste de dictionnaires). Clavier virtuel. 
    * Par défaut, cette clé contient une lsite vide. 
    * Les éléments de la liste sont des dictionnaires représentant les boutons du clavier. Les clés de ces dictionnaires sont `label`, `action` et `value`.
* `input_embed` (chaîne). Formule dans laquelle est insérée le champ de réponse. 

#### Evluation de réponse
* `checkratsimp` (booléen Python). 
    * Si cette clé vaut `True`, l'exercice vérifie que les valeurs rationnelles sont simplifiées dans la réponse de l'élève. Des réponses du type $4+3$, $1+\fra{1}{2}$, $\sqrt{4+3}$, $\sqrt{4}$, etc. déclencheront un message d'avertissement.
    * Valeur par défaut : `True`.
* `unauthorized_func` (liste de chaînes Python). 
    * Cette clé contient les noms des fonctions non autorisées.
    * Valeur par défaut : `[]`.
* `symbol_dict` (dictionnaire Sympy). 
    * Cette clé contient le dictionnaire des symboles utilisé pour convertir la réponse de l'élève en expression SymPy.
    * Valeur par défaut : `{'e': E}`. Le symbole `e` est alors interprété comme le nombre d'Euler (objet SymPy `E`).
    * 
#### Messages
* `solution` (chaîne). Message de correction de l'exercice.
    * Cette clé offre les mêmes possibilités de mise en forme que la clé `text`.
* `hint` (chaîne). Message(s) d'indication.
    * Cette clé offre les mêmes possibilités de mise en forme que la clé `text`.
* `message.NotExpr` (chaîne). Message d'avertissement quand la réponse n'est pas un expression mathématique.
   * `La réponse doit être une expression mathématique.`
* `message.NotRatSimp` (chaîne). Message d'avertissement quand la réponse n'est pas simplifiée.
   * `L'expression peut encore être simplifiée.`
* `message.NotEqual` (chaîne). Message d'erreur.
   * `La réponse n'est pas égale à la solution.`

## Exemples

#### Calculer la distance entre deux points du plan

```
extends = /model/math/expr.pl

title = Calculer la distance entre deux points du plan

before ==
xA = randint(-5, 5)
yA = randint(-5, 5)
xB = randint(-5, 5)
yB = randint(-5, 5)
sol = sqrt((xA-xB)**2 + (yA-yB)**2)
==

text ==
Dans le plan muni d'un repère orthonormé on considère les points de coordonnées 
$! ( {{ xA }}, {{ yA }} ) !$ et $! ( {{ xB }}, {{ yB }} ) !$.

Quelle est la distance entre ces deux points ?
==
```

#### Exprimer une inconnue en fonction d'une autre

```
extends = /model/math/expr.pl

title = Exprimer une inconnue en fonction d'une autre

before ==
var('x y')
a = randint(-5, 5, [0])
b = randint(-5, 5, [0])
expr = a*y+b
sol = (x-b)/a
==

text ==
Soit deux nombres $! x !$ et $! y !$ tels que :
$$ x = {{ expr|latex }}.$$

Exprimer $! y !$ en fonction $! x !$.
==

input_prefix = $! y = !$
```

#### Valeurs remarquables de sinus et cosinus

```
extends = /model/math/expr.pl

title = Valeurs remarquables de sinus et cosinus

before ==
x = choice([pi/6, pi/4, pi/3, 3*pi/4, 2*pi/3, 5*pi/6])
f = choice([sin, cos]) 
sol = f(x)
==

text ==
Quelle est la valeur de la fonction $! {{ f|latex }} !$ en $!\displaystyle {{ x|latex }} !$ ?
==

unauthorized_func = ['sin', 'cos']
```

#### Calculer la dérivée d'une fonction


#### Déterminer l'équation d'une droite

```
extends = /model/math/expr.pl

title = Déterminer l'équation d'une droite

before ==
from mplsympy import plotsvg
var('x')
a = choice([-1, 1]) * sympify(choice(['1/2', 1, '3/2', 2]))
b = randint(-3, 3)
sol = a*x + b
image = plotsvg(sol)
==

text ==
Déterminer l'équation de la droite tracée ci-dessous (en notant $! x !$ la variable d'abscisse et $! y !$ la variable d'ordonnée).

<div class="img-container">
{{ image }}
</div>
==

input_prefix = $! y = !$

solution ==
L'équation de la droite est :
$$ y = {{ sol|latex }}. $$
==
```
