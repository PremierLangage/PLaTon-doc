# Syntaxe PL

Il y a trois types d'opérations possibles dans la syntaxe PL :

  * affecter une valeur à une clé ;
  * inclure un fichier externe dans l'environnement de l'exercice ;
  * hériter du contenu d'un fichier PL.
  
 Des lignes de commentaires peuvent être insérées en utilisant un croisillon (#) comme caractère initial.
 
 ~~~
 # Ceci est un commentaire.
 ~~~

## Affecter une valeur à une clé

### Cas général

Le principal opérateur d'affectation dans la syntaxe PL est l'opérateur `=`. Il permet d'affecter une valeur `value` à une clé `key` de la façon suivante.

```
key = value
```

Les types de valeurs autorisés sont les types du [format JSON](https://fr.wikipedia.org/wiki/JavaScript_Object_Notation) :

  * chaîne de caractères (*string*) ;
  * nombre (*number*) ;
  * true, false, null ;
  * tableau (*array*) ;
  * objet (*object*).

Les chaînes de caractères sont représentées entre doubles guillements droits (") et peuvent contenir n'importe quel caractère Unicode, sauf le double guillemet droit et la barre oblique inversée (\\) qui doivent être précédés d'un caractère d'échappement (la barre oblique inversée). Les caractères de contrôle comme le retour à la ligne sont représentés par des séquences d'échappement.

```
mystring1 = "Titre de l'exercice"

mystring2 = "Πλάτων"

mystring3 = "Les verbes \"détester\" et \"abhorrer\" sont synonymes."

mystring4 = "Ligne 1\nLigne 2"
```
L'opérateur `==`, décrit un peu plus bas, permet d'utiliser des chaînes multilignes brutes (sans échappement).

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

Attention ! La syntaxe PL ne permet pas (encore ?) l'affectation d'un tableau séparé sur plusieurs lignes.


Les objets sont des dictionnaires. Les clés sont nécessairement des chaînes de caractères. Les valeurs peuvent être de n'importe quel type.

```
myobject =  {"firstname": "Victor", "lastname": "Hugo", "born": 1802, "dead": 1885}
```  

```
myobject.firstname = "Victor"

myobject.lastname = "Hugo"
```

### Chaînes multilignes brutes

Pour faciliter la saisie de chaînes multilignes contenant des guillements droits ou des barres obliques inversées, la syntaxe PL dispose de l'opérateur `==`.

```
mystring ==
Ligne 1
Ligne 2
Ligne 3
==
```
L'opérateur `==` est particulièrement utile pour entrer des scripts Python, des textes d'énoncé (en Markdown ou en HTML), etc.

```
before ==
import random as rd
lst = ["A", "B", "C"]
c = rd.choice(lst)
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

L'inclusion d'un fichier exter se fait gâce à l'opérateur `@`.

~~~
@ dirA/dirB/myfile.py
~~~

Le fichier peut-être renommé au moment de l'inclusion.

~~~
@ dirA/dirB/myfile.py [thisfile]
~~~
  
## Hériter du contenu d'un fichier PL

La commande `extends` permet d'hériter du contenu d'un fichier PL, c'est-à-dire ses clés et ses fichiers externes.


```
extends = file.pl
```
