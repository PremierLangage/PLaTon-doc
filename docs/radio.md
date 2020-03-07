# Question à choix multiples (un seul choix sélectionnable)

## Composant `RadioGroup`

Le composant `RadioGroup` permet de créer un champ de réponse à choix multiples avec un seul choix sélectionnable. Des méthodes Python (utilisables dans les scripts `before` et `evaluator`) facilitent la manipulation de ce composant.

  * `setitems` : définit la liste des choix.
  * `setsol_from_index` : définit la solution à partir de son indice dans la liste des choix.
  * `setsol_from_content`: définit la solution à partir de son contenu.
  * `shuffle` : mélange la liste des choix.
  * `sort`: trie la liste des choix par ordre alphabétique.
  * `eval`: évalue la réponse de l'élève (en comparant à la solution préalablement définie) et afficher éventuellement une correction visuelle.

## Exemple : Capitale d'un pays

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
