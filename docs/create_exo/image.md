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

Si l'on veut paraméter le rendu de l'image (taille, alignement, etc.), il est nécessaire de revenir la balise HTML `<img>`. Pour les paramétrages les plus courants, la plateforme propose plusieurs classes prédéfinies. La classe `img` permet de centrer l'image. Les classes `img-40`, `img-60`, `img-80` ajustent l'image à 40%, 60%, 80% de la largeur (sur tablette et téléphone, ces valeurs sont automatiquement rehaussées).

```
question ==
<img class="img img-40" src="https://w.wiki/3ZAX">
==

```
## Image sur le serveur PLaTon

Pour charger une image sur le serveur PLaTon, il faut sélectionner le fichier image dans l'explorateur de fichiers de son ordinateur, puis le glisser-déposer dans l'explorateur de fichiers de l'éditeur de ressources PLaTon.

