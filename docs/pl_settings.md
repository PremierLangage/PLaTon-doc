# Paramètres d'un Exercice

Les exercices utilisent un espace de nom `settings` (voir
[espaces de noms](../langage_pl/#espaces-de-noms)) pour définir ou modifier
certains paramètres, comme par exemple:

```
settings.oneshot = true
settings.allow_reroll = true
```
___



## Paramètrage de la graine de randomisation

Lorsqu'un élève lance un exercice pour la première fois, une *graine* lui est
attribuée. Cette graine conditionne les tirages aléatoires utilisés pour
produire la version randomisée de l'exercice proposée à l'élève.
Par défaut ce tirage est définitif et la graine ne changera jamais.
Il est cependant possible de modifier ce comportement grâce aux paramètres suivants.

#### À chaque essai

Pour qu'une nouvelle graine soit tirée après chaque essai de l'élève, il faut
définir le paramètres `settings.oneshot = true`. Une nouvelle graine sera alors
tirée à chaque fois que l'élève aura un score inférieur à 100.

Il est possible de modifier ce seuil avec
`settings.oneshot_threshold = [-1, 100]`.

Par exemple, avec:
```
settings.oneshot = true
settings.oneshot_threshold = 50
```
une nouvelle graine sera tirée tant que l'élève aura un score inférieur à 50.


#### Après une réussite

Par défaut, une fois que l'élève a réussit un exercice (score égal à 100 par défaut),
la graine est fixée (même si `settings.oneshot` est activé). Il est alors
possible d'autoriser l'élève à tirer une nouvelle graine (pour s'entrainer par
exemple). Il faut pour cela définir le paramètre `settings.allow_reroll = true`.

Il est possible de modifier le score à partir duquel le bouton apparait
(100 par défaut) grâce à `settings.reroll_threshold = [-1, 100]`.

Par exemple, avec:
```
settings.allow_reroll = true
settings.reroll_threshold = 75
```
le bouton permettant d'effectuer un nouveau tirage aléatoire apparaitra
si l'élève obtient un score d'au moins 75.

***NOTE*** : Le bouton pour effectuer un nouveau tirage n'apparait pas dans
l'éditeur, mais seulement dans le cadre d'une activité.
