On commence par inclure la librairie `sandboxio` (bientôt plus nécessaire ?) et par choisir le `builder` et le `grader.

~~~
@ /utils/sandboxio.py
@ /builder/before.py [builder.py]
@ /grader/evaluator.py [grader.py]
~~~

On définit ensuite le titre de l'exercice avec la clé `title`.
~~~
title = Somme d'entiers
~~~

La clé `before` permet de définir un script Python qui est exécuté au lancement de l'exercice. C'est avec ce script qu'on génère aléatoirement les deux nombres à additionner.

~~~
before ==
import random as rd
a=rd.randint(10,20)
b=rd.randint(10,20)
==
~~~

On définit l'énoncé de l'exercice avec la clé `text`. Les variables qui ont été créés par le script `before` sont disponibles et peuvent être incluses an utilisant des doubles accolades.

~~~
text ==
Calculer {{a}} + {{b}}.
==
~~~

La création du champ de réponse se fait grâce à un composant prédéfini. On crée un composant `Input` de type `text` qu'on appelle `input`. On insère ensuite ce composant dans la clé `form` qui est destinée à recevoir le ou les champs de réponse de l'exercice. L'insertion d'un composant se fait entre doubles accolades avec le filtre `component`. 

~~~
input =: Input
input.type = text

form ==
{{ input | component }}
==
~~~

La clé `evaluator` permet de définir un script Python qui est exécuté après la validation de l'exercice par l'élève. Ce script doit définir une variable `grade` qui contient la note de l'exercice et un feedback. La note doit être comprise entre 0 et 100 ou, pour déclencher un message d'avertissement, être égale à -1. 

On récupère la valeur entrée par l'élève dans le champ de réponse grâce à la commande `input.value`. Puisqu'il s'agit d'une chaîne de caractères, on commence par la convertir en un nombre entier, puis on teste ensuite si ce nombre entier est égal à la somme des deux entiers de l'énoncé (les variables de types standards créées par le script `before` sont disponibles dans le script `evaluator`). En fonction du résultat de ce test, on renvoie une note égale à 0 ou 100. Si l'opération de conversion de la réponse de l'élève en un nombre entier échoue, on renvoie un avertissement.

~~~
evaluator ==
try:
    if int(input.value)==a+b:
        grade=(100,"")
    else:
        grade=(0,"")
except:
    grade=(-1,"Votre réponse n'est pas un nombre entier.")
==
~~~
