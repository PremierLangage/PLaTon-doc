# Modèle `basic/dragdrop`

Le modèle `basic/dragdrop.pl` permet de fabriquer des exercices avec des étiquettes à glisser-déposer.

Le placement des étiquettes et des zones de dépôt dans l'énoncé se fait par un système de balises.

## Clés du modèle

* `sol` (chaîne multilignes ou liste). Liste des solutions.
    * Cette clé contient les valeurs des solutions attendues dans les zones de dépôt. Elle peut-être déclarée comme une chaîne multilignes (chaque ligne correspondant à une zone de dépôt) ou une liste.* `nbdrops` (entier). Nombre de zones de dépôt pour les étiquettes.
* `contents` (chaîne multilignes ou liste). 
    * Cette clé contient les valeurs des étiquettes. Elle peut-être déclarée comme une chaîne multilignes (chaque ligne correspondant à une étiquette) ou une liste.
* `shuffled` (booléen). Si `shuffle` vaut `true`, la liste des étiquettes est mélangée. Sinon, elle est laissée dans l'ordre entré dans `labelcontents`. Par défaut, `shuffle` vaut `false`.
