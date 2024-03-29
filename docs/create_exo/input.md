# Réponse textuelle

Le modèle `basic/textinput` permet de fabriquer des exercices avec un champ de réponse textuel.

Les clés de base de ce modèle sont :

  * `question` : l'énoncé de l'exercice ;
  * `sol` : la liste des réponses acceptées.

Par défaut, l'évaluation de la réponse ne tient pas compte des minuscules et des majuscules. Pour en tenir compte, la clé `casesens` doit être mise à `True`.

**Exemple 1.** Dans cet exemple, les solutions acceptées sont `Victor Hugo`, `Hugo`, mais aussi `victor hugo`, `victor Hugo`, `HUGO`, etc.

```
extends = /model/basic/textinput.pl

question ==
Qui a écrit *Les Misérables* ?
==

sol ==
Victor Hugo
Hugo
==
```

La clé `tol`, qui prend un entier positif, permet de définir une tolérance pour les réponses approximatives. Si la réponse et la solution sont égales à `tol` ajouts/suppressions/remplaçements de caractère près, la réponse est acceptée.

**Exemple 2.** Dans cet exemple, les réponses acceptées sont les chaînes égales à `Oxygène` à un ajout/suppression/remplaçement de caractère près : `oxygènes`, `oxgène`, `oxigène`, etc.

~~~
extends = /model/basic/textinput.pl

question ==
Quel élément chimique a pour symbole **O** ?
==

sol ==
Oxygène
==

tol = 1
~~~
