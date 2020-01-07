# Question à choix multiples (plusieurs choix sélectionnables)

## Composant `CheckboxGroup`

Le composant `CheckboxGroup` permet de créer un champ de réponse à choix multiples avec un seul choix sélectionnable. La création du composant et son insertion dans la clé `form` se fait comme n'importe quel autre composant.

~~~
checkbox =: CheckboxGroup

form ==
{{ checkbox | component }}
==
~~~

La réponse de l'élève est évaluée grâce à la méthode `eval` du composant. Celle-ci renvoie... Par ailleurs, cette méthode modifie l'apparence du champ de réponse : les bonnes réponses cochées sont colorées en vert, les bonnes réponses non cochées sont encadrées en vert et les mauvaises réponses cochées sont colorées en rouge. Enfin, le composant est désactivé en mettant à `True` la valeur de l'attribut `disabled` : l'élève ne peut plus modifier les réponses cochées.

Le choix du barème se fait par l'attribut `grading`. Trois barèmes sont proposés.

!!! info
    `AllOrNothing` : renvoie un score de 100 si la réponse est parfaitement correcte (toutes les bonnes réponses sont sélectionnées, aucune mauvaise réponse n'est sélectionnée) et un score de 0 sinon.
    
    `CorrectItems` : renvoie le nombre d'items corrects (bonnes réponses sélectionnées et mauvaises réponses non sélectionnées) moins deux fois le nombre d'items incorrects, le tout ramené entre 0 et 100.
    
    `RightMinusWrong` : renvoie le nombre de bonnes réponses sélectionnés moins le nombre de mauvaises réponses sélectionnées, le tout divisé par le nombre total de bonnes réponses et ramené sur 100.
    
    
## Template checkbox.pl

~~~
extends = basic.pl

checkbox =: CheckboxGroup

settings.feedback.class = score

form ==
{{ checkbox | component }}
==

evaluator ==
grade = checkbox.eval()
checkbox.disabled=True
==
~~~


## Exemple 1 : Multiples de 3

Dans cet exemple, on demande à l'élève de sélectionner les multiples de 3 parmi une liste de nombres.

[Tester l'exemple](https://pl.u-pem.fr/filebrowser/demo/6926/)

On commence par créer un composant `CheckboxGroup`.

~~~
checkbox =: CheckboxGroup
~~~


~~~
before ==
import random as rd
mult3 = [str(n) for n in range(50,100) if n%3 == 0]
other = [str(n) for n in range(50,100) if n%3 != 0]
checkbox.loadRightWrong(mult3,other,5,rd.randint(1,4))
checkbox.grading="RightMinusWrong"
==
~~~
