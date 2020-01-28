# Fichiers externes

Il est possible d'importer des fichiers externes (en format texte) dans l'environnement d'un exercice. Ces fichier peuvent ensuite être utilisées dans les scripts `before` et `evaluator`.

L'inclusion se fait avec l'opérateur `@`.

~~~
@ chemin/vers/mon/fichier.txt [alias]
~~~

## Exemple : Fichier de données CSV

Le [format CSV](https://fr.wikipedia.org/wiki/Comma-separated_values) (Comma-Separated Values) est un format texte représentant des données tabulaires sous forme de valeurs séparées par des virgules. Chaque ligne du texte correspond à une ligne du tableau et les virgules correspondent aux séparations entre les colonnes. Les virgules peuvent être remplacées par d'autres séparateurs (points-virgules, espaces, etc.) La création d'un fichier CSV se fait avec un tableur ou directement dans un éditeur de texte.

Voilà un exemple de fichier CSV contenant les conjugaisons au présent de quelques verbes.

~~~
infinitif,1S,2S,3S,1P,2P,3P
chanter,chante,chantes,chante,chantons,chantez,chantent
manger,mange,manges,mange,mangeons,mangez,mangent
finir,finis,finis,finit,finissons,finissez,finissent
prendre,prends,prends,prend,prenons,prenez,prennent
~~~

Voyons comment créer un exercice de conjugaison à l'aide de ce fichier de données.

Tester l'exercice : [Conjugaisons au présent]()

~~~
extends = /template/basicinput.pl

@ conj_data.csv

title = Conjugaison

before ==
import random as rd
import csv

with open('conj_data.csv',newline='') as file:
    rows=list(csv.DictReader(file,delimiter=','))

row=rd.choice(rows)
p=rd.choice(['1S','2S','3S','1P','2P','3P'])

dic_pronom={'1S':'je','2S':'tu','3S':'il','1P':'nous','2P':'vous','3P':'ils'}

verbe_inf=row['infinitif']
verbe_conj=row[p]
pronom=dic_pronom[p]
==

text ==
Conjuguer le verbe **{{verbe_inf}}** au présent avec le pronom indiqué.
==

form ==
<div class="d-flex align-items-center">
  <div class="align-self-center">{{pronom}} &nbsp; </div>
  <div class="flex-grow-1">{{input|component}}</div>
</div>
==

evaluator ==
if input.value==verbe_conj:
    grade=(100,"")
else:
    grade=(0,"")
==
~~~

L'ouverture du fichier se fait avec la commande Python usuelle `open`. Le nom du fichier à spécifier est le nom de l'alias donné au moment de l'inclusion avec l'opérateur `@`. Pour lire le contenu du fichier, on utilise la commande `DictReader` du module `csv`.

Le reste du code de l'exercice ne présente pas de difficultés.


## Exemple : Module Python

