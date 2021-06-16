# Syntaxe PL

La syntaxe PL est la syntaxe employée pour décrire un exercice dans un fichier PL. Il n'y a que trois types d'opérations possibles dans cette syntaxe :

  * affecter une valeur à une clé ;
  * charger un fichier dans l'environnement ;
  * hériter du contenu d'un fichier PL.
  
 Des lignes de commentaires peuvent être insérées en utilisant un croisillon (#) comme caractère initial.
 
```
# Ceci est un commentaire.
```

## Affecter une valeur à une clé

Les types de valeur qu'une clé peut prendre sont les types de base de Python :

  * chaînes de caractères ;
  * nombres entiers ;
  * nombres flottants ;
  * booléens ;
  * `None` ;
  * listes ;
  * dictionnaires.

### Opérateur `=`

Le principal opérateur d'affectation dans la syntaxe PL est l'opérateur `=`. Il permet d'affecter à une clé une valeur des types cités plus haut.

```
mystring1 = "Titre de l'exercice"

mystring2 = "Πλάτων"

mynint = 6

myfloat = 17.89

mybool = False

myvar = None

mylist1 = [4, -1, 0.5, 1]

mylist2 = [[0, "A"], [1, "B"], [2, "C"]]

mydict =  {"firstname": "Victor", "lastname": "Hugo", "born": 1802, "dead": 1885}
```

Il est possible de définir un dictionnaire propriété par propriété ou de façon mixte. Par exemple les définitions ci-dessous sont équivalentes à la définition précédente de `mydict`.

```
mydict.firstname = "Victor"
mydict.lastname = "Hugo"
mydict.born = 1802
mydict.dead = 1885
```

```
mydict = {"firstname": "Victor", "lastname": "Hugo"}
mydict.born = 1802
mydict.dead = 1885
```

!!! warning
    La syntaxe PL ne permet pas encore l'affectation d'une liste ou d'un dictionnaire sur plusieurs lignes.
  
### Opérateur `==`

L'opérateur `==` permet de saisir des chaînes multilignes brutes (sans séquence d'échappement). Par exemple, les affectations ci-dessous, faites respectivement avec les opérateurs `=` et `==`, sont équivalentes. 

```
mystring ==
Ligne 1
Ligne 2
==
```

L'opérateur `==` est particulièrement utile pour entrer des textes, des scripts Python, des blocs HTML, etc.

```
myscript ==
import random as rd
lst = ["A", "B", "C"]
c = rd.choice(lst)
==
```

## Charger un fichier dans l'environnement

Le chargement un fichier dans l'environnement se fait gâce à l'opérateur `@`. On fait référence au fichier par son chemin absolu ou par son chemin relatif.

~~~
@ dirA/dirB/myfile.py
~~~

Le nom du fichier peut-être remplacé par un alias au moment du chargement.

~~~
@ dirA/dirB/myfile.py [thisfile]
~~~


## Images et sons 

Les images et sons n'ont pas besoin d'être dans l'environnement de l'exercice sur la sandbox. 
Il suffit qu'il soit accesssible par http. 

Deux possibilités:
- le média est accessible à l'extérieur sur un serveur pérenne indiquer directement l'url dans votre lien markdown 
: ! [ alt-text ] (url)

- Vous souhaitez que le média soit sur platon: vous devez le "drag&drop" dans l'arborescence de fichiers. 
En suite vous devez le "charger" dans votre exercice avec la syntaxe :

~~~
$ cheminsurplatondufichier
~~~


## Hériter d'un fichier PL

~~~
extends= nomdefichier.pl 
~~~

Charge toute les clefs de l'exercice indiqué 'nomdefichier.pl' préalablement aux valeur du fichier courant et ce de façon récursive.


