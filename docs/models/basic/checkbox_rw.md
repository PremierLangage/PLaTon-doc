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
<td> Nombre d&#39;items à proposer.</td>
<td> int </td>
<td> 0 </td>
</tr>

<tr>
<th scope="row"> maxright </th>
<td> Nombre maximum de bonnes réponses à proposer. </td>
<td> int </td>
<td> 0 </td>
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

## Exemples

### Exemple 1

Adresse : `/demo/basic/checkbow_rw/capitales.pl`

```
extends = /model/basic/checkbox.pl

question ==
Parmi ces villes, lesquelles sont des capitales d'états européens ?
==

right ==
Paris
Rome
Madrid
Berlin
Londres
Bruxelles
Berne
==

wrong ==
Lyon
Milan
Barcelone
Munich
Liverpool
Anvers
Genève
==

nbitems = 5

minright = 1

maxright = 3
```

### Exemple 2

Adresse : `/demo/basic/checkbow_rw/multiples_de_3.pl`

```
extends = /model/basic/checkbox_rw.pl

before ==
right = [str(n) for n in range(50, 100) if n % 3 == 0]
wrong = [str(n) for n in range(50, 100) if n % 3 != 0]
==

question ==
Parmi les nombres suivants, lesquels sont des multiples de 3 ?
==

nbitems = 4

minright = 2

maxright = 3
```
