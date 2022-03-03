# Exercices de base

## Clés communes

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
<th scope="row"> before </th>
<td> Script Python permettant de générer les clés de l&#39;exercice. </td>
<td> str </td>
<td>  </td>
</tr>

<tr>
<th scope="row"> title </th>
<td> Titre de l&#39;exercice. </td>
<td> str </td>
<td>  </td>
</tr>

<tr>
<th scope="row"> question </th>
<td> Template Markdown/HTML contenant l&#39;énoncé de l&#39;exercice. </td>
<td> str </td>
<td>  </td>
</tr>

<tr>
<th scope="row"> inputblock </th>
<td> Template Markdown/HTML contenant l&#39;énoncé de l&#39;exercice. </td>
<td> str </td>
<td>  </td>
</tr>

<tr>
<th scope="row"> solution </th>
<td> Template Markdown/HTML contenant la correction de l&#39;exercice. </td>
<td> str </td>
<td>  </td>
</tr>

<tr>
<th scope="row"> evaluator </th>
<td> Script Python permettant d&#39;évaluer la réponse de l&#39;exercice. </td>
<td> str </td>
<td>  </td>
</tr>

</tbody>
</table>

## Détails

### `before`

La clé `before` peut recevoir un script Python. Celui-ci est exécuté après le chargement des clés du fichier PL et avant la construction de la page de l'exercice. Toutes les clés du fichier PL sont utilisables et modifiables dans le script (une clé correspond simplement à la variable de même nom dans le script). Toute variable créée dans le script est ensuite convertie en clé de l'exercice (avec le même nom).

La version de Python utilisée est la version 3.7. Tous les modules de la [bibliothèque standard](https://docs.python.org/fr/3/library/index.html) peuvent être importés. D'autres [modules usuels](https://documentationpl.readthedocs.io/fr/latest/technic_doc/modules_sandbox.md), ainsi que des modules propres à la plateforme, sont également disponibles.

Pour alléger l'écriture du script `before`, un certain nombre de fonctions sont importées automatiquement avant l'exécution du script `before`.

```
from random import choice, choices, sample, shuffle
from plrandom import randint, sampleint
from plcsv import csv_choice, csv_sample, csv_col
```

### `question`


Pour insérer dynamiquement les données générées par le script `before` dans l'énoncé de l'exercice, la clé `question` admet un système de **template**. Le contenu d'une clé `key`, définie explicitement ou dynamiquement dans le script `before`, peut être inséré dans la clé `question` en utilisant l'expression `{{ key }}`.


**Exemple**

```
before ==
capitale = choice(["Paris", "Berlin", "Rome"])
==

question ==
Quel pays a pour capitale {{ capitale }} ?
==
```
