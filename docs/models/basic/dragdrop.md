# Modèle `basic/dragdrop`

Le modèle `basic/dragdrop.pl` permet de fabriquer des exercices avec des étiquettes à placer.

Le placement des étiquettes et des zones de dépôt dans l'énoncé se fait par un système de balises.

## Clés du modèle

* `sol` (chaîne multilignes). Valeurs attendues dans les zones de dépôt.
    * Cette clé contient les valeurs des solutions attendues dans les zones de dépôt (chaque ligne correspondant à une zone de dépôt)
* `labval` (chaîne multilignes). Valeur des étiquettes.
    * Cette clé contient les valeurs des étiquettes (chaque ligne correspondant à une étiquette).
    * Les valeurs de `sol` non contenues dans `labval` sont ajoutées automatiquement.
* `shuffled` (booléen). 
    * Si `shuffle` vaut `true`, la liste des étiquettes est mélangée. Sinon, elle est laissée dans l'ordre entré dans `labelcontents`. Par défaut, `shuffle` vaut `false`.

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
