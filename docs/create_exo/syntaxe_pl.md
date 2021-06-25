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

L'opérateur `==` permet de saisir des chaînes multilignes brutes (sans échappement).

```
mystring ==
Ligne 1
Ligne 2
==
```

L'opérateur `==` est particulièrement utile pour entrer des textes, des scripts Python, des blocs HTML, etc.

```
myscript ==
lst = []
for k in range(5):
 lst.append(k**2)
==
```

## Charger un fichier dans l'environnement

L'opérateur `@` permet de charger un fichier dans l'environnement de l'exercice. Le fichier peut être désigné par son chemin absolu ou par son chemin relatif.

~~~
@ dirA/dirB/myfile.py
~~~

Le nom du fichier peut-être remplacé par un alias au moment du chargement.

~~~
@ dirA/dirB/myfile.py [thisfile.py]
~~~


## Hériter d'un fichier PL

Hériter d'un fichier PL consiste à importer son contenu (clés, fichiers à charger). C'est avec l'opérateur `extends` qu'on effectue cette opération. Le fichier peut être désigné par son chemin absolu ou par son chemin relatif.

~~~
extends = dirA/dirB/parent.pl 
~~~

Si des clés définies dans le corps du fichier PL ont le même nom que des clés héritées, les premières remplacent les secondes. Il en va de même pour les fichiers à charger.

**Exemple.** L'exercice associé au fichier `myfile.pl` contiendra une clé `key1` valant `0` et une clé `key2` valant `"toto"`.

`parent.pl`
```
key1 = 5

key2 = "toto"
```

`myfile.pl`
```
extends = parent.pl

key1 = 0
```

Il est possible d'hériter en cascade de plusieurs fichiers.
