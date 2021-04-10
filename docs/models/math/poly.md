# Modèle `math/poly`

Le modèle `math/poly` est un modèle dérivé du modèle `math/input` pour des exercices où la réponse est unique et de type polynôme. Le script d'évaluation y est prédéfini.

## Clés du modèle

#### Clés de base
* `title` (chaîne). Titre de l'exercice.
* `before` (script Python). Script de génération des données et de la solution. 
    * La solution doit être une [expression SymPy](https://docs.sympy.org/latest/modules/core.html?#module-sympy.core.expr). et doit être stockée dans la variable `sol`.
* `text` (chaîne). Enoncé de l'exercice. 

#### Interface de réponse
* `input_prefix` (chaîne). Chaîne placée avant le champ de réponse.

#### Evaluation de la réponse
* `poly_form` (chaîne). Forme attendue de la réponse.
    * `expanded`
    * `factorized`
    * Valeur par défaut : chaîne vide.
