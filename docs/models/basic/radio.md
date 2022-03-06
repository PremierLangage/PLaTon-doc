# Modèle `basic/radio`

Le modèle `basic/radio` permet de fabriquer des exercices à choix multiple (avec un seul item à sélectionner).

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
      <th scope="row"> items </th>
      <td> Liste des items. Elle peut être saisie comme une liste ou comme une chaîne multilignes (chaque ligne correspondant à un item). </td>
      <td> (str, list) </td>
      <td>  </td>
    </tr>
    <tr>
      <th scope="row"> indsol </th>
      <td> Indice de la solution dans la liste des items (la numérotation commence à 0). </td>
      <td> int </td>
      <td> 0 </td>
    </tr>
    <tr>
      <th scope="row"> shuffled </th>
      <td> Valeur indiquant si les items seront mélangés. </td>
      <td> bool </td>
      <td> True </td>
    </tr>
  </tbody>
</table>

## Exemples

**Exemple 1**

```
extends = /model/basic/radio.pl

question ==
Quel pays a pour capitale Paris ?
==

items ==
France
Allemagne
Italie
Espagne
==
```

**Exemple 2**

```
extends = /model/basic/radio.pl

question ==
À quel siècle vivait Victor Hugo ?
==

items ==
XVIIe siècle
XVIIIe siècle
XIXe siècle
XXe siècle
==

shuffled = False

indsol = 2
```
