# Question à choix multiples (un seul choix sélectionnable)

## Composant `RadioGroup`

Le composant `RadioGroup` permet de créer un champ de réponse à choix multiples avec un seul choix sélectionnable. Il dispose de méthode pour 

  * La méthode `loaditems` permet de charger la liste des choix possibles.
  * Les méthodes `setsol_by_content` et `setsol_by_content` permettent de définir la solution (en vue d'une évaluation automatique de la réponse de l'élève).
  * Les méthodes `shuffle` et `sort` permettent respectivement de mélanger et de trier la liste des choix.
  * La méthode `eval` permet d'évaluer la réponse de l'élève en renvoyant une note et en affichant une correction visuelle.

## Exemple 1 : Capitale d'un pays

[Tester l'exercice](https://pl.u-pem.fr/filebrowser/demo/6899/)

On commence par créer un composant de type `RadioGroup` qu'on appelle `radio`.

~~~
radio =: RadioGroup
~~~

Dans le script `before`, on commence par lire les données du fichier `pays_europe.csv`. On stocke ces données dans la liste `rows`, puis on tire aléatoirement 4 éléments de `rows`. Le premier de ces 4 éléments correspond au pays dont on va demander la capitale à  l'élève. On charge les 4 nomes de pays à l'aide de la méthode `loaditems` et on indique la solution avec la méthode `setsol_by_index`. On termine en mélangeant les choix avec la méthode `shuffle`.

~~~
before ==
import random as rd
import csv

with open('pays_europe.csv',newline='') as file:
    all_rows = list(csv.DictReader(file,delimiter=','))
    
sample_rows=rd.sample(all_rows,4)

pays = sample_rows[0]['pays']
article = sample_rows[0]['article']

radio.loaditems([row['capitale'] for row in sample_rows])
radio.setsol_by_index(0)
radio.shuffle()

partitif = {"le":"du ", "la":"de la ", "les":"des ", "l":"de l'"}
du_pays = partitif[article] + pays
==
~~~
