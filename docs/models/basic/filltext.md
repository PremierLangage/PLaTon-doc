# Modèle `basic/filltext`

Le modèle `basic/filltext` permet de fabriquer des exercices de type *texte à trous*

## Clés du modèle

#### Clés de base
* `filledtext` (string). Texte complet. Les mots entre accolades seront remplacés par des trous.
* `labval` (string). Etiquettes supplémentaires.

## Exemples

#### Génétique

~~~
extends = /model/basic/filltext.pl

title = Génétique

text ==
Compléter le texte suivante avec les bonnes étiquettes.
==

filledtext ==
L’ensemble des gènes caractéristiques de l’espèce à laquelle appartient un organisme, constitue son {génome}. 
Chez les individus d’une même espèce, un gène peut cependant exister sous différentes formes présentant de légères modifications de séquence : les allèles. 
L’ensemble des allèles d’un individu définit son {génotype}. Lorsqu’ils s’expriment, lors de la synthèse des protéines, les gènes participent à la construction de l’individu et à la mise en place de son {phénotype}. 
==

labval ==
caryotype
ADN
ARN
==
~~~
