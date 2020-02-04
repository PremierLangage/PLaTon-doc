# Syntaxe PL


## Affectation de valeurs aux clés

* Le principal opérateur d'affectation dans la syntaxe PL est l'opérateur `=`.
```
key = value
```

* L'opérateur `==` permet d'affecter une chaîne de caractères multilignes.
```
key ==
Voici un énoncé d'exercice
qui peut prendre plusieurs lignes.
==
```

## Inclusion de fichiers  externes

En plus des clés, il est parfois nécessaire d'ajouter des fichiers à un exercice
  (pour l'évaluation par exemple), ou un exercice à une feuille d'exercice,
  nous utilisons pour cela l'opérateur `@`. La syntaxe correcte est donc
  `@ chemin/vers/fichier.txt [alias]`, l'alias étant optionnel. Exemple:
