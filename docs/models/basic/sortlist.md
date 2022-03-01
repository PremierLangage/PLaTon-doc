# Modèle `basic/sortlist`

Le modèle `basic/sortlist` permet de fabriquer des exercices où l'élève doit ordonner des items. La liste des items peut être déclarée explicitement ou générée par un script Python.

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
<th scope="row"> sortedlist </th>
<td> Liste des items. Elle peut être saisie comme une liste ou comme une chaîne multilignes (chaque ligne correspondant à un item). </td>
<td> (str, list[str]) </td>
<td> [] </td>
</tr>

<tr>
<th scope="row"> nbitems </th>
<td> Nombre d&#39;items à ordonner parmi la liste d&#39;items. Si ce nombre n&#39;est pas précisé, tous les items de la liste sont pris. </td>
<td> (int, None) </td>
<td> None </td>
</tr>

<tr>
<th scope="row"> scoring </th>
<td> Barème de l&#39;exercice. </td>
<td> (&#39;KendalTau&#39;, &#39;ExactOrder&#39;) </td>
<td> &#39;KendalTau&#39; </td>
</tr>

</tbody>
</table>

## Exemples (avec une liste déclarée explicitement)

#### Ordre alphabétique

~~~
extends = model/basic/sortlist.pl

question ==
Classer les mots suivants dans l'ordre alphabétique.
==

sortedlist ==
Abricot
Avion
Ballon
Cartable
==
~~~

#### Premiers Ministres

~~~
extends = /model/basic/sortlist.pl

question ==
Classer ces premiers ministres de la Ve République du plus ancien 
au plus récent (selon la date d'entrée en fonction).
==

nbitems = 5

sortedlist ==
Édouard Balladur
Alain Juppé
Lionel Jospin
Jean-Pierre Raffarin
Dominique de Villepin
François Fillon
Jean-Marc Ayrault
Manuel Valls
Bernard Cazeneuve
Édouard Philippe
Jean Castex
==

scoring = KendallTau
~~~

## Exemples (avec une liste générée par un script)

```
extends = /model/basic/sortlist.pl

question ==
Classer les nombres suivants du plus petit au plus grand.
==

before ==
sortedlist = list(range(1, 100))
==

nbitems = 5
```
