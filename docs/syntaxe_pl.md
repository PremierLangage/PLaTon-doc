# Syntaxe PL

Il y a trois types d'opérations possibles dans la syntaxe PL :

  * affecter une valeur à une clé ;
  * inclure un fichier externe dans l'environnement de l'exercice ;
  * hériter du contenu d'un fichier PL.

## Affecter une valeur à une clé

### Affectation simple

Le principal opérateur d'affectation dans la syntaxe PL est l'opérateur `=`. Il permet d'affecter une valeur `value` à une clé `key` de la façon suivante.

```
key = value
```

Les types de valeurs autorisés sont les types du [format JSON](https://fr.wikipedia.org/wiki/JavaScript_Object_Notation) :

  * chaîne de caractères ;
  * nombre ;
  * booléen ;
  * tableau ;
  * objet (dictionnaire).

Les chaînes de caractères sont représentées entre doubles guillements droits et peuvent contenir n'importe quel caractère Unicode. La barre oblique inversée (\\) sert d'échappement pour représenter certains caractères (double guillement, retour à la ligne, etc.).

```
mystring1 = "Titre de l'exercice"

mystring2 = "Πλάτων"

mystring3 = "Ligne 1\nLigne 2"
```

Les nombres peuvent être sous forme entière, décimale ou scientifique. Le séparateur décimal est le point.

```
mynumber1 = 6

mynumber2 = 17.89

mynumber3 = 1.5e6
```
Les valeurs booléennes sont `true` et `false` (sans majuscule).

```
mybool = false
```
Les tableaux sont représentés entre crochets.
```
myarray = [4, -1, 0.5, 1]

myobject =  {"firstName": "Victor", "lastName": "Hugo"}
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



Souvent, la valeur à affecter à une clé est une chaîne multilignes avec des caractères spéciaux : script Python, code HTML, template de code HTML, etc. La syntaxe PL dispose d'un opérateur `==` ce type d'affectation.

```
key ==

==
```

### Composants

Les composants



## Inclure un fichier externe

En plus des clés, il est parfois nécessaire d'ajouter des fichiers à un exercice
  (pour l'évaluation par exemple), ou un exercice à une feuille d'exercice,
  nous utilisons pour cela l'opérateur `@`. La syntaxe correcte est donc
  `@ chemin/vers/fichier.txt [alias]`, l'alias étant optionnel.
  
## Hériter du contenu d'un fichier PL
