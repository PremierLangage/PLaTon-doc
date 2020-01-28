# Utilisation d'un fichier de données

## Importation de fichiers externes

Il est possible d'importer des fichiers externes (en format texte) dans l'environnement d'un exercice. Ces fichier peuvent ensuite être utilisées dans les scripts `before` et `evaluator`.

L'inclusion se fait avec l'opérateur `@`.

~~~
@ chemin/vers/mon/fichier.txt [alias]
~~~

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

Tester l'exercice : [Conjugaisons au présent]()

~~~
@ /utils/sandboxio.py
@ /builder/before2.py [builder.py]
@ /grader/evaluator2.py [grader.py]

@ country_data2.csv [data.csv]

title = Capitales d'Europe

before ==
import random as rd
import csv

with open('data.csv',newline='') as file:
    rows=list(csv.DictReader(file,delimiter=','))

item=rd.choice(rows)
country=item['country']
article=item['article']
capital=item['capital']

partitif={"le":"du ","la":"de la ","les":"des ","l":"de l'"}
ofcountry = partitif[article] + country
==

text ==
Quelle est la capitale {{ofcountry}} ?
==

input =: Input

form ==
{{ input | component }}
==

evaluator ==
if input.value==capital:
    grade=(100,"")
else:
    grade=(0,"")
==
~~~

L'ouverture du fichier se fait avec la commande Python usuelle `open`. Le nom du fichier à spécifier est le nom de l'alias donné au moment de l'inclusion avec l'opérateur `@`. Pour lire le contenu du fichier, on utilise la commande `DictReader` du module `csv`.

Le reste du code de l'exercice ne présente pas de difficultés.
