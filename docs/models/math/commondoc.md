# Documentation commune

Tous ces modèles permettent de créer des exercices dont la réponse est une expression mathématique. Le champ de réponse permet de saisir facilement une expression mathématique avec un rendu de type TeX. Chaque modèlede l'exercice et l'évaluation de la réponse de l'élève est effectuée par des scripts Python.

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

## Détailes

### `before`


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

### `question`




## Annexes


## Description

Les données et la solution de l'exercice doivent être générées par un script Python contenu dans la clé `before`. Pour définir et manipuler des expressions mathématiques, on utilise la [bibliothèque SymPy](https://www.sympy.org/en/index.html). En particulier, la solution doit être définie comme un objet SymPy de type `Expr`.

L'énoncé de l'exercice doit être saisi dans la clé `question`.

    * L'insertion de formules mathématiques s'effectue avec du code LaTeX dans les balises `$!...!$` (mode en ligne) ou `$$...$$` (mode équation).
    * L'insertion dynamique de données produites par le script `before` s'effectue à l'aide des balises `{{...}}`. Par exemple, si la variable `var` a été définie dans le script `before`, la commande `{{ var }}` permet d'insérer sa représentation textuelle dans l'énoncé.
    * Par ailleurs, un filtre `latex` permet d'insérer la représentation LaTeX d'un objet SymPy. Par exemple, si l'objet SymPy `obj` a été défini dans le script `before`, la commande `{{ obj|latex }}` permet d'insérer sa représentation LaTeX dans l'énoncé.
    * La mise en forme avancée du texte s'effectue avec des balises HTML.

L'évaluation de la réponse de l'élève est automatique.


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
