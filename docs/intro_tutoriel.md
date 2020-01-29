# Introduction

On crée un exercice en choisissant un **builder** et un **grader**, puis en affectant des valeurs à un ensemble de **clés**. En pratique, ces choix et ces affectations sont écrits dans un fichier texte, d'extension `.pl`, selon une syntaxe dédiée.

Lorsque l'exercice est lancé sur la plateforme, le **builder** construit la page web de l'exercice (énoncé, champs de réponse) à partir des valeurs contenues dans les **clés**. Une fois que l'élève a validé sa réponse, le **grader** évalue cette réponse et modifie la page web de l'exercice (retour sur la réponse).

Pour faciliter la création de la partie web de l'exercice, en particulier la création des champs de réponse, la plateforme dispose d'une bibliothèque de **composants**.

Le builder et le grader génériques sont le builder`before`et le grader `evaluator`. Ils permettent au créateur d'exercice de programmer la génération des données de l'exercice et l'évaluation de la réponse de l'élève par des scripts Python (définis dans des clés spécifiques). Ils peuvent être utilisés avec n'importe quels types de champs de réponse.

L'objectif de ce premier tutoriel est de présenter l'utilisation du builder`before`et du grader `evaluator`. Pour simplifier l'exposé, on se limte à des champs de réponse libres (numériques ou textuels).
