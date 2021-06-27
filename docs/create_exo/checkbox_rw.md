# Question à choix multiple (3)

Il existe un deuxième modèle pour fabriquer une question à choix multiple avec plusieurs propositions sélectionnables : le modèle `basic/checkbox_rw`. 

Dans ce modèle, les clés de base sont :

  * `question` : l'énoncé de l'exercice ;
  * `right` : une liste de bonnes réponses ;
  * `wrong` : une liste de mauvaises réponses.

Par défaut, les deux listes sont fusionnées et mélangées. Comme pour le modèle `basic/checkbox`, le barème est modifiable grâce à la clé `scoring`.

**Exemple 1**

```
extends = /model/basic/checkbox_rw.pl

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

Avec ce modèle, il est également possible d'obtenir de l'aléa en entrant des listes longues dans les clés `right` et `wrong`, puis en fixant le nombre de propositions et de bonnes réponses à tirer.

Les clés paramétrant ce comportement sont :

  * `nbitems` : nombre de propositions à tirer;
  * `minright` : nombre minimal de bonnes réponses à tirer;
  * `maxright` : nombre maximal de bonnes réponses tirer.


**Exemple 2**

```
extends = /model/basic/checkbox_rw.pl

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
