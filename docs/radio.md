# Question à choix multiples (un seul choix sélectionnable)

## Composant `RadioGroup`

Le composant `RadioGroup` permet de créer un champ de réponse à choix multiples avec un seul choix sélectionnable. Des méthodes Python (utilisables dans les scripts `before` et `evaluator`) facilitent la manipulation de ce composant.

  * `setitems` : définit la liste des choix.
  * `setsol_from_index` : définit la solution à partir de son indice dans la liste des choix.
  * `setsol_from_content`: définit la solution à partir de son contenu.
  * `shuffle` : mélange la liste des choix.
  * `sort`: trie la liste des choix par ordre alphabétique.
  * `eval`: évalue la réponse de l'élève (en comparant à la solution préalablement définie) et affiche éventuellement une correction visuelle.

## Exemple : Capitale d'un pays

Dans cet exercice, on demande à l'élève de trouver la capitale d'un pays d'Europe parmi une liste de quatre choix. Les données sont tirées aléatoirement à partir d'un fichier CSV.

[Tester l'exercice](https://pl.u-pem.fr/filebrowser/demo/6899/)

On commence par hériter du modèle d'exercice `basic.pl` et on inclut le fichier de données `pays_europe.csv` dans l'environnement de l'exercice.

~~~
extends = /model/basic.pl

@ pays_europe.csv
~~~

On crée un composant de type `RadioGroup` qu'on appelle `radio`.

~~~
radio =: RadioGroup
~~~

Dans le script `before`, on lit les données du fichier `pays_europe.csv` et on les stocke dans la liste `all_rows`. Chaque élément de la liste contient les données d'un pays sous forme d'un dictionnaire dont les clés sont `pays`, `article` et `capitale`. On tire aléatoirement 4 éléments de cette liste.

On définit la liste des 4 choix de capitales à l'aide de la méthode `setitems`. On indique que la solution est le premier choix avec la méthode `setsol_from_index`. Enfin, on mélange les choix avec la méthode `shuffle`.

~~~
before ==
import random as rd
import csv

with open('pays_europe.csv', newline='') as file:
    all_rows = list(csv.DictReader(file, delimiter=','))
    
sample_rows = rd.sample(all_rows, 4)

pays = sample_rows[0]['pays']
article = sample_rows[0]['article']

radio.setitems([row['capitale'] for row in sample_rows])
radio.setsol_from_index(0)
radio.shuffle()

partitif = {"le": "du ", "la": "de la ", "les": "des ", "l": "de l'"}
du_pays = partitif[article] + pays
==
~~~

~~~
text ==
Quelle est la capitale {{ du_pays }} ?
==

form ==
{{ radio|component }}
==
~~~

~~~
evaluator ==
score = radio.eval()
==
~~~
