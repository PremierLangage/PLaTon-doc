# Syntaxe PL

Il y a trois types d'opérations possibles dans la syntaxe PL :

  * affecter une valeur à une clé ;
  * inclure un fichier externe dans l'environnement de l'exercice ;
  * hériter du contenu d'un fichier PL.

## Affecter une valeur à une clé

### Cas général

Le principal opérateur d'affectation dans la syntaxe PL est l'opérateur `=`. Il permet d'affecter une valeur `value` à une clé `key` de la façon suivante.

```
key = value
```

Les types de valeurs autorisés sont les types du [format JSON](https://fr.wikipedia.org/wiki/JavaScript_Object_Notation) :

  * chaîne de caractères ;
  * nombre ;
  * booléen ;
  * vide ;
  * tableau ;
  * objet (dictionnaire).

Les chaînes de caractères sont représentées entre doubles guillements droits (") et peuvent contenir n'importe quel caractère Unicode, sauf le double guillemet droit et la barre oblique inversée (\\) qui doivent être précédés d'une barre oblique inversée. La barre oblique inversée sert également à représenter certains caractères de contrôle comme le retour à la ligne. Une façon plus commode de définir des chaînes multilignes est décrite plus bas.

```
mystring1 = "Titre de l'exercice"

mystring2 = "Πλάτων"

mystring3 = "Les verbes \"détester\" et \"abhorrer\" sont synonymes."

mystring4 = "Ligne 1\nLigne 2"
```

Les nombres peuvent être sous forme entière, décimale ou scientifique. Le séparateur décimal est le point.

```
mynumber1 = 6

mynumber2 = 17.89

mynumber3 = 1.5e6
```
Les valeurs booléennes sont `true` et `false` (sans majuscule). La valeur vide est `null`.

```
mybool = false

myvar = null
```
Les tableaux sont représentés entre crochets.
```
myarray = [4, -1, 0.5, 1]

```  

Attention ! Pas d'affectation sur plusieurs lignes.

```
myobject =  {"firstName": "Victor", "lastName": "Hugo"}
```  

```
myobject.firstName = "Victor"

myobject.lastName = "Hugo"
```

### Chaînes multilignes

Pour faciliter la saisie de chaînes multilignes, qui sont courantes dans les exercices (scripts Python, texte des énoncés, etc.),  la syntaxe PL dispose de l'opérateur `==`.

```
mystring ==
Ligne 1
Ligne 2
Ligne 3
==
```


### Composants

```
mycomponent1 % {"cid": "myid1", "selector": "c-input"}

mycomponent2 % {"cid": "myid2", "selector": "c-radio-group"}
```

```
mycomponent1 =: Input

mycomponent2 =: RadioGroup
```

## Inclure un fichier externe

En plus des clés, il est parfois nécessaire d'ajouter des fichiers à un exercice
  (pour l'évaluation par exemple), ou un exercice à une feuille d'exercice,
  nous utilisons pour cela l'opérateur `@`. La syntaxe correcte est donc
  `@ chemin/vers/fichier.txt [alias]`, l'alias étant optionnel.
  
## Hériter du contenu d'un fichier PL

```
extends = file.pl
```
