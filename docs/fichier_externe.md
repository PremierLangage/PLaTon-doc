# Utiliser un fichier de données

On dispose d'un fichier au format CSV contenant les conjugaisons au présent de certains verbes.

~~~
infinitif,1S,2S,3S,1P,2P,3P
chanter,chante,chantes,chante,chantons,chantez,chantent
manger,mange,manges,mange,mangeons,mangez,mangent
finir,finis,finis,finit,finissons,finissez,finissent
prendre,prends,prends,prend,prenons,prenez,prennent
~~~

Pour utiliser un fichier externe dans un exercice, il faut d'abord l'inclure grâce à l'opérateur `@`.

~~~
@ conj_data.csv [data.csv]
~~~

~~~
before ==

import random as rd
import csv

with open('data.csv',newline='') as file:
    rows=list(csv.DictReader(file,delimiter=','))

row=rd.choice(rows)
p=rd.choice(['1S','2S','3S','1P','2P','3P'])

lst_txt_prs={'1S':'1ère personne du singulier',
         '2S':'2e personne du singulier',
         '3S':'3e personne du singulier',
         '1P':'1ère personne du pluriel',
         '2P':'2e personne du pluriel',
         '3P':'3e personne du pluriel'}

verbe_inf=row['infinitif']
verbe_conj=row[p]
txt_prs=lst_txt_prs[p]

==
~~~

~~~
text ==
Conjuguer le verbe {{verbe_inf}} à la {{txt_prs}} du présent.
==
~~~

~~~
input =: Input

form ==
{{input|component}}
==
~~~

~~~
evaluator ==
if input.value==verbe_conj:
    grade=(100,"")
else:
    grade=(0,"")
==
~~~
