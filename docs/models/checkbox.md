# Questions a choix Multiple 

Vous avez deux possibilités soit vous utiliser directement le composant: https://pl.u-pem.fr/components/checkbox-group

Soit vous utiliser un des modèles l'utilisant:

```
extends = /model/checkbox/goodbad.pl
text= Votre énoncé comme d'habitude
good==# une chaine multiple avec une bonne solution par ligne 
bonne1
bonne2
bonne3
==
bad==
mauvaise 1 
mauvaise 2
mauvaise 3
==
```





Vous créez deux listes dans votre before que vous utilisez pour initialiser votre question.
https://pl.u-pem.fr/filebrowser/demo/32803/

Essayez ce code.
```
extends = /model/checkbox/div3.pl

text= Cochez les réponses positives
before==
import random
good= ['yes','good','ok','da','Ney','dac','ouais']
bad= ['non','no','όχι','bad','worst','niet']
# 5 est le nombre de propositions
# le randint est le nombre de bonnes propositions 
checkbox.setdata_from_rw(good, bad, 5, random.randint(1, 4))
==
```
