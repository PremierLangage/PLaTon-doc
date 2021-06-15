# Introduction

Un exercice est un **dispositif pédagogique** élémentaire. Il prescrit une **tâche** et offre une **interface de réponse**. Il est capable d'**évaluer** la réponse entrée par l'élève et de fournir des **informations de correction**. Dans certains exercices, les données de l'énoncé sont **aléatoires**.

La plateforme peut exécuter un exercice selon diverses **configurations pédagogiques** : nombre de tentatives, limite de temps, informations de correction désactivées, etc.

Les exercices sont généralement insérés dans des dispositifs pédagogiques plus complexes appelés **activités**.

Pour créer un exercice, il faut d'abord choisir un **modèle** d'exercice parmi ceux proposés par la plateforme. Chaque modèle permet de fabriquer un certain type d'exercice, plus ou moins spécifique.

Il reste ensuite à compléter ce modèle avec un certain nombre d'éléments, propres au modèle choisi. Les modèles les plus simples ne nécessitent que le texte de l'énoncé et la valeur de la solution. Les modèles plus avancés ou plus génériques requièrent en général du code informatique, par exemple des scripts Python (pour la génération des données ou l'évaluation de la réponse) ou des bloc HTML (pour composer l'interface de réponse).

En pratique, un exercice est défini dans un fichier texte dont l'extension est `.pl` (**fichier PL**) selon une syntaxe propre (**syntaxe PL**). Cette syntaxe permet de choisir le modèle d'exercice, puis de définir les éléments nécessaires au fonctionnement du modèle en les affectant dans des **clés**.

#### A reprendre

Pour faciliter la création de l'interface réponse, la plateforme dispose d'une bibliothèque de **composants web** (champ de réponse numérique ou textuel, champ de réponse à choix multiples, éditeur de code, etc.). 

!!! Vive les composants:
    * Ces composants permettent de s'affranchir de tout code html
    * sont composables: plusieurs composant dans un même exercice (hint, crono, editor, input) 


!!! Remarque:
    Pour simplifier l'usage deux **clés** sont proposées **before** et **evaluator** qui sont éxécutées dans les scripts builder et grader.


En pratique, on ne programme pas un *builder* et un *grader* différents pour chaque exercice, on utilise des *builders* et des *graders* génériques auxquels on fournit des paramètres et des données à travers les clés et les fichiers externes.

Le builder et le grader de base sont le *builder* `before` et le *grader* `evaluator` Ils délèguent la génération des données de l'exercice et l'évaluation de la réponse de l'élève à des scripts Python définis dans des clés correspondantes.



