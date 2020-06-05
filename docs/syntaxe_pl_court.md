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

  * *string* : chaîne de caractères ;
  * *number* : nombre entier ou flottant ;
  * true, false, null ;
  * *array* : tableau ;
  * *object* : dictionnaire qui associe des valeurs à des clés (propriétés).

!!! note
Le format JSON est un format d'échange de données assez répandu. Comme son nom l'indique, il dérive du langage JavaScript.

### Opérateur `=`

Le principal opérateur d'affectation dans la syntaxe PL est l'opérateur `=`. Il permet d'affecter une valeur `value` de type JSON à une clé `key` en utilisant la syntaxe du format JSON.

```
key = value
```

Les chaînes de caractères sont représentées entre doubles guillements droits (").

```
mystring = "Titre de l'exercice"

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

Attention ! La syntaxe PL ne permet pas (encore ?) l'affectation d'un tableau séparé sur plusieurs lignes.


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

### Opérateur `==`

Pour faciliter la saisie de chaînes multilignes contenant des guillements droits ou des barres obliques inversées, la syntaxe PL dispose de l'opérateur `==`.

```
mystring ==
Ligne 1
Ligne 2
Ligne 3
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
