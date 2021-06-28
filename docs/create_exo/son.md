# Insérer un son

Comme pour une image, le son à insérer doit être stocké sur le serveur PLaTon ou stocké sur un serveur extérieur et accessible par une adresse web pérenne.

L'insertion dans l'énoncé de l'exercice se fait alors par une balise HTML.

```
question ==
<audio id="player" controls src="https://w.wiki/3ZAq"></audio> 
==
```

```
question ==
<audio id="player" src="https://w.wiki/3ZAq"></audio> 
<button onclick="player.play()" class="btn btn-sm btn-info icon-audio"></button>
==
```
