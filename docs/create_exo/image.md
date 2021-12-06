# Insérer une image

L'image à insérer doit être stockée sur le serveur PLaTon ou stockée sur un serveur extérieur et accessible par une adresse web pérenne (par exemple, une image issue de [Wikimedia](https://commons.wikimedia.org)).

L'insertion dans l'énoncé de l'exercice se fait alors par une balise Markdown ou une balise HTML (pour une mise en forme plus riche).

Attention
Le nom du fichier image, qui apparaît dans l'adresse et est facilement visible par l'élève, peut parfois constituer une indication de la réponse à l'exercice. Dans ce cas, il est préférable de charger l'image sur le serveur PLaTon en lui donnant un nom générique.

## Image accessible par une adresse web

La commande Markdwon pour insérer une image est simplement : `![](adresse web de l'image)`. L'image est affichée à sa taille réelle, dans la limite de la largeur disponible.

```
question ==
![](https://w.wiki/3ZAX)
==
```

Si l'on veut paramétrer le rendu de l'image (taille, alignement, etc.), il est nécessaire d'utiliser une balise HTML `<img>`. Pour les paramétrages les plus courants, la plateforme propose plusieurs classes prédéfinies. La classe `img` permet de centrer l'image. Les classes `w100`, `w90`, `w80`, ..., `w10` ajustent l'image à 100%, 90%, 80%, ..., 10% de la largeur (sur tablette et téléphone, ces valeurs sont automatiquement rehaussées).

```
question ==
<img class="img w40" src="https://w.wiki/3ZAX">
==

```
## Image sur le serveur PLaTon

Pour charger une image sur le serveur PLaTon, il faut sélectionner le fichier image dans l'explorateur de fichiers de son ordinateur, puis le glisser-déposer dans l'explorateur de fichiers de l'éditeur de ressources PLaTon.


## Un exemple d'exercice

```
extends = /model/basic/radio.pl

flag0 =$ /demo/media/flag0.png
flag1 =$ /demo/media/flag1.png
flag2 =$ /demo/media/flag2.png
flag3 =$ /demo/media/flag3.png

before ==
indsol = randint(0, 3)
flags = [flag0, flag1, flag2, flag3]
flag = flags[indsol]
==

question ==
A quel pays appartient ce drapeau ?
<img class="img w40" src="{{ flag }}">
==

items ==
France
Espagne
Allemagne
Italie
==
```

