# Syntaxe PL

Il y a trois types d'opérations possibles dans la syntaxe PL :
    * affecter une valeur à une clé ;
    * inclure un fichier externe dans l'environnement de l'exercice ;
    * hériter du contenu d'un fichier PL.

L'ordre n'a pas d'importance (?).

## Affecter une valeur à une clé

Le principal opérateur d'affectation dans la syntaxe PL est l'opérateur `=`. Il permet d'affecter une valeur `value` à une clé `key` de la façon suivante.

```
key = value
```

Les types de valeurs autorisés sont :
  * chaîne de caractères ;
  * nombres (entier ou flottant) ;
  * booléen ;
  * tableaux ;
  * dictionnaire.

```
key1 = "Mon exercice"

key2 = 6

key3 = 17.89

key4 = false
```  
  
Il s'agit des types autorisés dans le format JSON.

Souvent, la valeur à affecter à une clé est une chaîne multilignes avec des caractères spéciaux : script Python, code HTML, template de code HTML, etc. La syntaxe PL dispose d'un opérateur `==` ce type d'affectation.

```
key ==

==
```

## Inclure un fichier externe

En plus des clés, il est parfois nécessaire d'ajouter des fichiers à un exercice
  (pour l'évaluation par exemple), ou un exercice à une feuille d'exercice,
  nous utilisons pour cela l'opérateur `@`. La syntaxe correcte est donc
  `@ chemin/vers/fichier.txt [alias]`, l'alias étant optionnel.
  
## Hériter du contenu d'un fichier PL
