# Modèle `basic/dragdrop`

Le modèle `basic/dragdrop.pl` permet de fabriquer des exercices avec des étiquettes à placer.

Le placement des étiquettes et des zones de dépôt dans l'énoncé se fait par un système de balises.

## Clés du modèle

* `sol` (chaîne multilignes). Valeurs attendues dans les zones de dépôt.
    * Cette clé contient les valeurs des solutions attendues dans les zones de dépôt (chaque ligne correspondant à une valeur).
    * Pour chacune de ces valeurs, une zone de dépôt est créée. Ces zones sont numérotées en partant de zéro.
* `labval` (chaîne multilignes). Valeur des étiquettes.
    * Cette clé contient les valeurs des étiquettes (chaque ligne correspondant à une valeur).
    * Pour chacune de ces valeurs, une étiquette est créée. Ces étiquettes sont numérotées en partant de zéro.
    * Pour chaque valeur de `sol` non contenue dans `labval`, une étiquette est également créée (en poursuivant la numérotation).
* `text` (chaîne). Enoncé de l'exercice.
* `form` (chaîne). Zone de réponse de l'exercice.
    * Les codes HTML correspondant aux zones de dépôt et aux étiquettes se trouvent respectivement dans les listes `drops` et `labels`.
    * Pour insérer la i-ème zone de dépôt, il suffit donc d'utiliser la balise `{{ drops[i] }}`.
    * Il est également possible d'utiliser des boucles.
* `shuffled` (booléen). 
    * Si `shuffled` vaut `true`, la liste des étiquettes est mélangée. Sinon, elle est laissée dans l'ordre entré dans la clé `labval` (et la clé `sol`).
    * Par défaut, `shuffled` vaut `false`.

## Exemples

```
title = Homophones : ces ou c'est

text ==
Compléter les phrases suivantes avec les étiquettes proposées.
==

form ==
<ul>
<li> Je voudrais {{ drops[0] }} chausures pour mon anniversaire. </li>
<li> Tu est toujours en retard, {{ drops[1] }} agaçant ! </li>
<li> Je n'aime pas {{ drops[2] }} méthodes. </li>
</ul>

{{ labels[0] }} {{ labels[1] }}
==

sol ==
ces
c'est
ces
==
```
