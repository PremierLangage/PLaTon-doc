# Modèle `basic/seltext`

Le modèle `basic/seltext` permet de fabriquer des exercices où l'élève doit sélectionner des unités (mots, groupes de mots, groupes de lettres) dans un texte.

## Clés du modèle

* `seltext` (chaîne). Texte à sélectionner.
    * Par défaut les unités sélectionnables du texte sont les mots. Pour définir une unité sélectionnable différente d'un mot, il suffit d'entourer cette unité de crochets.
    * Les unités solutions doivent être indiquées entre accolades ({}).
    
* Pour considérer les accolades et les crochets comme des caractères et non des délimiteurs d'unités (solution ou pas), on met les précède de '\'

TODO : Options pour changer les délimiteurs.

## Exemples

```
extends = /model/basic/seltext.pl

title = Compréhension d'un texte

text ==
Sélectionner dans ce texte les mots qui désignent Van Gogh
==

seltext == 
En 1888, {Vincent Van Gogh} peint [«Nuit Etoilée»]. 
Il est difficile de représenter [la nuit] [en couleurs].
{L'artiste} installait [son chevalet] lorsque [la nuit] tombait.
Mais comment peindre sans lampadaire ? 
{Le peintre} a eu pour cela [une idée lumineuse]. 
On dit qu'{il} a planté [des bougies] sur [le rebord] de [son chapeau]. 
{L'homme} a ainsi pu peindre grâce [aux minuscules flammes]
Mon super test pour les \{accolades\} et les \[crochets\].
==
```
