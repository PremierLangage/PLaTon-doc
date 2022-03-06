# Modèle `quiz/AMC_TXT`

Le modèle `quiz/AMC_TXT` permet de fabriquer des quiz à partir de données au format [AMC-TXT](https://www.auto-multiple-choice.net/auto-multiple-choice.fr/AMC-TXT.shtml).

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
<th scope="row"> title </th>
<td> Titre du quiz. </td>
<td> str </td>
<td> '' </td>
</tr>

<tr>
<th scope="row"> intro </th>
<td> Texte d'introduction du quiz. </td>
<td> str </td>
<td> '' </td>
</tr>

<tr>
<th scope="row"> quiz </th>
<td> Questions du quiz au format AMC-TXT. </td>
<td> str </td>
<td> '' </td>
</tr>

</tbody>
</table>

## Exemples

### Exemple 1

```
extends = /model/quiz/AMC.pl

intro ==
Ce quiz est composé de 3 questions.
==

quiz ==
* Quelle est la capitale du Cameroun ?
+ Yaoundé
- Douala
- Kribi

** Parmi les nombres suivants,
lesquels sont positifs ?
+ 2
- -2
+ 10

*[ordered] Combien font
un plus un ?
- 0
- 1
+ 2
==
```
```
