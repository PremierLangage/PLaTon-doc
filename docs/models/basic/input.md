# Modèle `input`

Le modèle `input` permet de fabriquer des exercices avec un champ de réponse textuel libre.

[![](input1.png)](https://pl.u-pem.fr/filebrowser/demo/33986/)

## Clés du modèle

#### Clés obligatoires
* `text` (string). Enoncé de l'exercice.
* `solution` (string). Solution de l'exercice.

#### Clés d'évaluation (optionnelles)
* `casesensitive` (boolean). Si cette clé vaut `false`, l'évaluation de la réponse ne tient pas compte de la casse. Par défaut, cette clé vaut `false`.
* `diffmeasure` ("EditDist", "EditRatio"). Type de mesure utilisée pour calculer l'écart entre la réponse entrée par l'élève et la solution. Par défaut cette clé vaut `"EditDist"`.
* `tolerance` (number). Ecart maximal accepté (pour le type mesure choisi dans `diffmeasure`). Par défaut cette clé vaut `0`.

#### Clés de données (optionnelles)
* `data` (string). Données (au format CSV) qui pourront être utilisées dans les clés `text` et `solution`.
* `delimiter`(string). Délimiteur utilisé dans le format CSV des données de `data`. Par défaut, cette clé vaut `","`.
* `skipinitialspace` (boolean). Si cette clé vaut `false`, l'espace initial après chaque délimiteur est ignoré à la lecture des données. Par défaut, cette clé vaut `true`.

## Exemples

~~~
extends = /model/basic/input.pl

text ==
Qui a écrit *Les Misérables* ?
==

solution ==
Victor Hugo
Hugo
==
~~~

~~~
extends = /model/basic/input.pl

title ==
Exemple 2
==

data ==
symbole,nom
Hydrogène,H
Hélium,He
Carbone,C
Azote,N
Oxygène,O
Fluor,F
Néon,Ne
Sodium,Na
Magnésium,Mg
Aluminium,Al
Silicium,Si
Phosphore,P
Soufre,S
Chlore,Cl
Argon,Ar
Potassium,K
Calcium,Ca
Chrome,Cr
Manganèse,Mn
Fer,Fe
Cobalt,Co
Nickel,Ni
Cuivre,Cu
Zinc,Zn
==

text ==
Quel élément chimique a pour symbole **{{ symbole }}** ?
==

solution ==
{{ nom }}
==

diffmeasure = EditDist

tolerance = 1
~~~
