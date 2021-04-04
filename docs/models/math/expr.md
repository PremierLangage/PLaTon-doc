# Modèle `math/expr`

Le modèle `math/expr` permet de créer des exercices dont la réponse est une expression mathématique.

## Clés du modèle

#### Clés de base
* `title` (chaîne). Titre de l'exercice.
* `before` (script Python). Ce script est exécuté au lancement de l'exercice. Il permet de générer les données de l'énoncé ainsi que la solution.
* `text` (string). Enoncé de l'exercice.

#### Interface de réponse
* `input_prefix` (chaîne). Chaîne placée avant le champ de réponse.
* `form` (string). Solution de l'exercice.

#### Evaluation de la réponse
* `checkratsimp` (booléen Python, valeur par défaut : `True`). Si cette clé vaut `True`, l'exercice vérifie que les valeurs rationnelles sont simplifiées dans la réponse de l'élève.
* `unauthorized_func` (liste de chaînes Python, valeur par défaut : `[]`). Cette clé contient les noms des fonctions non autorisées.
* `symbol_dict` (dictionnaire Sympy). Dictionnaire des symboles utilisées pour interpréter la réponse de l'élève.

#### Indications et solution
* `solution` (chaîne). Solution de l'exercice.
* `hint` (chaîne). Indication.
