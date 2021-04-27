# Modèle `basic/radio`

Le modèle `basic/radio` permet de fabriquer des exercices à choix multiple (avec un seul item à sélectionner).

## Clés du modèle

Les clés `title`, `text` et `before` ont leur signification et leur syntaxe usuelles.

* `items` (chaîne ou liste). Items de la question
    * Cette clé contient une liste d'items sous la forme d'une chaîne multilignes (chaque ligne correspondant à un choix) ou d'une liste.
* `indsol` (liste). Indice du bon item.
    * L' indice se rapporte à l'ordre des items dans la clé `items`. L'indexation commence à 0.
    * Par défaut `indsol` vaut 0.
* `shuffled` (booléen). Mélange des choix.

## Exemples (avec déclaration explicite des items)
