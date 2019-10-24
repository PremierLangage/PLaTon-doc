# Question à choix multiples (radio)

## Exemple 1 : Plus petit nombre

[Tester l'exercice](https://pl.u-pem.fr/filebrowser/option?name=test_pl&path=Yggdrasil/demo/radio1.pl)

On commence par créer un composant `RadioGroup`.

~~~
radio =: RadioGroup
~~~

On tire une liste 4 nombres au hasard entre 0 et 49. Avec la méthode `loadContent`, on charge cette liste de choix dans le composant. On détermine le plus petit de ces 4 nombres et on indique qu'il s'agit de la solution en utilisant la méthode `setSolByContent`.

~~~
before ==
import random as rd
numbers=rd.sample(list(range(50)),4)
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
{{ radio|component }}
==
~~~

~~~
evaluator ==
grade = radio.eval()
radio.disabled=True
==
~~~

## Template `radio.pl`

~~~
extends = basic.pl

@ /utils/radiogroup.py [customradiogroup.py]

radio =: RadioGroup
radio.decorator = CustomRadioGroup

form = {{ radio|component }}

evaluator ==
grade = radio.eval()
radio.disabled=True
==
~~~

## Exemple 2 : Capitale d'un pays

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
