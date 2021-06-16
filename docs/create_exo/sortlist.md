# Liste à ordonner

Le modèle `basic/sortlist` permet de fabriquer des exercices où il faut ordonner une liste. 

Les clés de base de ce modèle sont :

  * `question` : l'énoncé de l'exercice ;
  * `sortedlist` : la liste ordonnée.

**Exemple 1**

```
extends = model/basic/sortlist.pl

question ==
Classer les mots suivants dans l'ordre alphabétique.
==

sortedlist ==
Abricot
Avion
Ballon
Carotte
Cartable
==
```
