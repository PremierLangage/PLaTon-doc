# Syntaxe PL

La syntaxe PL est la syntaxe employée pour décrire un exercice dans un fichier PL. Il n'y a que trois types d'opérations possibles dans cette syntaxe :

  * affecter une valeur à une clé ;
  * inclure un fichier externe dans l'environnement de l'exercice ;
  * hériter du contenu d'un fichier PL.
  
 Des lignes de commentaires peuvent être insérées en utilisant un croisillon (#) comme caractère initial.
 
```
# Ceci est un commentaire.
```

## Affecter une valeur à une clé

Les types de valeur qu'une clé peut prendre sont les types du [format JSON](https://fr.wikipedia.org/wiki/JavaScript_Object_Notation) (JavaScript Object Notation) : 

  * *string* (chaîne de caractères) ;
  * *number* (nombre entier ou flottant) ;
  * `true`, `false`, `null`;
  * *array* (tableau) ;
  * *object* (dictionnaire qui associe des valeurs à des clés, aussi appelées propriétés).

!!! note
  Le format JSON est un format d'échange de données assez répandu. Comme son nom l'indique, il dérive du langage JavaScript.

### Opérateur `=`

Le principal opérateur d'affectation dans la syntaxe PL est l'opérateur `=`. Il permet d'affecter une valeur `value` de type JSON à une clé `key` en utilisant la syntaxe du format JSON.

```
key = value
```

Les chaînes de caractères doivent être représentées entre doubles guillements droits ("). Attention, les doubles guillemets ne peuvent pas être remplacés par des guillements simples comme dans d'autres langages. Les chaînes peuvent contenir n'importe quel caractère Unicode sauf le double guillemet droit et la barre oblique inversée (\\). Ces deux caractères ainsi que les caractères de contrôle (nouvelle ligne, tabulation, etc.) sont représentés par des séquences d'échappement.

```
mystring1 = "Titre de l'exercice"

mystring2 = "Πλάτων"

mystring3 = "Les verbes \"détester\" et \"abhorrer\" sont synonymes."

mystring4 = "Ligne 1\nLigne 2"
```

Les nombres peuvent être représentés sous forme entière, décimale ou scientifique.

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
Les tableaux sont représentés entre crochets. Les éléments peuvent être de n'importe quel type et de type différent au sein d'un même tableau.

```
myarray1 = [4, -1, 0.5, 1]

myarray2 = [[0, "A"], [1, "B"], [2, "C"]]
```

Les objets sont des dictionnaires qui associent des valeurs à des propriétés. Les propriétés sont nécessairement des chaînes de caractères. Les valeurs peuvent être de n'importe quel type.

```
myobject =  {"firstname": "Victor", "lastname": "Hugo", "born": 1802, "dead": 1885}
```

Il est possible de définir un objet propriété par propriété ou de façon mixte. Par exemple les définitions ci-dessous sont équivalentes à la définition précédente.

```
myobject.firstname = "Victor"
myobject.lastname = "Hugo"
myobject.born = 1802
myobject.dead = 1885
```

```
myobject =  {"firstname": "Victor", "lastname": "Hugo"}
myobject.born = 1802
myobject.dead = 1885
```

warning !!!
  La syntaxe PL ne permet pas (encore ?) l'affectation d'un tableau ou d'un objet séparé sur plusieurs lignes.
  
### Opérateur `==`

L'opérateur `==` permet de saisir des chaînes multilignes brutes (sans séquence d'échappement). Par exemple, les affectations ci-dessous, faites respectivement avec les opérateurs `=` et `==`, sont équivalentes. 

```
mystring3 = "Les verbes \"détester\" et \"abhorrer\" sont synonymes."

mystring4 = "Ligne 1\nLigne 2"
```

```
mystring3 ==
Les verbes "détester" et "abhorrer" sont synonymes.
==

mystring4 ==
Ligne 1
Ligne 2
==
```

L'opérateur `==` est particulièrement utile pour entrer des scripts Python, des textes au format Markdown, du code HTML, etc.

```
before ==
import random as rd
lst = ["A", "B", "C"]
c = rd.choice(lst)
==
```

## Inclure un fichier externe

L'inclusion d'un fichier externe se fait gâce à l'opérateur `@`. La référence au fichier se fait par son chemin absolu ou son chemin relatif (à la localisation du fichier PL).

~~~
@ dirA/dirB/myfile.py
~~~

Le nom du fichier peut-être remplacé par un alias au moment de l'inclusion.

~~~
@ dirA/dirB/myfile.py [thisfile]
~~~
  
## Hériter du contenu d'un fichier PL

La commande `extends` permet d'hériter du contenu d'un fichier PL, c'est-à-dire ses clés et ses fichiers externes.


```
@ file1.pl

key1 = value1

key2 = value2
```

```
extends = file.pl

key3 = value3
```
