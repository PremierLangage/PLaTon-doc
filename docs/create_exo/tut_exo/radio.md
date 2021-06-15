# Question à choix multiple

Le modèle qui permet de fabriquer une question à choix multiple est le modèle `basic/radio`. Pour choisir ce modèle dans notre exercice, on commence par écrire la commande suivante.

```
extends = /model/basic/radio.pl
```

Ce modèle nécessite de renseigner au moins deux clés :
    * `question` : l'énoncé de l'exercice ;
    * `items` : la liste des propositions.
    
La liste des propositions dans `items` peut être saisie comme une liste de chaînes ou, ce qui est plus pratique, comme une chaîne multilignes (chaque ligne correspondant à une proposition).

Par défaut, la première proposition est considérée comme la solution et les propositions sont mélangées lors de la construction de l'exercice.

Voilà donc le code source complet d'un 

```
extends = /model/basic/radio.pl

question ==
Quel pays a pour capitale Budapest ?
==

items ==
Hongrie
Estonie
Roumanie
Slovaquie
==
```
