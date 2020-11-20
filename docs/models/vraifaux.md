
# Vraie ou fausse

Tester une affirmation au près de vos étudiants.

[![image](./VF.png)](https://pl.u-pem.fr/filebrowser/demo/32678/)



Le code de l'exemple 
```
extends = /model/basic/vraifaux.pl

title= Un exemple de proposition vraie ou fausse 

text==
Le cheval blanc de Henri IV est il blanc ? 
==


answer=Non


# pour aligner les proposition 
horizontal % true 

feedback_correct ==
Bien vu il est gris car il s'est roulé dans la poussière.  
<img src="https://upload.wikimedia.org/wikipedia/commons/a/a8/Lol_LOL.png">
==
feedback_wrong = Il vous manque des informations.
general_feedback==



Bien entendu c'est une question piège.
==

```
