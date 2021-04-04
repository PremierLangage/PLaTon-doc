# Modèle `math/expr`

Le modèle `math/expr` permet de créer des exercices dont la réponse est une expression mathématique.

## Clés du modèle

#### Clés de base
* `title` (chaîne). Titre de l'exercice.
* `before` (script Python). Script de génération des données et de la solution. Ce script est exécuté au lancement de l'exercice. Un certain nombre d'importations de fonctions sont faites automatiquement (voir annexe ci-après). La solution doit être une [expression SymPy](https://docs.sympy.org/latest/modules/core.html?#module-sympy.core.expr). et doit être stockée dans la variable `sol`.
* `text` (chaîne). Enoncé de l'exercice. L'insertion dynamique de données produites par le script `before` s'effectue à l'aide des balises `{{...}}`.

#### Interface de réponse
* `input_prefix` (chaîne). Chaîne placée avant le champ de réponse. Par défaut, cette chaîne est `Réponse :`.
* `form` (string). Solution de l'exercice.

#### Evaluation de la réponse
* `checkratsimp` (booléen Python, valeur par défaut : `True`). Si cette clé vaut `True`, l'exercice vérifie que les valeurs rationnelles sont simplifiées dans la réponse de l'élève.
* `unauthorized_func` (liste de chaînes Python, valeur par défaut : `[]`). Cette clé contient les noms des fonctions non autorisées.
* `symbol_dict` (dictionnaire Sympy). Dictionnaire des symboles utilisées pour interpréter la réponse de l'élève.

#### Indications et solution
* `solution` (chaîne). Solution de l'exercice.
* `hint` (chaîne). Indication.
