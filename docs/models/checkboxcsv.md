
# CheckBox QCM Choix multiples avec un fichier de données

Si vous avez une base de connaissances qui fait des associations par exemple une association entre une maladie et le type de pathogène le fichier *maladies.csv* : 

```
target;source
Tuberculose;bactéries
Tétanos;bactéries
Typhoïde;bactéries
Lèpre;bactéries
Rage;virus
Poliomyélite;vi
```

Vous souhaitez un exercice qui vas proposer des tirages aléatoires de questions prises dans ce fichier.

```
extends= /model/checkbox/checkboxcsv.pl
# le fichier csv 
@ maladies.csv [content.csv]
```

# Futur 

Possibilités de préciser le délimiteur, le nombre de propositions, le nombre de proposition exactes.

Possibilité de changer le type d'exercice ou qu'il soit choisi aléatoirement.

