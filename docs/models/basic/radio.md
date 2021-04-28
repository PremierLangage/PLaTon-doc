# Modèle `basic/radio`

Le modèle `basic/radio` permet de fabriquer des exercices à choix multiple (avec un seul item à sélectionner).

## Clés du modèle

Les clés `title`, `text` et `before` ont leur signification et leur syntaxe usuelles.

* `items` (chaîne ou liste). Items de la question
    * Cette clé contient une liste d'items sous la forme d'une chaîne multilignes (chaque ligne correspondant à un choix) ou d'une liste.
* `indsol` (entier). Indice du bon item.
    * L' indice se rapporte à l'ordre des items dans la clé `items`. L'indexation commence à 0.
    * Par défaut `indsol` vaut 0.
* `shuffled` (booléen). Mélange des items.

## Exemples (déclaration explicite des items)

```
extends = /model/basic/radio.pl

title = Géographie

text ==
Quel pays a pour capitale Budapest ?
==

items ==
Hongrie
Estonie
Roumanie
Slovaquie
==
```

```
extends = /model/basic/radio.pl

title = Histoire

text ==
A quel siècle vivait Louis XI ?
==

items ==
XIIe siècle
XIIIe siècle
XIVe siècle
XVe siècle
==

indsol % 3

shuffled % false
```

## Exemples (génération des items par un script)


```
extends = /model/basic/radio.pl

title = Trouver le plus petit nombre

text ==
Sélectionner le plus petit nombre de la liste suivante.
==

before ==
items = sorted(sample(range(50), 4))
==
```

```
extends = /model/basic/radio.pl

title = Géographie

before ==
datasample = csv_sample(data, 4)
capitale = datasample[0]['capitale']
items = [row['pays'] for row in datasample]
==

text ==
Quel pays a pour capitale {{capitale}} ?
==

data ==
pays,article,capitale
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
==
```

```
extends = /model/basic/radio.pl

title = Géographie

@ /demo/data/pays_europe.csv

before ==
with open('pays_europe.csv', newline='') as f:
    datasample = csv_sample(f, 4)
capitale = datasample[0]['capitale']
items = [row['pays'] for row in datasample]
==

text ==
Quel pays a pour capitale {{capitale}} ?
==
```
