# Réponse textuelle

Le modèle `basic/input` permet de fabriquer des exercices avec un champ de réponse textuel.

Les clés de base de ce modèle sont :

  * `question` : l'énoncé de l'exercice ;
  * `sol` : la liste des réponses acceptées.

Par défaut, on ne tient pas compte des minuscules et des majuscules pour comparer la réponse de l'élève aux réponses acceptées.

**Exemple 1** Dans cet exemple, les solutions acceptées sont `Victor Hugo`, `Hugo`, mais aussi `victor hugo`, `victor Hugo`, `HUGO`, etc.

```
extends = /model/basic/input.pl

question ==
Qui a écrit *Les Misérables* ?
==

sol ==
Victor Hugo
Hugo
==
```
