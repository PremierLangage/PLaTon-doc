# Modèle `basic/textinput`

Le modèle `basic/textinput` permet de fabriquer des exercices avec un champ de réponse textuel.

[![](input1.png)](https://pl.u-pem.fr/filebrowser/demo/33986/)

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
<td> Liste des réponses acceptées. Elle peut être saisie comme une liste ou comme une chaîne multilignes (chaque ligne correspondant à un item). </td>
<td> (str, list[str]) </td>
<td> [] </td>
</tr>

<tr>
<th scope="row"> diffmeasure </th>
<td> Mesure utilisée pour calculer l&#39;écart entre la réponse saisie et les réponses acceptées. </td>
<td> (&#39;EditDist&#39;, &#39;EditRation&#39;) </td>
<td> &#39;EditDist&#39; </td>
</tr>
   
<tr>
<th scope="row"> tol </th>
<td> Ecart maximum (par rapport à la mesure définie dans `diffmeasure`) pour considérer une réponse comme correcte. </td>
<td> (int, float) </td>
<td> 0 </td>
</tr>
   
<tr>
<th scope="row"> casesens </th>
<td> Valeur indiquant si la casse est prise en compte pour évaluer la réponse. </td>
<td> bool </td>
<td> False </td>
</tr>

<tr>
<th scope="row"> prefix </th>
<td> Texte affiché à gauche du champ de réponse. </td>
<td> str </td>
<td> &#39;Réponse :&#39; </td>
</tr>

</tbody>
</table>

TODO : Un 2e seuil de tolérance qui déclencherait un avertissement ?

## Exemples

#### Littérature

Dans cet exemple, les solutions acceptées sont `Victor Hugo`, `Hugo`, mais aussi, puisque par défaut on ne tient pas compte de la casse, `victor hugo`, `victor Hugo`, `HUGO`, etc.

[Tester l'exercice](https://pl.u-pem.fr/filebrowser/demo/33986/)

~~~
extends = /model/basic/textinput.pl

question ==
Qui a écrit *Les Misérables* ?
==

sol ==
Victor Hugo
Hugo
==
~~~

#### Chimie

Dans cet exemple, les solutions acceptées sont les chaînes égales à `Oxygène` à un caractère près : `oxigène`, `oxgène`, `oxygèn`, etc.

[Tester l'exercice](https://pl.u-pem.fr/filebrowser/demo/34253/)

~~~
extends = /model/basic/input.pl

title ==
Chimie
==

question ==
Quel élément chimique a pour symbole **O** ?
==

sol ==
Oxygène
==

diffmeasure = EditDist

tol = 1
~~~

#### Listening

~~~
extends = /model/basic/input.pl

title = Listening

file =$ english_sentence.mp3

text ==
{{ audio_button(file) }} Transcrire la phrase.
==

sol ==
I'm gonna make him an offer he can't refuse
==

diffmeasure = EditRatio

tol =0.1
~~~
