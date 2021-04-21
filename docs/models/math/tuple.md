# Modèle `math/tuple`

Le modèle `math/tuple` est un modèle dérivé du modèle `math/input`. Le script d'évaluation `evaluator` y est prédéfini. Il compare la réponse de l'élève à une solution attendue de type n-uplet.

## Clés du modèle

Les clés `title`, `text`, `input_prefix`, `solution`, `hint`, `latexsettings` ont la même signification et la même syntaxe que dans le modèle `math/input`.

* `before` (script Python). Script de génération des données et de la solution. 
    * Le script doit définir une variable `sol` contenant la solution. Cette solution doit être un objet SymPy de type `Tuple`.

## Exemples

#### Image par une application de Z^2 dans Z^2

```
extends = /model/math/tuple.pl

title = Image par une application de Z^2 dans Z^2

before ==
n0 = randint(-5, 5)
p0 = randint(-5, 5)
sol = Tuple(n0+p0, n0-p0)
==

text ==
On considère la fonction $! f : \mathbb{Z}^2 \rightarrow \mathbb{Z}^2  !$  définie par :
$$ f(n, p)= (n+p, n-p) .$$

Déterminer $! f( {{ n0 }}, {{ p0 }} ). !$
==
```
