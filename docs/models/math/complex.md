# Modèle `math/complex`

Le modèle `math/complex` est un modèle dérivé du modèle `math/input`. Le script d'évaluation `evaluator` y est prédéfini. Il compare la réponse de l'élève à une solution attendue de type nombre complexe.

## Clés du modèle

Les clés `title`, `text`, `input_prefix`, `solution`, `hint`, `latexsettings` ont la même signification et la même syntaxe que dans le modèle `math/input`.

* `before` (script Python). Script de génération des données et de la solution. 
    * Le script doit définir une variable `sol` contenant la solution. Cette solution doit être un objet SymPy de type `Complex`.
* `imaginary_unit` (chaîne). Nom de l'unité imaginaire.
    * Nom de l'unité imaginaire utilisée pour interpréter la réponse de l'élève.
    * Par défaut, cette clé vaut `i`.
* `complex_form` (chaîne). Forme attendue de la réponse de l'élève.
    * Les 3 valeurs possibles sont : chaîne vide (pas de forme particulière), `cartesian` (forme cartésienne) et `exponential` (forme exponentielle).
    * Par défaut, la valeur de cette clé est une chaîne vide.

## Exemples

#### Multiplier deux nombres complexes

```
extends = /model/math/complex.pl

title = Multiplier deux nombres complexes

before ==
z1 = randint(-5, 5, [0]) + randint(-5, 5, [0])*I
z2 = randint(-5, 5, [0]) + randint(-5, 5, [0])*I
sol = (z1 * z2).expand()
==

text ==
On considère les nombres complexes $! z_1 = {{ z1|latex }} !$ et $! z_2 = {{ z2|latex }} !$. 

Calculer $! z_1 \times z_2 !$ (sous forme algébrique).
==

complex_form = cartesian
```
