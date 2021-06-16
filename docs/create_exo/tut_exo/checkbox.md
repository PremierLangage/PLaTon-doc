# Question à choix multiple (2)

Sur le même principe que le modèle `basic/radio`,  le modèle `basic/checkbox` permet de fabriquer une question à choix multiple avec plusieurs propositions sélectionnables.

Les clés de base de ce modèles sont :

  * `question` : l'énoncé de l'exercice ;
  * `items` : la liste des propositions ;
  * `indsol` : la liste des indices des bonnes réponses.

Par défaut, les propositions sont mélangées lors de la construction de l'exercice.

**Exemple 1**

```
extends = /model/basic/checkbox.pl

question ==
Parmi ces villes, lesquelles ne sont pas des capitales ?
==

items ==
Barcelone
Milan
Paris
Berlin
==

indsol = [0, 1]
```
