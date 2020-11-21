# Enoncé

L'énoncé de l'exercice est à définir dans la clé `text`. Avant d'être inséré dans le code HTML de la page web de l'exercice, le contenu de la clé `text` subit une inteprétation Jinja puis une interprétation Markdown.

L'inteprétation [Jinja](https://jinja.palletsprojects.com/) permet d'obtenir un énoncé dynamique, qui peut notamment intègrer les données générées par le script `before`.

L'interprétation Markdown offre une syntaxe de mise en forme plus légère que la syntaxe HTML (pour une mise en forme simple).


## Interprétation Jinja

Le langage des ***templates*** Jinja permet d'insérer des variables et des expressions (en leur appliquant éventuellement des fonctions) et d'utiliser des structures de contrôle (`if`, `for`, etc.) La syntaxe est inspirée de la syntaxe Python. L'interprétation d'un *template* Jinja se fait par rapport à un **contexte**, c'est-à-dire un dictionnaire de valeurs. 

Pour l'interprétation de la clé `text`, le contexte utilisé est le dictionnaire Python de l'exercice tel qu'il est à la fin de l'exécution du script `before`.

~~~
before ==
import random as rd
mot = rd.choice(["fourchette", "couteau", "assiette"])
==

text ==
Le mot {{ mot }} est-il féminin ou masculin ?
==
~~~

Des balises permettent aussi de contrôler la structure du document.

## Interprétation Markdown
