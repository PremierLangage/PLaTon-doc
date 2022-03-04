# Modèle `math/tuple`

Le modèle `math/tuple` est un modèle dérivé du modèle `math/input`. Le script d'évaluation `evaluator` y est prédéfini. Il compare la réponse de l'élève à une solution attendue de type n-uplet.

## Clés spécifiques

            
<table class="table">
<thead>
<tr>
<th scope="col">Clé</th>
<th scope="col">Description</th>
<th scope="col">Type</th>
<th scope="col">Défaut</th>
</tr>
</thead>
<tbody>

<tr>
<th scope="row"> sol </th>
<td> Bonne réponse. Elle doit être définie dans le script `before` comme une liste/tuple d'objets SymPy ou un objet SymPy de type Tuple. </td>
<td> (list, tuple, Tuple </td>
<td>  </td>
</tr>

<tr>
<th scope="row"> checksize </th>
<td> Valeur indiquant si une réponse de taille incorrecte déclenche un avertissement. </td>
<td> bool </td>
<td> 'False </td>
</tr>

</tbody>
</table>

## Exemples

### Exemple 1 : Image par une application de Z^2 dans Z^2

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
