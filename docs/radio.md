# Question à choix multiples (avec une seule bonne réponse)

Le composant `RadioGroup` permet de créer un champ de réponse à choix multiples (avec une seule bonne réponse).

La création du composant et son insertion dans la clé `form` se fait comme n'importe quel autre composant.

~~~
radio =: RadioGroup

form ==
{{ radio | component }}
==
~~~

La définition du contenu et l'évaluation de ce champ de réponse se fait facilement grâce à des méthodes spécifiques.
  * Dans le script `before` :
    * Les différents choix possibles sont définis en fournissant une liste de chaînes de caractères à la méthode `loadContent`.
    * La bonne réponse est fixée grâce de la méthode `setSolByContent` (en donnant la valeur de la bonne réponse) ou à la méthode `setSolByIndex` (en donnant son indice).
    * Enfin, la liste des choix est mélangée, si nécessaire, en utilisant la méthode`shuffle`.
  * Dans le script `evaluator`, l'évaluation de la réponse de l'élève se fait avec la méthode `eval`.
  
Le template `radio.pl` permet d'alléger l'écriture d'exercices utilisant un champ de réponse à choix multiples en prédéfinissant certains éléments.

## Exemple 1 : Plus petit nombre

[Tester l'exercice](https://pl.u-pem.fr/filebrowser/demo/6898/)

On commence par créer un composant `RadioGroup`.

~~~
radio =: RadioGroup
~~~

On tire une liste de 5 nombres au hasard entre 0 et 49. Avec la méthode `loadContent`, on charge cette liste de choix dans le composant. On détermine le plus petit de ces 5 nombres et on indique qu'il s'agit de la solution en utilisant la méthode `setSolByContent`.

~~~
before ==
import random as rd
numbers=rd.sample(list(range(50)),5)
radio.loadContent([str(item) for item in numbers])
sol = min(numbers)
radio.setSolByContent(str(sol))
==
~~~

~~~
text ==
Sélectionner le plus petit nombre.
==

form ==
{{ radio | component }}
==
~~~

La réponse de l'élève est évaluée grâce à la méthode `eval` du composant. Celle-ci renvoie `(100,"")` si la réponse de l'élève est correcte et `(0,"")` sinon. Par ailleurs, cette méthode modifie l'apparence du champ de réponse : la solution est colorée en vert et l'éventuelle mauvaise réponse de l'élève est colorée en rouge. Enfin, le composant est désactivé en mettant à `True` la valeur de l'attribut `disabled` : l'élève ne peut plus l'item sélectionné.

~~~
evaluator ==
grade = radio.eval()
radio.disabled=True
==
~~~

## Template `radio.pl`

Pour alléger l'écriture d'exercices à choix multiples, on peut utiliser le templace `radio.pl`.

~~~
extends = basic.pl

radio =: RadioGroup

form ==
{{ radio|component }}
==

evaluator ==
grade = radio.eval()
radio.disabled=True
==
~~~

## Exemple 2 : Capitale d'un pays

[Tester l'exercice](https://pl.u-pem.fr/filebrowser/demo/6899/)

~~~
@ country_data.csv [data.csv]

title = Capitale d'un pays
~~~

On charge les données sur les pays dans la liste `rows`, puis on tire 4 éléments de `rows`. Le premier de ces 4 éléments est la pays dont on demande la capitale. On charge les 4 choix à l'aide de la méthode `loadContent` et on indique la solution avec la méthode `setSolByIndex`. On finit en mélangeant les choix avec la méthode `shuffle`.

~~~
before ==
import random as rd
import csv

with open('data.csv',newline='') as file:
    rows=list(csv.DictReader(file,delimiter=','))

items=rd.sample(rows,4)
country=items[0]['country']
article=items[0]['article']
capitals=[item['capital'] for item in items]

radio.loadContent(capitals)
radio.setSolByIndex(0)
radio.shuffle()

if article=="le":
    ofcountry = "du " + country
elif article=="l":
    ofcountry = "de l'" + country
elif article=="la":
    ofcountry = "de la " + country
elif article=="les":
    ofcountry = "des " + country
==

text ==
Quelle est la capitale {{ofcountry}} ?
==
~~~
