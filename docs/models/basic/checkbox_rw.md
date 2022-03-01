# Modèle `basic/checkbox_rw`

Le modèle `basic/checkbox_rw` permet de fabriquer des exercices à choix multiples (avec plusieurs réponses possibles). Les données de l'exercices sont fournies sous la forme d'une liste de bonnes réponses et d'une liste de mauvaises réponses.

## Clés spécifiques du modèle

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
<th scope="row"> right </th>
<td> Liste des bonnes réponses. Elle peut être saisie comme une liste ou comme une chaîne multilignes (chaque ligne correspondant à un item). </td>
<td> (str, list[str]) </td>
<td> [] </td>
</tr>

<tr>
<th scope="row"> wrong </th>
<td> Liste des mauvaises réponses. Elle peut être saisie comme une liste ou comme une chaîne multilignes (chaque ligne correspondant à un item). </td>
<td> (str, list[str]) </td>
<td> [] </td>
</tr>

<tr>
<th scope="row"> nbitems </th>
<td> Nombre d&#39;items à proposer. Si cette clé vaut None, tous les items sont proposés. </td>
<td> (int, None) </td>
<td> None </td>
</tr>

<tr>
<th scope="row"> maxright </th>
<td> Nombre minimum de bonnes réponses à proposer. Si cette clé vaut None, toutes les bonnes réponses sont proposées. </td>
<td> (int, None) </td>
<td> None </td>
</tr>

<tr>
<th scope="row"> minright </th>
<td> Nombre minimum de bonnes réponses à proposer. </td>
<td> int </td>
<td> 0 </td>
</tr>
 
<tr>
<th scope="row"> scoring </th>
<td> Barème de l&#39;exercice. </td>
<td> (&#39;AllOrNothing&#39;, &#39;RightMinusWrong&#39;, &#39;CorrectItems&#39;) </td>
<td> &#39;RightMinusWrong&#39; </td>
</tr>

</tbody>
</table>
## Exemples (avec déclaration explicite des listes de réponses)

```
extends = /model/basic/checkbox_rw.pl

text ==
Indiquer parmi les noms suivants ceux qui sont des noms valides pour une variable en Python.
==

nbitems = 5
minright = 2
maxright = 3

right ==
bonjour
abc
oui
NON
Ciao
good_morning
byeBye7
\_UGE\_
==

wrong ==
Hi!
au revoir
6hello6
def
for
good-afternoon
f()
==
```

## Exemples (avec génération des listes de réponses)

```
extends = /model/basic/checkbox_rw.pl

title = Multiples de 3

nbitems % 5
minright % 1
maxright % 4

before ==
right = [str(n) for n in range(50, 100) if n % 3 == 0]
wrong = [str(n) for n in range(50, 100) if n % 3 != 0]
==

text ==
Parmi les nombres suivants, lesquels sont des multiples de 3 ?
==
```
