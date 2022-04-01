# Documentations techniques spécifiques

Les documentations suivantes sont plus complètes et plus techniques. Certaines sont générales, 
d'autres sont plus spécifiques. 

## Fonctionnement de PL

* TODO : Stratégie générale de la mise en situation (description globale de playexo avec schéma...)
* [Le langage des ressources PL](langage_pl.md)
* [Affichage et Formulaires](affichage.md)
* [La construction des ressources (builder)](construction.md)
* [Évaluation et notation (grader)](evaluation.md)
* [Paramètres dans les ressources](pl_settings.md)
* [Ecrire une Feuille d'Exercices](pltp.md) (assemblage d'un ou plusieurs exercices)
* [Tester un exercice](pl_testing.md) (Créer des tests automatiques pour vos exercices)

## Template généraux

* [Qu'est ce qu'un template](template_index.md)
* [le builder `before`](before.md) permettant d'exécuter un petit script Python durant la 
  fabrication de la ressource.
* [le builder `build`](build.md) permettant d'exécuter une fonction Python qui pourra modifier
  le contexte de l'exercice.
* [le grader `evalfunc`](evalfunc.md) pour corriger un exercice en un appel à une seule 
  fonction Python.
* [le grader `evaluator`](evaluator.md) pour corriger un exercice à l'aide d'un petit
  script embarqué dans l'exercice.
* Écrire un nouveau grader (TODO : branchement et relecture)
* Formulaires dans les exercices (TODO : branchement et relecture)

## Coté informatique

* [Le template java](template_java.md)
* [Le grader java](grader_java.md)
* [Le grader doctest python](../models/pltest.md) Exercice de programmation en Python avec doctests
* Le tempate pour les [exercices de programmation standard en C](std_progC.md) (verison 07/2020)


## Python

[Documentation Bibliothèque Standard](https://docs.python.org/3/library/)
[Liste des modules Python disponibles](modules_sandbox.md)

### SymPy

[Documentation SymPy](https://docs.sympy.org/latest/index.html)

## Jinja

[Documentation Jinja](https://jinja.palletsprojects.com/)

## JSXGraph

[Documentation JSXGraph](https://jsxgraph.uni-bayreuth.de/wp/docs/index.html)


