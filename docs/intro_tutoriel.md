# Introduction

Un exercice est défini en choisissant un **builder** et un **grader** et en affectant des valeurs à un ensemble de **clés**. En pratique, ces données sont écrites dans un fichier texte, d'extension `.pl`, selon une syntaxe dédiée.

Lorsque l'exercice est lancé sur la plateforme, le **builder** construit la page web de l'exercice (énoncé, champs de réponse) à partir des valeurs contenues dans les **clés**. Après que l'élève a validé sa réponse, le **grader** évalue cette réponse et modifie la page web de l'exercice (retour sur la réponse).

Plusieurs builders et graders sont disponibles. Dans ce tutoriel, on se limite au builder `before` (qui permet de produire les données de l'exercice avec un script Python) et au grader `evaluator` (qui permet de produire les données de l'exercice avec un script Python).

Pour faciliter la gestion de la partie web de l'exercice, en particulier la gestion des champs de réponse, la plateforme dispose d'une bibliothèque de **composants**.


