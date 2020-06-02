# Fonctionnement du *builder* `before` et du *grader* `evaluator`


**Quand l'exercice est lancé sur la plateforme.**

1. Les clés du fichier PL sont chargées dans un dictionnaire JSON. Les fichiers externes référencés dans le fichier PL sont inclus dans l'environnement.

2. Le programme nommé `builder.py` dans l'environnement est exécuté.

    a. Le dictionnaire JSON de l'exercice est converti en dictionnaire Python.

    b. Le script Python contenu dans la clé `before` est exécuté avec le dictionnaire de l'exercice comme dictionnaire de variables globales.

    c. Le dictionnaire de l'exercice est mis à jour avec les variables globales créées par le script.

    d. Les clés `text` et `form` du dictionnaire Python de l'exercice sont mises en forme avec le moteur de template Jinja en utilisant le dictionnaire Python de l'exercice comme dictionnaire.

    e. Le dictionnaire de l'exercice est converti en dictionnaire JSON.

3. La plateforme construit la page web de l'exercice à partir des clés `text` et `form` contenues dans le dictionnaire JSON.
