# Modèle de base (1)

Le modèle `math/expr` permet de fabriquer des exercices aléatoires où la réponse est une expression mathématique (expression impliquant des nombres, des variables, des opérations algébriques et des fonctions).

Les clés de base de ce modèles sont :

  * `question` : l'énoncé de l'exercice ;
  * `sol` : la solution.

La solution `sol` doit être un objet SymPy de type `Expr`.
