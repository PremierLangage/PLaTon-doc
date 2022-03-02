# Modèle `basic/filltext`

Le modèle `basic/filltext` permet de fabriquer des exercices de type *texte à trous*

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
<th scope="row"> filledtext </th>
<td> Texte complet, avec les parties à compléter spécifiées par les délimiteurs définies dans la clé `delimiters`. </td>
<td> str </td>
<td>  </td>
</tr>

<tr>
<th scope="row"> delimiters </th>
<td> Délimiteurs utilisés pour spécifier les parties à compléter. </td>
<td> lst[str] </td>
<td> [&#39;{&#39;, &#39;}&#39;] </td>
</tr>

<tr>
<th scope="row"> labels </th>
<td> Liste d&#39;étiquettes supplémentaires. Elle peut être saisie comme une liste ou comme une chaîne multilignes (chaque ligne correspondant à un item). </td>
<td> (str, list[str]) </td>
<td> [] </td>
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

#### Génétique

~~~
extends = /model/basic/filltext.pl

title = Génétique

question ==
Compléter le texte suivante avec les bonnes étiquettes.
==

filledtext ==
L’ensemble des gènes caractéristiques de l’espèce à laquelle appartient un organisme, constitue son {génome}. 
Chez les individus d’une même espèce, un gène peut cependant exister sous différentes formes présentant de légères modifications de séquence : les allèles. 
L’ensemble des allèles d’un individu définit son {génotype}. Lorsqu’ils s’expriment, lors de la synthèse des protéines, les gènes participent à la construction de l’individu et à la mise en place de son {phénotype}. 
==

labels ==
caryotype
ADN
ARN
==
~~~
