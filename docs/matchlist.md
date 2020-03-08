# Correspondances

## Composant `MatchList`

Le composant `MatchList` permet de créer un champ de réponse de type correspondances (il s'agit de relier les items d'une liste source aux items d'une liste cible). Des méthodes Python (utilisables dans les scripts `before` et `evaluator`) facilitent la manipulation de ce composant.

  * `setitems` : définit la liste des items sources et des items cibles.
  * `setsol` : définit les correspondances solutions.
  * `setdata_from_matches` : définit la liste des items sources et des items cibles ainsi que les correspondances solutions à partir d'une liste de couples cible-source.
  * `eval` : évalue la réponse de l'élève (en comparant aux solutions préalablement définies) et affiche éventuellement une correction visuelle.

## Exemple : Capitales

Dans cet exercice, on demande à l'élève d'associer pays et capitales. Les données sont tirées aléatoirement à partir d'un fichier CSV.

[Tester l'exercice](https://pl.u-pem.fr/filebrowser/demo/6899/)

On commence par hériter du modèle d'exercice `basic.pl` et on inclut le fichier de données `pays_europe.csv` dans l'environnement de l'exercice.

~~~
extends = /model/basic.pl

@ pays_europe.csv
~~~

On crée un composant de type `MatchList` qu'on appelle `matchlist`.

~~~
matchlist =: MatchList
~~~

Dans le script `before`, on lit les données du fichier `pays_europe.csv` et on les stocke dans la liste `all_rows`. Chaque élément de la liste contient les données d'un pays sous forme d'un dictionnaire dont les clés sont notamment `pays` et `capitale`. On tire aléatoirement 4 éléments de cette liste.

~~~
before==
import random as rd
import csv

with open('pays_europe.csv', newline='') as file:
    all_rows = list(csv.DictReader(file,delimiter=','))
    
sample_rows = rd.sample(all_rows, 4)

matchlist.setdata_from_matches([(row['pays'], row['capitale']) for row in sample_rows])
==
~~~
