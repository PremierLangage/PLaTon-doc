# *Builder* `before`

## Fonctionnement

1. Le dictionnaire JSON de l'exercice est converti en dictionnaire Python.

2. Le script contenu dans la clé `before` est exécuté avec le dictionnaire Python de l'exercice comme dictionnaire de variables globales.

3. Le dictionnaire Python de l'exercice est mis à jour avec les variables globales créées par le script.

4. Les clés `text` et `form` du dictionnaire Python de l'exercice sont mises en forme avec le moteur de template Jinja en utilisant le dictionnaire Python de l'exercice comme dictionnaire.

5. Le dictionnaire Python de l'exercice est converti en dictionnaire JSON.

## Clés spécifiques

- before
- title
- text
- form
