# Modèle `basic/input`

Le modèle `basic/input` permet de fabriquer des exercices avec un champ de réponse textuel.

[![](input1.png)](https://pl.u-pem.fr/filebrowser/demo/33986/)

## Clés du modèle

* `text` (chaîne). Enoncé de l'exercice.
* `sol` (chaîne). Solution de l'exercice.
    * Chaque ligne correspond à une réponse acceptée. 
* `casesensitive` (booléen).
    *  Si cette clé vaut `false`, l'évaluation de la réponse ne tient pas compte de la casse. 
    *  Par défaut, cette clé vaut `false`.
* `diffmeasure` ("EditDist", "EditRatio"). Msure utilisée pour calculer l'écart entre la réponse de l'élève et la solution. 
    * Par défaut cette clé vaut `"EditDist"`.
* `tol` (nombre). Ecart maximal accepté (pour le type mesure choisi dans `diffmeasure`). 
    * Par défaut cette clé vaut `0`.

TODO : Un 2e seuil de tolérance qui déclencherait un avertissement ?

## Exemples

#### Littérature

Dans cet exemple, les solutions acceptées sont `Victor Hugo`, `Hugo`, mais aussi, puisque par défaut on ne tient pas compte de la casse, `victor hugo`, `victor Hugo`, `HUGO`, etc.

[Tester l'exercice](https://pl.u-pem.fr/filebrowser/demo/33986/)

~~~
extends = /model/basic/input.pl

text ==
Qui a écrit *Les Misérables* ?
==

sol ==
Victor Hugo
Hugo
==
~~~

#### Chimie

Dans cet exemple, les solutions acceptées sont les chaînes égales à `Oxygène` à un caractère près : `oxigène`, `oxgène`, `oxygèn`, etc.

[Tester l'exercice](https://pl.u-pem.fr/filebrowser/demo/34253/)

~~~
extends = /model/basic/input.pl

title ==
Chimie
==

text ==
Quel élément chimique a pour symbole **O** ?
==

sol ==
Oxygène
==

diffmeasure = EditDist

tol = 1
~~~

#### Listening

~~~
extends = /model/basic/input.pl

title = Listening

file =$ english_sentence.mp3

text ==
{{ audio_button(file) }} Transcrire la phrase.
==

sol ==
I'm gonna make him an offer he can't refuse
==

diffmeasure = EditRatio

tol % 0.1
~~~
