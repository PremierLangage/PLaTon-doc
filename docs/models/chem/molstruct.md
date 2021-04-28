# Modèle `chem/molstruct`

Le modèle `chem/molstruct` permet de fabriquer des exercices où l'élève doit dessiner la structure d'une molécule.

## Clés du modèle

* `smiles` (chaîne). Chaîne SMILES de la molécule à dessiner. 

## Exemple

```
extends = /model/chem/molstruct.pl

title = Décrire la structure d'une molécule

text ==
Décrire la structure du 3-Méthylbutan-1-ol
==

smiles = OCCC(C)C
```
