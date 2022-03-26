# Documentation commune

Tous ces modèles permettent de créer des exercices dont la réponse est une expression mathématique. Le champ de réponse permet de saisir facilement une expression mathématique avec un rendu de type TeX. Chaque modèle propose une évaluation spécifique de la réponse : expression, nombres complexes, polynômes, etc.

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
<th scope="row"> before </th>
<td> Script Python permettant de générer les clés de l'exercice. </td>
<td> str </td>
<td>  </td>
</tr>

<tr>
<th scope="row"> title </th>
<td> Titre de l'exercice. </td>
<td> str </td>
<td>  </td>
</tr>

<tr>
<th scope="row"> question </th>
<td> Template HTML contenant l'énoncé de l'exercice. </td>
<td> str </td>
<td>  </td>
</tr>

<tr>
<th scope="row"> inputblock </th>
<td> Template HTML contenant l'énoncé de l'exercice. </td>
<td> str </td>
<td>  </td>
</tr>

<tr>
<th scope="row"> solution </th>
<td> Template HTML contenant la correction de l'exercice. </td>
<td> str </td>
<td>  </td>
</tr>

<tr>
<th scope="row"> evaluator </th>
<td> Script Python permettant d'évaluer la réponse de l'exercice. </td>
<td> str </td>
<td>  </td>
</tr>

<tr>
<th scope="row"> keypad </th>
<td> Liste des boutons du clavier virtuel attaché au champ de réponse. </td>
<td> list </td>
<td> [] </td>
</tr>

<tr>
<th scope="row"> embed </th>
<td> Formule dans laquelle est insérée le champ de réponse. </td>
<td> str </td>
<td> '' </td>
</tr>

<tr>
<th scope="row"> checkratsimp </th>
<td> Valeur indiquant si l'évaluation vérifie que les valeurs rationnelles sont simplifiées dans la réponse saisie. </td>
<td> bool </td>
<td> True </td>
</tr>

<tr>
<th scope="row"> symbol_dict </th>
<td> Dictionnaire des symboles utilisés pour convertir la réponse saisie en expression SymPy. </td>
<td> dict </td>
<td> {'e': E} </td>
</tr>

<tr>
<th scope="row"> unauthorized_func </th>
<td> Liste des fonctions non autorisées. </td>
<td> list[str] </td>
<td> [] </td>
</tr>

<tr>
<th scope="row"> latexsettings </th>
<td> Dictionnaire des paramètres de conversion SymPy vers LaTeX. </td>
<td> dict </td>
<td> {} </td>
</tr>

</tbody>
</table>

## Détails

### `before`

La clé `before` peut recevoir un script Python. Celui-ci est exécuté après le chargement des clés du fichier PL et avant la construction de la page de l'exercice. Toutes les clés du fichier PL sont utilisables et modifiables dans le script (une clé correspond simplement à la variable de même nom dans le script). Toute variable créée dans le script est ensuite convertie en clé de l'exercice (avec le même nom).

La version de Python utilisée est la version 3.7. Tous les modules de la [bibliothèque standard](https://docs.python.org/fr/3/library/index.html) peuvent être importés. D'autres [modules usuels](https://documentationpl.readthedocs.io/fr/latest/technic_doc/modules_sandbox.md), ainsi que des modules propres à la plateforme, sont également disponibles.

En particulier les modules suivants sont disponibles :
  * `sympy` : calcul symbolique (https://docs.sympy.org)
  * `plrandom` : fonctions aléatoires (bibliothèque locale)
  * `randsympy` : génération aléatoire d'objets SymPy (bibliothèque locale)
  * `sympy2latex` : conversion d'objets SymPy en LateX (bibliothèque locale)
  * `latex2sympy` : conversion d'expressions LateX en objets SymPy (bibliothèque locale)

Pour alléger l'écriture du script `before`, un certain nombre de fonctions sont importées automatiquement avant l'exécution du script `before`.

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

L'insertion de formules mathématiques s'effectue avec du code LaTeX dans les balises `$!...!$` (mode en ligne) ou `$$...$$` (mode équation).

Pour insérer les données générées par le script `before` dans l'énoncé de l'exercice, la clé `question` utilise le moteur de **template** Jinja. En particulier, le contenu d'une variable `var` créée dans le script `before` peut être inséré en utilisant la syntaxe `{{ var }}`.

Par ailleurs, un filtre `latex` permet d'insérer la représentation LaTeX d'un objet SymPy. Par exemple, si l'objet SymPy `obj` a été défini dans le script `before`, la commande `{{ obj|latex }}` permet d'insérer sa représentation LaTeX dans l'énoncé.

La mise en forme avancée de l'énoncé s'effectue avec des balises HTML.

### `keypad`

Les clés de ces dictionnaires sont `label`, `action` et `value`.

### `embed`

Cette clé permet de définir une expression mathématique dans laquelle sera insérée le champ de réponse. Cette expression doit être écrite en LaTeX et la position du champ de réponse doit être indiquée par un croisillon (`#`) au sein de cette expression.

**Exemple.**
```
embed ==
\sqrt{ # }
==
```

### `checkratsimp`

Si cette clé vaut `True`, l'exercice vérifie que les valeurs rationnelles sont simplifiées dans la réponse de l'élève. Des réponses du type $4+3$, \( 1+\fra{1}{2} \), \\( \sqrt{4+3} \\), $\sqrt{4}$, etc. déclencheront un message d'avertissement.

### `latexsettings`

https://docs.sympy.org/latest/modules/printing.html?#module-sympy.printing.latex
