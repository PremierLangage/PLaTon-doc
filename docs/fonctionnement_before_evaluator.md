# Fonctionnement du *builder* `before` et du *grader* `evaluator`

Un exercice est composé des éléments suivants :

  - un ***builder*** : un programme Python qui construit l'énoncé et l'interface de réponse ;
  - un ***grader*** : un programme Python capable d'évaluer la réponse et de fournir la rétroaction corrective ;
  - un ensemble de **clés** au format JSON et un ensemble de **fichier externes**, qui peuvent être utilisés par le *builder* et le *grader*.
  
## Fonctionnement général d'un exercice

Voilà les opérations effectuées quand un exercice est lancé sur la plateforme.

1. Les clés du fichier PL sont chargées dans un dictionnaire au format JSON. Les fichiers externes référencés dans le fichier PL sont chargés dans l'environnement d'exécution. 

2. Le *builder* est exécuté. Il a accès au dictionnaire JSON de l'exercice et peut le modifier intégralement. Il a également accès aux fichiers externes de l'environnement. A la fin de l'exécution du *builder*, on doit trouver dans le dictionnaire JSON des clés `title`, `text` et `form`, contenant respectivement le titre, l'énoncé et l'interface de réponse au format HTML. 

3. La plateforme construit la page web de l'exercice à partir en insérant le contenu des clés `title`, `text` et `form` dans un modèle prédéfini de page web.

Voilà les opérations effectuées quand l'élève valide sa réponse.

1. Le dictionnaire JSON de l'exercice est mis à jour avec la réponse de l'élève.

2. Le *grader* est exécuté. Il a accès au dictionnaire JSON de l'exercice et peut le modifier intégralement. Il a également accès aux fichiers externes de l'environnement. A la fin de l'exécution du *builder*, on doit trouver dans le dictionnaire JSON une clé `score`, contenant une valeur entière entre 0 et 100 (ou égale à -1 pour indiquer une erreur de syntaxe), et une clé`feedback`, contenant une rétroaction corrective au format HTML. 

3. La plateforme reconstruit la page web de l'exercice à partir en utilisant le contenu des clés `score` et `feedback`.

## Fonctionnement du *builder* `before`

Voilà les différentes actions réalisées par le *builder* `before` lors de son exécution.

1. Le dictionnaire JSON de l'exercice est converti en dictionnaire Python.

2. Le script Python contenu dans la clé `before` est exécuté avec le dictionnaire de l'exercice comme dictionnaire de variables globales.

3. Le dictionnaire de l'exercice est mis à jour avec les variables globales créées par le script.

4. Les clés `title`, `text` et `form` du dictionnaire Python de l'exercice subissent une interprétation Jinja (en utilisant le dictionnaire Python de l'exercice comme contexte), puis une inteprétation Markdown.

5. Le dictionnaire de l'exercice est converti en dictionnaire JSON.

## Fonctionnement du *grader* `evaluator`

Voilà les différentes actions réalisées par le *grader* `evaluaor` lors de son exécution.

1. Le dictionnaire JSON de l'exercice est converti en dictionnaire Python.

2. Le script Python contenu dans la clé `evaluaor` est exécuté avec le dictionnaire de l'exercice comme dictionnaire de variables globales.

3. Le dictionnaire de l'exercice est mis à jour avec les variables globales créées par le script.

4. Le dictionnaire de l'exercice est converti en dictionnaire JSON.
