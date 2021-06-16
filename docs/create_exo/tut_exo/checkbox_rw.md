# Question à choix multiple (3)

Il existe un deuxième modèle pour fabriquer une question à choix multiple avec plusieurs propositions sélectionnables : le modèle `basic/checkbox_rw`. 

Dans ce modèle, les clés de base sont :

  * `question` : l'énoncé de l'exercice ;
  * `right` : une liste de bonnes réponses ;
  * `wrong` : une liste de mauvaises réponses.

Par défaut, les deux listes sont fusionnées et mélangées. Comme pour le modèle `basic/checkbox`, le barème est modifiable grâce à la clé `scoring`.

**Exemple 1**

```
extends = /model/basic/checkbox.pl

question ==
Parmi ces villes, lesquelles ne sont pas des capitales ?
==

right ==
Barcelone
Milan
==

wrong ==
Paris
Berlin
==
```

Avec ce modèle, il est également possible d'obtenir des ensembles aléatoires de propositions en entrant des listes suffisamment longues dans les clés `right` et `wrong`, puis en choisissant le nombre de propositions et le nombre de bonnes réponses.

Les clés paramétrant ces choix sont :

  * `nbitems` : nombre de propositions ;
  * `minright` : nombre minimal de bonnes réponses ;
  * `maxright` : nombre maximal de bonnes réponses.


**Exemple 2**

```
extends = /model/basic/checkbox.pl

question ==
Parmi ces villes, lesquelles ne sont pas des capitales ?
==

right ==
Barcelone
Milan
New-York
Montréal
Saint-Pétersbourg
Genève
Bombay
Shanghai
==

wrong ==
Paris
Berlin
Rome
Madrid
Moscou
Ottawa
Washington
Pékin
==

nbitems = 4
minright = 1
maxright = 2
```
