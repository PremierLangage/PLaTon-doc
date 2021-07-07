# N-ulets

Le modèle `math/tuple` permet de fabriquer des exercices où la réponse est de type n-uplet.

Les clés de base de ce modèles sont :

  * `question` : l'énoncé de l'exercice ;
  * `sol` : la solution.

La solution `sol` doit être un objet SymPy de type `Tuple`.

Le modèle contrôle que la réponse saisie est bien un n-uplet. 

```
extends = /model/math/tuple.pl

before ==
n0 = randint(-5, 5)
p0 = randint(-5, 5)
sol = Tuple(n0+p0, n0-p0)
==

question ==
On considère la fonction $! f : \mathbb{Z}^2 \rightarrow \mathbb{Z}^2  !$  définie par :
$$ f(n, p)= (n+p, n-p) .$$

Déterminer $! f( {{ n0 }}, {{ p0 }} ). !$
==
```
