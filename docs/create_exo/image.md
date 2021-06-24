# Insérer une image

L'image à insérer doit être stockée sur le serveur PLaTon ou stockée sur un serveur extérieur et accessible par une adresse web pérenne (par exemple, une image issue de [Wikimedia](https://commons.wikimedia.org)).

L'insertion dans l'énoncé de l'exercice se fait alors par une balise Markdown ou une balise HTML (pour une mise en forme plus riche).

Attention
Le nom du fichier image, qui apparaît dans l'adresse et est facilement visible par l'élève, peut parfois constituer une indication de la réponse à l'exercice. Dans ce cas, il est préférable de charger l'image sur le serveur PLaTon en lui donnant un nom générique.

## Image accessible par une adresse web

La commande Markdwon pour insérer une image est simplement : `![](adresse web de l'image)`. L'image est affichée à sa taille réelle, dans la limite de la largeur disponible.

```
question ==
![](https://upload.wikimedia.org/wikipedia/commons/thumb/5/5d/Eug%C3%A8ne_Delacroix_-_Le_28_Juillet._La_Libert%C3%A9_guidant_le_peuple.jpg/598px-Eug%C3%A8ne_Delacroix_-_Le_28_Juillet._La_Libert%C3%A9_guidant_le_peuple.jpg)
==
```

Si l'on veut ajuster la place occupée par l'image, il faut utiliser la balise HTML `<img>`.

```
question ==
<img class="img img-40" src="https://upload.wikimedia.org/wikipedia/commons/thumb/c/c3/Flag_of_France.svg/640px-Flag_of_France.svg.png">
==

```
## Image sur le serveur PLaTon

Pour charger une image sur le serveur PLaTon, il faut sélectionner le fichier image dans l'explorateur de fichiers de son ordinateur, puis le glisser-déposer dans l'explorateur de fichiers de l'éditeur de ressources PLaTon.

