# Introduction

Un exercice est un **dispositif pédagogique** élémentaire. Il prescrit une **tâche** et offre une **interface de réponse**. Il est capable d'**évaluer** la réponse entrée par l'élève et de fournir des **informations de correction**. Dans certains exercices, les données de l'énoncé sont **aléatoires**.

La plateforme peut exécuter un exercice selon diverses **configurations pédagogiques** : nombre de tentatives, limite de temps, informations de correction désactivées, etc.

Les exercices sont généralement insérés dans des dispositifs pédagogiques plus complexes appelés **activités**.

D'un point de vue informatique, un exercice est composé des éléments suivants :

  - un ensemble de **clés** au format JSON et un ensemble de **fichier externes**, qui peuvent être utilisés par le *builder* et le *grader*; 
  - un ***builder*** : un programme Python qui construit l'énoncé et l'interface de réponse ;  
  - un ***grader*** : un programme Python capable d'évaluer la réponse et de fournir une rétroaction corrective. 




Ces éléments sont définis ou référencés dans un **fichier PL** (fichier texte dont l'extension est `.pl`) selon une syntaxe propre (**syntaxe PL**).

Pour faciliter la création de l'interface réponse, la plateforme dispose d'une bibliothèque de **composants web** (champ de réponse numérique ou textuel, champ de réponse à choix multiples, éditeur de code, etc.). 

!!! Vive les composants:
    * Ces composants permettent de s'affranchir de tout code html
    * sont composables: plusieurs composant dans un même exercice (hint, crono, editor, input) 


!!! Remarque:
    Pour simplifier l'usage deux **clés** sont proposées **before** et **evaluator** qui sont éxécutées dans les scripts builder et grader.


En pratique, on ne programme pas un *builder* et un *grader* différents pour chaque exercice, on utilise des *builders* et des *graders* génériques auxquels on fournit des paramètres et des données à travers les clés et les fichiers externes.

Le builder et le grader de base sont le *builder* `before` et le *grader* `evaluator` Ils délèguent la génération des données de l'exercice et l'évaluation de la réponse de l'élève à des scripts Python définis dans des clés correspondantes.



