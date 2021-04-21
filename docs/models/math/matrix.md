# Modèle `math/matrix`

Le modèle `math/matrix` permet de créer des exercices dont la réponse est une matrice.

* Le champ de réponse permet de saisir facilement une matrice. 

## Clés du modèle

* `before` (script Python). Script de génération des données et de la solution.
    * Le script doit définir une variable `sol` contenant la solution. Cette solution doit être un objet SymPy de type `Matrix`.
