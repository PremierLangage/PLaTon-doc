# Générer aléatoirement des données à partir d'un fichier

## Fichiers CSV

Le [format CSV](https://fr.wikipedia.org/wiki/Comma-separated_values) (Comma-Separated Values) permet de représenter un tableau de données. Il s'agit d'un format texte où chaque ligne représente une ligne du tableau et où les cellules d'une ligne sont séparées par des virgules. Les virgules peuvent être remplacées par d'autres séparateurs (points-virgules, espaces, etc.) On peut créer un fichier CSV avec un tableur ou simplement un éditeur de texte.

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

## Lire des données dans un fichier CSV

Pour utiliser un fichier externe dans un exercice, il est tout d'abord nécessaire de charger ce fichier dans l'environnement de l'exercice grâce à l'opérateur `@` de la syntaxe PL.

Ensuite, dans le script `before`, on peut utiliser les commandes Python usuelles pour la manipulation des fichiers.


## Un exemple d'exercice



