# Utilisation d'un fichier de données

## Fichiers CSV

Le [format CSV](https://fr.wikipedia.org/wiki/Comma-separated_values) (Comma-Separated Values) est un format texte représentant des données tabulaires sous forme de valeurs séparées par des virgules. Chaque ligne du texte correspond à une ligne du tableau et les virgules correspondent aux séparations entre les colonnes. Les virgules peuvent être remplacées par d'autres séparateurs (points-virgules, espaces, etc.) La création d'un fichier CSV se fait avec un tableur ou directement dans un éditeur de texte.

Voilà un exemple de fichier CSV contenant une liste de pays européens et leur capitale.

~~~
country,article,capital
Allemagne,l,Berlin
Autriche,l,Vienne
Belgique,la,Bruxelles
Danemark,le,Copenhague
Espagne,l,Madrid
Finlande,la,Helsinki
France,la,Paris
Grèce,la,Athènes
Hongrie,la,Budapest
Irlande,l,Dublin
Italie,l,Rome
Norvège,la,Oslo
Pays-Bas,les,Amsterdam
Pologne,la,Varsovie
Portugal,le,Lisbonne
Roumanie,la,Bucarest
Royaume-Uni,le,Londres
Slovaquie,la,Bratislava
Suède,la,Stockholm
Suisse,la,Berne
~~~

## Exemple d'exercice utilisant un fichier de données CSV

Voyons comment créer un exercice sur les capitales à l'aide de ce fichier de données.

Tester l'exercice : []()

L'ouverture du fichier se fait avec la commande Python usuelle `open`. Pour lire le contenu du fichier, on utilise la commande `DictReader` du module `csv`.

~~~
import csv

with open('pays_europe.csv',newline='') as file:
    rows = list(csv.DictReader(file,delimiter=','))
~~~

## Code complet

~~~
@ /builder/before.py [builder.py]
@ /grader/evaluator.py [grader.py]

@ pays_europe.csv

title = Capitales d'Europe

before ==
import random as rd
import csv

with open('pays_europe.csv',newline='') as file:
    rows = list(csv.DictReader(file,delimiter=','))
    
row = rd.choice(rows)

pays = row['pays']
article = row['article']
capitale = row['capitale']

partitif = {"le":"du ", "la":"de la ", "les":"des ", "l":"de l'"}
du_pays = partitif[article] + pays
==

text ==
Quelle est la capitale {{du_pays}} ?
==

input =: Input

form ==
{{ input | component }}
==

settings.feedback = rightwrong

evaluator ==
if input.value == capitale:
    grade = (100,"")
else:
    grade = (0, capitale)
==
~~~

