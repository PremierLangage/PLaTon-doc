# Un premier exemple d'exercice

Le premier exemple que nous allons examiner est un exercice très simple d'addition. On demande de calculer la somme de deux entiers tirés aléatoirement (entre 10 et 20). La réponse doit être rentrée dans un champ de réponse numérique libre.

[Tester l'exercice](https://pl.u-pem.fr/filebrowser/demo/10859/)

## Choix du builder et du grader

En pratique, les *builders* et les *graders* sont des scripts Python stockés sur la plateforme. Pour choisir un *builder* et un *grader* particuliers dans un exercice, il faut inclure ces scripts dans l'environnement de l'exercice en les renommant `builder.py` et `grader.py`.

Dans cet exercice, nous allons utiliser le *builder* `before` et le *builder* `evaluator` qui sont, on le rappelle, le *builder* et le *grader* génériques.

~~~
@ /builder/before.py [builder.py]
@ /grader/evaluator.py [grader.py]
~~~

## Génération aléatoire des données

Avec le *builder* `before`, on peut définir un script Python qui sera exécuté au lancement de l'exercice afin de produire les données de l'exercice. Ce script doit être affecté à la clé `before`.

Dans notre exercice d'addition, le script de génération des données est très simple. Il consiste à tirer aléatoirement deux entiers. On utilise pour cela le module `random` (qui fait partie de la bibliothèque standard de Python).

~~~
before ==
import random as rd
a=rd.randint(10,20)
b=rd.randint(10,20)
==
~~~

## Titre, énoncé, champ de réponse

La page web de l'exercice contient trois blocs lors de son premier affichage : le titre, l'énoncé, la zone de réponse. Le contenu de ces trois blocs est à définir dans les clés `title`, `text` et `form`.

La clé `title` doit recevoir une chaîne de caractères.

~~~
title = "Addition"
~~~

La clé `text` doit recevoir une chaîne de caractères ou un *template* de chaîne de caractères. L'utilisation d'un *template* permet de créer facilement un énoncé dynamique. La moteur de template utilisé est Jinja2. L'insertion d'une valeur se fait en tre doubles accolades `{{...}}`.

~~~
text ==
Calculer {{a}} + {{b}}.
==
~~~

Comme la clé `text`, la clé `form` doit recevoir une chaîne de caractères ou un *template* de chaîne de caractères. L'insertion d'un composant se fait entre doubles accolades avec un filtre spécifique `{{ ... | component}}`.

~~~
input =: Input
input.type = number

form ==
{{ input | component }}
==
~~~

## Evaluation de la réponse et retour sur la réponse

Avec le *builder* `evaluator`, il faut définir un script Python qui sera exécuté après la validation de l'exercice par l'élève afin d'évaluer sa réponse. Ce script doit être affecté à la clé `evaluator`. Il doit définir une variable `grade` qui contient la note de l'exercice et un feedback. La note doit être comprise entre 0 et 100 ou, pour déclencher un message d'avertissement, être égale à -1. 

On récupère la valeur entrée par l'élève dans le composant `input` grâce à la commande `input.value`. Puisqu'il s'agit d'une chaîne de caractères, on commence par la convertir en un nombre entier, puis on teste ensuite si ce nombre entier est égal à la somme des deux entiers de l'énoncé (). 

```
evaluator ==
if input.value==a+b:
    grade=(100,"")
else:
    grade=(0,f"La réponse est {a+b}.")
==
```

!!! warning
    Toutes les variables créées dans le script `before` ne sont pas disponibles dans le script `evaluator`. Seules les variables         de type `dict`, `list`, `tuple`, `string`, `int`, `float`, ainsi que les objets `True`, `False` et `None` sont transférés du script `before` au script `evaluator`. Ces limitations sont dues au protocole de transfert des variables qui utilise un format JSON.

## Fichier source complet de l'exercice
