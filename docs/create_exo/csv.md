# Générer aléatoirement des données à partir d'un fichier

## Fichiers CSV

Le [format CSV](https://fr.wikipedia.org/wiki/Comma-separated_values) (Comma-Separated Values) permet de représenter un tableau de données. Il s'agit d'un format texte où chaque ligne représente une ligne du tableau et où les cellules d'une ligne sont séparées par des virgules. Les virgules peuvent être remplacées par d'autres séparateurs (points-virgules, espaces, etc.) On peut créer un fichier CSV avec un tableur ou simplement un éditeur de texte.

Voilà un exemple de fichier CSV contenant une liste de pays européens et leur capitale.

~~~
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
~~~

## Lire des données dans un fichier CSV

La commande

```python
>>> f = open('pays_europe.csv')
```

La fonction `csv_choice` permet de tirer aléatoirement une ligne dans un fichier CSV. Plus précisément, la commande `csv_choice(f)` renvoie une ligne du fichier CSV `f` sous forme d'un dictionnaire dont les clés sont les en-têtes du fichier.

```python
>>> row = csv_choice(f)
>>> row['pays']
'Rome'
>>> row['capitale']
'Italie'
```

La fonction `csv_csample` permet de tirer aléatoirement plusieurs igne dans un fichier CSV. Plus précisément, la commande `csv_sample(f, k)` renvoie `k` lignes du fichier CSV `f` sous forme d'une liste de dictionnaires.

```python
>>> data = csv_sample(f, 4)
>>> data[0]['pays']
'Portugal'
>>> data[1]['pays']
'Autriche'
```

## Un exemple d'exercice

Pour pouvoir utiliser un fichier externe dans un exercice, il faut tout d'abord nécessaire de charger ce fichier dans l'environnement de l'exercice grâce à l'opérateur `@` de la syntaxe PL.

```
extends = /model/basic/input.pl

@ /demo/data/pays_europe.csv

before ==
f = open('pays_europe.csv')
row = csv_choice(f)
capitale = row['capitale']
sol = row['pays']
==

question ==
Quel pays a pour capitale {{capitale}} ?
==
```
