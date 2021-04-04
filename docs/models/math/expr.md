# Modèle `math/expr`

Le modèle `math/expr` permet de créer des exercices dont la réponse est une expression mathématique.

## Clés du modèle

#### Clés de base
* `title` (chaîne). Titre de l'exercice.
* `before` (script Python). Script de génération des données et de la solution. Ce script est exécuté au lancement de l'exercice. Un certain nombre d'importations de fonctions sont faites automatiquement (voir annexe ci-après). La solution doit être une [expression SymPy](https://docs.sympy.org/latest/modules/core.html?#module-sympy.core.expr). et doit être stockée dans la variable `sol`.
* `text` (chaîne). Enoncé de l'exercice. 
  * L'insertion de formules mathématiques s'effectue avec du code LaTeX dans les balises `$!...!$` (mode en ligne) ou `$$...$$` (mode équation).
  * L'insertion dynamique de données produites par le script `before` s'effectue à l'aide des balises `{{...}}`. Par exemple, si la variable `var` a été définie dans le script `before`, la commande `{{ var }}` permet d'insérer sa représentation textuelle dans l'énoncé.
  * Par ailleurs, un filtre `latex` permet d'insérer sa représentation LaTeX d'un objet SymPy. Par exemple, si l'objet SymPy `obj` a été défini dans le script `before`, la commande `{{ obj|latex }}` permet d'insérer sa représentation LaTeX dans l'énoncé.
  * La mise en forme avancée du texte s'effectue avec des balises Markdown ou HTML.

#### Interface de réponse
* `input_prefix` (chaîne). Chaîne placée avant le champ de réponse. Par défaut, cette chaîne est `Réponse :`.

#### Evaluation de la réponse
* `checkratsimp` (booléen Python, valeur par défaut : `True`). Si cette clé vaut `True`, l'exercice vérifie que les valeurs rationnelles sont simplifiées dans la réponse de l'élève. Des réponses du type $4+3$, $1+\fra{1}{2}$, $\sqrt{4+3}$, $\sqrt{4}$, etc. déclencheront un message d'avertissement.
* `unauthorized_func` (liste de chaînes Python, valeur par défaut : `[]`). Cette clé contient les noms des fonctions non autorisées.
* `symbol_dict` (dictionnaire Sympy). Dictionnaire des symboles utilisées pour interpréter la réponse de l'élève.

#### Indications et solution
* `solution` (chaîne). Solution de l'exercice.
* `hint` (chaîne). Indication.
