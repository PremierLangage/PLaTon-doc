# Modèle `basic/autoinput`

Le modèle `basic/autoinput` permet de fabriquer des exercices avec un champ de réponse textuel proposant des suggestions (par un système d'autocomplétion).

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
<th scope="row"> items </th>
<td> Liste des items. Elle peut être saisie comme une liste ou comme une chaîne multilignes (chaque ligne correspondant à un item). </td>
<td> (str, list[str]) </td>
<td>  </td>
</tr>

<tr>
<th scope="row"> prefix </th>
<td> Texte affiché à gauche du champ de réponse. </td>
<td> str </td>
<td> 'Réponse :' </td>
</tr>

</tbody>
</table>


## Exemples

```
extends = /model/basic/autoinput.pl

question ==
Quel pays a pour capitale Paris ?
==

sol ==
France
==

items ==
Allemagne
Autriche
Belgique
Danemark
Espagne
Finlande
France
Grèce
Hongrie
Irlande
Italie
Norvège
Pays-Bas
Pologne
Portugal
Roumanie
Royaume-Uni
Slovaquie
Suède
Suisse
==
```
