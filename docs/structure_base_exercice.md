# Structure de base d'un exercice

Maintenant que nous avons vu le principe de fonctionnement d'un exercice ainsi que les bases de la syntaxe PL, nous pouvons décrire la structure de base du code source d'un exercice.

Il faut tout d'abord déclarer que nous allons utiliser le builder *before* et le grader *evaluator*. Pour cela, il faut inclure dans l'environnement de l'exercice les fichiers `before.py` et `evaluator.py` en leur donnant les alias `builder.py` et `grader.py`.

~~~
@ /builder/before.py [builder.py]

@ /grader/evaluator.py [grader.py]
~~~

Si l'on veut faire un exercice à données aléatoires, il faut définir dans la clé `before` un script Python qui génère ces données.

~~~
before ==

# Script Python de génération des données

==
~~~

Pour décrire l'apparence de l'exercice (titre, énoncé, interface de réponse), il faut ensuite renseigner les clés `title`, `text` et `form`.
~~~
title = "Titre de l'exercice"

text ==

Texte de l'énoncé

==

form ==

Interface de réponse

==
~~~

Enfin, il faut définir dans la clé `evaluator` un script Python qui évalue la réponse et, éventuellement, génère une rétroaction corrective.
~~~
evaluator ==

# Script Python d'évaluation de la réponse

==
~~~
