# Modèle `math/numeric`

Le modèle `math/numeric` est un modèle dérivé du modèle `math/input`. Le script d'évaluation `evaluator` y est prédéfini. Il compare la réponse de l'élève à une solution attendue de type numérique.

## Clés du modèle

Les clés `title`, `text`, `input_prefix`, `solution`, `hint`, `latexsettings` ont la même signification et la même syntaxe que dans le modèle `math/input`.

* `before` (script Python). Script de génération des données et de la solution. 
    * Le script doit définir une variable `sol` contenant la solution. Cette solution doit être un nombre (`int`, `float`, `Float`).
* `diffmeasure` (chaîne). Mesure de la différence entre la solution et la réponse de l'élève.
    * `Absolute` ou `Relative`
    * Valeur par défaut : `Absolute`.
* `tol` (nombre). Tolérance
    * Tolérance pour la réponse.
    * Valeur par défaut : `0`.
