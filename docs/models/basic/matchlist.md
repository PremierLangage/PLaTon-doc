# Modèle `basic/matchlist`

Le modèle `basic/matchlist` permet de fabriquer des exercices de correspondances.

## Clés du modèle

Les clés `title`, `text` et `before` ont leur signification et leur syntaxe usuelles.

* `matches` (chaîne ou liste). Correspondances.
    * Cette clé contient la liste des correspondances sous la forme d'une chaîne multilignes (chaque ligne correspondant à une correspondance, les deux éléments étant distingués par un séparateur défini dans la clé `separator`) ou d'une liste de listes à deux éléments.
    *  ligne correspond à une correspondance. Les deux éléments en correspondance sont séparés par un délimiteur.
* `séparator` (chaîne). Séparateur des éléments d'une correspondance.
    * Par défaut, le séparateur est la virgule (`,`).
* `nbmatches` (entier ou null). 
    * Si la clé `nbitems` contient un entier, la liste à ordonner par l'élève sera un échantillon aléatoire de `nbmatches` items de `sortedlist`. 
    * Si la clé `nbitems` vaut `null`, la liste des correspondances sera égale à `matches`.
    * Par défaut la clé `nbmatches` vaut `null`.
* `scoring` (chaîne). Barème de l'exercice. 
    * `AllOrNothing` : renvoie un score de 100 si toutes les bonnes réponses sont sélectionnées et aucune mauvaise réponse n'est sélectionnée ; renvoie un score de 0 sinon.
    * `RightMinusWrong` : renvoie le nombre de bonnes réponses sélectionnés moins le nombre de mauvaises réponses sélectionnées, le tout divisé par le nombre total de bonnes réponses et ramené entre 0 et 100.
    * Par défaut, le barème est `RightMinusWrong`.

TODO : Une option `strip` ou `skipinitialspace` pour éliminer les espaces superflus dans `matches.
TODO : Revoir les barèmes (Comment compter une source non reliée ? une cible non reliée ? etc.)

## Exemples (avec une liste déclarée explicitement)

#### Capitales

~~~
extends = /model/basic/matchlist.pl

title = Capitales

text ==
Relier chaque pays à sa capitale.
==

matches ==
France,Paris
Italie,Rome
Allemagne,Berlin
Espagne,Madrid
==
~~~

```
extends = /model/basic/matchlist.pl

text ==
Relier chaque pays à sa capitale.
==

separator % ";"

nbmatches % 4

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

## Exemples (avec une liste générée par un script)

```
extends = /model/basic/matchlist.pl

title = Décomposition de nombres

text ==
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
