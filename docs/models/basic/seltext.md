# Modèle `basic/seltext`

Le modèle `basic/seltext` permet de fabriquer des exercices où l'élève doit sélectionner des unités dans un texte.

## Clés du modèle

* `seltext` (chaîne). Texte à sélectionner.
    * Par défaut les unités sélectionnables du texte sont les mots. Pour définir une unité sélectionnable différente d'un mot, il suffit d'entourer cette unité d'accolades.
    * Les unités à sélectionner doivent être indiquées entre double accolades.

## Exemples

```
extends = /model/basic/seltext.pl

title = Grec ancien

text ==
Identifier les adjectifs comparatifs dans le texte ci-dessous.
==

seltext == 
Δαρείου καὶ Παρυσάτιδος γίγνονται παῖδες δύο, {{πρεσβύτερος}} μὲν Ἀρταξέρξης, {{νεώτερος}} δὲ Κῦρος· 
ἐπεὶ δὲ ἠσθένει Δαρεῖος καὶ ὑπώπτευε τελευτὴν τοῦ βίου, ἐβούλετο τὼ παῖδε ἀμφοτέρω παρεῖναι.
==
```
