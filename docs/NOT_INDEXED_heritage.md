# Héritage : templates et exercices à paramètres

La commande `extends` permet d'importer les clés d'un autre fichier `.pl`. 

## Templates

Dans l'exercice d'addition précédent, on 

On remarque que les deux premiers exemples d'exercices partagent un certain nombre de clés (choix du builder et du grader, champ de réponse). On imagine d'ailleurs que beaucoup d'autres exercices utiliseront cet ensemble de clés. Pour minimiser la duplication de codes, on peut donc placer ces clés dans un template `basicinput.pl`.

~~~
@ /utils/sandboxio.py
@ /builder/before.py [builder.py]
@ /grader/evaluator2.py [grader.py]

input =: Input

form ==
{{ input | component }}
==
~~~

Pour hériter des clés de ce template, il suffit ensuite d'utiliser la commande `extends`.

~~~
extends = /template/basicinput.pl

title = Addition

before ==
import random as rd
a=rd.randint(10,20)
b=rd.randint(10,20)
==

text ==
Calculer {{a}} + {{b}}.
==

evaluator ==
try:
    if int(input.value)==a+b:
        grade=(100,"")
    else:
        grade=(0,"%d + %d = %d" % (a,b,a+b))
except:
    grade=(-1,"Votre réponse n'est pas un nombre entier.")
==
~~~

!!!note
Un certain nombres de templates de base sont déjà disponibles dans le répertoire `lib/template/`.

## Exercices à paramètres

~~~
extends = /template/basicinput.pl

title = Addition

before ==
import random as rd
a=rd.randint(vmin,vmax)
b=rd.randint(vmin,vmax)
==

text ==
Calculer {{a}} + {{b}}.
==

evaluator ==
try:
    if int(input.value)==a+b:
        grade=(100,"")
    else:
        grade=(0,"%d + %d = %d" % (a,b,a+b))
except:
    grade=(-1,"Votre réponse n'est pas un nombre entier.")
==
~~~

~~~
extends = add_int_.pl

vmin % 10
vmax % 20
~~~

~~~
extends = add_int_.pl

vmin % 20
vmax % 40
~~~

