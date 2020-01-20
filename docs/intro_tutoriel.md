# Introduction

Un exercice est défini en choisissant un **builder** et un **grader** et en affectant des valeurs à un ensemble de **clés**.

Lorsque l'exercice est lancé sur la plateforme, le **builder** construit la page web de l'exercice (énoncé, champs de réponse) à partir des valeurs contenues dans les clés. Après que l'élève a validé sa réponse, le **grader** évalue cette réponse et modifie la page web de l'exercice (feedback), toujours en utilisant les valeurs contenues dans les clés.

Les clés peuvent contenir du texte, des valeurs numériques ou des données structurées (liste, dictionnaire).

En pratique, pour chaque exercice, ces données sont écrites dans un fichier texte, d'extension `.pl`, selon une syntaxe dédiée.

## Builders et graders

Plusieurs builders et graders sont disponibles.
- Le builder `before` est le builder de base, qui permet de produire les données de l'exercice avec un script Python.
- Le grader `evaluator` est le grader de base, qui permet de produire les données de l'exercice avec un script Python.
- Le builder `mathbefore` et le grader `mathevaluator` sont des variantes qui incluent automatiquement un certain nombre d'outils mathématiques.

Il est également possible de créer ses propres builders et graders.

## Clés

## Composants
