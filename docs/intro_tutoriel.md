# Introduction

Un exercice est un dispositif pédagogique élémentaire. Il prescrit une tâche dans un énoncé et offre une interface de réponse. Il est capable d'évaluer la réponse entrée par l'élève et, éventuellement, de fournir une rétroaction corrective.

Dans certains exercices, les données de l'énoncé peuvent être aléatoires. Une version d'un exercice associée à un jeu de données particulier est appelée une instance.

La plateforme peut exécuter un exercice selon diverses configurations pédagogiques : nombre de tentatives, limite de temps, possibilité de demander une nouvelle instance de l'exercice, etc.

Les exercices sont généralement insérés dans des dispositifs pédagogiques plus complexes appelés activités. Dans ce cadre, ils peuvent tout aussi bien servir à de l'apprentissage, de l'entraînement ou de l'évaluation.

D'un point de vue informatique, un exercice est composé des éléments suivants :

  - un ***builder*** : un programme Python qui construit l'énoncé et l'interface de réponse ;
  - un ***grader*** : un programme Python capable d'évaluer la réponse et de fournir la rétroaction corrective ;
  - un ensemble de **clés** au format JSON et un ensemble de **fichier externes**, qui peuvent être utilisés par le *builder* et le *grader*. 
  
Ces éléments sont définis dans un fichier texte, d'extension `.pl`, selon une syntaxe propre (**syntaxe PL**).

Pour faciliter la création de l'interface réponse, la plateforme dispose d'une bibliothèque de **composants web** (champ de réponse numérique ou textuel, champ de réponse à choix multiples, éditeur de code, etc.)

En pratique, on ne programme pas un *builder* et un *grader* différents pour chaque exercice, on utilise des *builders* et des *graders* génériques auxquels on fournit des paramètres et des données à travers les clés et les fichiers externes.

Le builder et le grader de base sont le *builder* `before` et le *grader* `evaluator` Ils délèguent la génération des données de l'exercice et l'évaluation de la réponse de l'élève à des scripts Python définis dans des clés spécifiques.
