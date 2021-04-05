# Modèle `math/input`

Le modèle `math/expr` permet de créer des exercices dont la réponse est une expression mathématique. Par expression mathématique, on entend une expression faisant intervenir des nombres, des variables, des opérations algébriques et des fonctions.

## Clés du modèle

#### Clés de base
* `title` (chaîne). Titre de l'exercice.

    Le titre doit décrire la tâche à effectuer dans l'exercice. Il n'est pas destiné aux élèves.


* `before` (script Python). Script de génération des données et de la solution.

    Ce script est exécuté au lancement de l'exercice. Un certain nombre d'importations de fonctions sont faites automatiquement (voir annexe ci-après). La solution doit être une [expression SymPy](https://docs.sympy.org/latest/modules/core.html?#module-sympy.core.expr). et doit être stockée dans la variable `sol`.

* `text` (chaîne). Enoncé de l'exercice. 
    * L'insertion de formules mathématiques s'effectue avec du code LaTeX dans les balises `$!...!$` (mode en ligne) ou `$$...$$` (mode équation).
    * L'insertion dynamique de données produites par le script `before` s'effectue à l'aide des balises `{{...}}`. Par exemple, si la variable `var` a été définie dans le script `before`, la commande `{{ var }}` permet d'insérer sa représentation textuelle dans l'énoncé.
    * Par ailleurs, un filtre `latex` permet d'insérer la représentation LaTeX d'un objet SymPy. Par exemple, si l'objet SymPy `obj` a été défini dans le script `before`, la commande `{{ obj|latex }}` permet d'insérer sa représentation LaTeX dans l'énoncé.
    * La mise en forme avancée du texte s'effectue avec des balises Markdown ou HTML.

* `evaluator` (script Python). Script d'évaluation de la réponse.


#### Interface de réponse
* `input_prefix` (chaîne). Chaîne placée avant le champ de réponse. Par défaut, cette chaîne est `Réponse :`.

#### Messages
* `solution` (chaîne). Solution de l'exercice.
* `hint` (chaîne). Indication.

## Exemples
