# Un premier exemple d'exercice

Le premier exemple que nous allons examiner est un exercice très simple d'addition. On demande de calculer la somme de deux entiers tirés aléatoirement (entre 10 et 20). La réponse doit être rentrée dans un champ de réponse numérique libre.

[Tester l'exercice](https://pl.u-pem.fr/filebrowser/demo/10859/)

## Choix du builder et du grader

En pratique, les *builders* et les *graders* sont des scripts Python stockés sur la plateforme. Pour choisir un *builder* et un *grader* particuliers dans un exercice, il faut inclure ces scripts dans l'environnement de l'exercice en les renommant `builder.py` et `grader.py`. Dans le langage propre aux exercices, l'inclusion de fichiers externes se fait grâce à l'opérateur `@`.

Dans cet exercice, nous allons utiliser le *builder* `before` et le *builder* `evaluator` qui sont, on le rappelle, le *builder* et le *grader* génériques.

~~~
@ /builder/before.py [builder.py]
@ /grader/evaluator.py [grader.py]
~~~

## Génération aléatoire des données

Avec le *builder* `before`, on peut définir un script Python qui sera exécuté au lancement de l'exercice et génerera aléatoirement les données de l'exercice. Ce script doit être affecté à la clé `before`. Comme il s'agit d'un texte à plusieurs lignes, l'affectation se fait avec l'opérateur `==`.

Dans notre exercice d'addition, le script de génération des données est très simple. Il consiste à générer aléatoirement deux entiers. On utilise pour cela le module `random` (qui fait partie de la bibliothèque standard de Python).

~~~
before ==
import random as rd
a=rd.randint(10,20)
b=rd.randint(10,20)
==
~~~

## Titre, énoncé, champ de réponse

La page web de l'exercice a trois sections : le titre, l'énoncé, le champ de réponse.


On définit ensuite le titre de l'exercice avec la clé `title`.
~~~
title = Somme d'entiers
~~~

On définit l'énoncé de l'exercice avec la clé `text`. Les variables qui ont été créés par le script `before` sont disponibles et peuvent être incluses en utilisant des doubles accolades.

~~~
text ==
Calculer {{a}} + {{b}}.
==
~~~

~~~
input =: Input
input.type = number

form ==
{{ input | component }}
==
~~~

## Evaluation de la réponse et retour sur la réponse


La clé `evaluator` permet de définir un script Python qui est exécuté après la validation de l'exercice par l'élève. Ce script doit définir une variable `grade` qui contient la note de l'exercice et un feedback. La note doit être comprise entre 0 et 100 ou, pour déclencher un message d'avertissement, être égale à -1. 

On récupère la valeur entrée par l'élève dans le composant `input` grâce à la commande `input.value`. Puisqu'il s'agit d'une chaîne de caractères, on commence par la convertir en un nombre entier, puis on teste ensuite si ce nombre entier est égal à la somme des deux entiers de l'énoncé (). 
  

En fonction du résultat de ce test, on renvoie une note égale à 0 ou 100. Si l'opération de conversion de la réponse de l'élève en un nombre entier échoue, on renvoie un avertissement.

```
evaluator ==
try:
    if int(input.value)==a+b:
        grade=(100,"")
    else:
        grade=(0,"")
except:
    grade=(-1,"Votre réponse n'est pas un nombre entier.")
==
```

!!! warning
    Toutes les variables créées dans le script `before` ne sont pas disponibles dans le script `evaluator`. Seules les variables         de type `dict`, `list`, `tuple`, `string`, `int`, `float`, ainsi que les objets `True`, `False` et `None` sont transférés du script `before` au script `evaluator`. Ces limitations sont dues au protocole de transfert des variables qui utilise un format JSON.

## Fichier source complet de l'exercice
