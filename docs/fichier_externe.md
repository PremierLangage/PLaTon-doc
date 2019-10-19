# Utiliser un fichier de données

Pour beaucoup d'exercices, les données utilisées dans l'énoncé seront stockées dans un fichier externe. Voyons donc comment lire un fichier externe depuis un exercice PL, à travers l'exemple d'un exercice de conjugaison.

Tester l'exercice : [Conjugaisons au présent]()

Les conjugaisons au présent d'un certain nombre de verbes sont stockées dans un fichier `conj_pres.csv` dans le répertoire `\home\demo\`. Le contenu de ce fichier est affiché ci-dessous.

~~~
infinitif,1S,2S,3S,1P,2P,3P
chanter,chante,chantes,chante,chantons,chantez,chantent
manger,mange,manges,mange,mangeons,mangez,mangent
finir,finis,finis,finit,finissons,finissez,finissent
prendre,prends,prends,prend,prenons,prenez,prennent
~~~

!!! note
    Le format CSV (Comma-Separated Values) est un format texte représentant des données tabulaires sous un forme de valeurs séparées par des virgules. Chaque ligne du texte correspond à une ligne du tableau et les virgules correspondent aux séparations entre les colonnes. Les virgules peuvent parfois être remplacées par d'autres séparateurs (points-virgules, espaces, etc.)

Pour utiliser un fichier externe dans un exercice, il faut d'abord l'inclure grâce à l'opérateur `@`.

~~~
@ conj_data.csv [data.csv]
~~~

L'ouverture du fichier se fait avec la commande Python usuelle `open`. Le nom du fichier à spécifier est le nom de l'alias donné au moment de l'inclusion avec l'opérateur `@`. Pour lire le contenu du fichier, on utilise la commande `DictReader` du module `csv`.

~~~
before ==

import random as rd
import csv

with open('data.csv',newline='') as file:
    rows=list(csv.DictReader(file,delimiter=','))

row=rd.choice(rows)
p=rd.choice(['1S','2S','3S','1P','2P','3P'])

lst_txt_prs={'1S':'1ère personne du singulier',
         '2S':'2e personne du singulier',
         '3S':'3e personne du singulier',
         '1P':'1ère personne du pluriel',
         '2P':'2e personne du pluriel',
         '3P':'3e personne du pluriel'}

verbe_inf=row['infinitif']
verbe_conj=row[p]
txt_prs=lst_txt_prs[p]

==
~~~

Le reste du code de l'exercice ne présente pas de difficultés.

~~~
text ==
Conjuguer le verbe {{verbe_inf}} à la {{txt_prs}} du présent.
==

input =: Input

form ==
{{input|component}}
==

evaluator ==
if input.value==verbe_conj:
    grade=(100,"")
else:
    grade=(0,"")
==
~~~
