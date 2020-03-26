# Composant JSXGraph

Le composant JSXGraph permet à l'élève de déplacer et de modifier des objets géométriques (points, droites, cercles, courbes, etc.) dans un panneau graphique. Il est basé sur la bibliothèque JavaScript [JSXGraph](https://jsxgraph.org) (voir aussi le [wiki](https://jsxgraph.uni-bayreuth.de/wiki/index.php/Main_Page)).

Les informations récupérées par le composant JSXGraph sont les coordonnées des points (dont les points de contrôle des objets complexes).

[Démo JSXGraph](https://pl.u-pem.fr/filebrowser/demo/14401/)

## Propriétés et méthodes

Propriétés :

  * `attributes` : propriétés du panneau graphique (dimension, navigation, etc.)
  * `script` : script utilisé dans le panneau graphique
  * `points`: dictionnaire contenant tous les points et leurs coordonnées

Méthodes :
  * `setscript` : définit un script JSXGraph.
  * `setscript` : ajoute un script JSXGraph.
  * `getpoint` : renvoie les coordonnées d'un point.
