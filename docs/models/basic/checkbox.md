# Modèle `basic/checkbox`

Le modèle `basic/checkbox` permet de fabriquer des exercices à choix multiple (avec plusieurs items à sélectionner).

## Clés du modèle

Les clés `title`, `text` et `before` ont leur signification et leur syntaxe usuelles.

* `items` (chaîne ou liste). Items de la question
    * Cette clé contient une liste de choix sous la forme d'une chaîne multilignes (chaque ligne correspondant à un choix) ou d'une liste.
* `indsol` (liste). Indices des bons items.
    * Les indices se rapportent à l'ordre des items dans la clé `items`. L'indexation commence à 0. 
* `shuffled` (booléen). Mélange des choix.
* `scoring` (chaîne). Barème de l'exercice.
    * `AllOrNothing` : renvoie un score de 100 si toutes les bonnes réponses sont sélectionnées et aucune mauvaise réponse n'est sélectionnée ; renvoie un score de 0 sinon.
    * `RightMinusWrong` : renvoie le nombre de bonnes réponses sélectionnés moins le nombre de mauvaises réponses sélectionnées, le tout divisé par le nombre total de bonnes réponses et ramené entre 0 et 100.
    * Par défaut, le barème est `RightMinusWrong`.

## Exemples (avec déclaration explicite des items)
