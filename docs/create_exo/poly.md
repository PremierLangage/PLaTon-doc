# Polynômes

Le modèle `math/poly` permet de fabriquer des exercices où la réponse est de type polynôme.

Les clés de base de ce modèles sont :

  * `question` : l'énoncé de l'exercice ;
  * `sol` : la solution.

La solution `sol` doit être un objet SymPy de type expression polynômiale.

Par défaut, le modèle contrôle que la réponse saisie est un polynôme, mais il n'impose aucune forme particulière pour ce nombre. La clé `poly_form` permet d'imposer une forme developpée (`expanded`) ou factorisé (`factorized`).
