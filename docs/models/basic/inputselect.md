# Modèle `basic/inputselect`

Le modèle `basic/inputselect` permet de fabriquer des exercices avec un champ de réponse textuel proposant des suggestions (par un système d'autocomplétion).

## Clés du modèle

* `sol` (chaîne). Solution de l'exercice.
    * Chaque ligne correspond à une réponse acceptée. 
* `items` (chaîne ou liste).


## Exemples

```
extends = /model/basic/inputselect.pl

title = Géographie

text ==
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
