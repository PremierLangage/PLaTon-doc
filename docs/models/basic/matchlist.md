# Modèle `basic/matchlist`

Le modèle `basic/matchlist` permet de fabriquer des exercices de correspondances.

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
<th scope="row"> matches </th>
<td> Liste des correspondances (source, cible). Elle peut être saisie comme une liste de couples ou comme une chaîne multilignes (chaque ligne correspondant à une correspondance, les deux éléments étant distingués par un séparateur défini dans la clé `separator`). </td>
<td> (str, list[tuple[str, str]] </td>
<td> [] </td>
</tr>

<tr>
<th scope="row"> separator </th>
<td> Séparateur des éléments d&#39;une correspondance (source, cible). </td>
<td> str </td>
<td> &#39;,&#39; </td>
</tr>

<tr>
<th scope="row"> nbmatches </th>
<td> Nombre de correspondances à proposer parmi la liste de correspondances. Si cette clé vaut `None`, toutes les correspondances sont proposées. </td>
<td> (int, None) </td>
<td> None </td>
</tr>

<tr>
<th scope="row"> targets </th>
<td> Liste de cibles supplémentaires. Elle peut être saisie comme une liste ou comme une chaîne multilignes (chaque ligne correspondant à un item). </td>
<td> (str, list[str]) </td>
<td> [] </td>
</tr>

<tr>
<th scope="row"> multiple </th>
<td> Valeur indiquant si une cible peut être reliée à plusieurs sources. </td>
<td> bool </td>
<td> True </td>
</tr>

<tr>
<th scope="row"> scoring </th>
<td> Barème de l&#39;exercice. </td>
<td> (&#39;AllOrNothing&#39;, &#39;RightMinusWrong&#39;, &#39;CorrectItems&#39;) </td>
<td> &#39;RightMinusWrong&#39; </td>
</tr>

</tbody>
</table>
           
TODO : Une option `strip` ou `skipinitialspace` pour éliminer les espaces superflus dans `matches`.

TODO : Revoir les barèmes (Comment compter une source non reliée ? une cible non reliée ? etc.)

## Exemples

### Exemple 1 : Capitales

~~~
extends = /model/basic/matchlist.pl

question ==
Relier chaque pays à sa capitale.
==

matches ==
France,Paris
Italie,Rome
Allemagne,Berlin
Espagne,Madrid
==
~~~

### Exemple 2 : Capitales

```
extends = /model/basic/matchlist.pl

question ==
Relier chaque pays à sa capitale.
==

separator = ";"

nbmatches = 4

matches ==
Allemagne;Berlin
Autriche;Vienne
Belgique;Bruxelles
Danemark;Copenhague
Espagne;Madrid
Finlande;Helsinki
France;Paris
Grèce;Athènes
Hongrie;Budapest
Irlande;Dublin
Italie;Rome
Norvège;Oslo
Pays-Bas;Amsterdam
Pologne;Varsovie
Portugal;Lisbonne
Roumanie;Bucarest
Royaume-Uni;Londres
Slovaquie;Bratislava
Suède;Stockholm
Suisse;Berne
==
```

### Exemple 3 (avec une liste générée par un script)

```
extends = /model/basic/matchlist.pl

question ==
Relier chaque nombre à la décomposition qui lui est égale.
==

before ==
matches = []
for a in sample(range(10, 20), 4) :
    b = randint(1, a-1)
    c = a - b
    matches.append([str(a), f"{b} + {c}"])
==
```
