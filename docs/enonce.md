# Enoncé

L'énoncé de l'exercice est à définir dans la clé `text`. Avant d'être inséré dans le code HTML de la page web de l'exercice, le contenu de la clé `text` subit plusieurs traitements.

Pour permettre des énoncés dynamiques (dépendant des données générés dans le script `before`), le *builder* applique applique d'abord une mise en forme Jinja au contenu de la clé `text`.


## Interprétation Jinja

Un [***template*** Jinja](https://jinja.palletsprojects.com/en/2.11.x/templates/) contient des variables et des expressions qui sont remplacées au moment de l'interprétation.

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
