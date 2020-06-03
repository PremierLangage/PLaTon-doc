# Structure de base d'un exercice

~~~
@ /builder/before.py [builder.py]

@ /grader/evaluator.py [grader.py]
~~~

~~~
before ==

# Script Python de génération des données

==

title = "Titre de l'exercice"

text ==

Texte de l'énoncé

==

form ==

Interface de réponse

==
~~~

~~~
evaluator ==

# Script Python d'évaluation de la réponse

==
~~~
