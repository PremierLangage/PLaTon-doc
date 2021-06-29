# Réponse textuelle avec suggestions

Le modèle `basic/inputselect` permet de fabriquer des exercices avec un champ de réponse textuel.

![](inputselect.png)

Les clés de base de ce modèle sont :

  * `question` : l'énoncé de l'exercice ;
  * `items` : la liste des suggestions ;
  * `sol` : la bonne réponse.


```
extends = /model/basic/inputselect.pl

question ==
Quel pays a pour capitale Paris ?
==

sol ==
France
==

items ==
Allemagne
Autriche
Belgique
Danemark
Espagne
Finlande
France
Grèce
Hongrie
Irlande
Italie
Norvège
Pays-Bas
Pologne
Portugal
Roumanie
Royaume-Uni
Slovaquie
Suède
Suisse
==
```
