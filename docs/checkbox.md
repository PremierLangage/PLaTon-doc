# Question à choix multiples (plusieurs choix sélectionnables)

Le composant `CheckboxGroup` permet de créer un champ de réponse à choix multiples avec plusieurs choix sélectionnables. Il possède les méthodes suivantes :
    - `loaditems`
    - `loadrw`
    - `eval`
 
    
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

mult3 = [str(n) for n in range(10,100) if n % 3 == 0]
other = [str(n) for n in range(10,100) if n % 3 != 0]

checkbox.loadrw(mult3,other,5,rd.randint(1,4))
==
~~~

La réponse de l'élève est évaluée grâce à la méthode `eval` du composant. Celle-ci renvoie un score. Par ailleurs, elle affiche une correction visuelle.

~~~
evaluator ==
grade = checkbox.eval(grading="AllOrNothing")
==
~~~

Le choix du barème se fait avec l'option `grading`. Trois barèmes sont proposés.

!!! info
    `AllOrNothing` : renvoie un score de 100 si toutes les bonnes réponses sont sélectionnées et aucune mauvaise réponse n'est sélectionnée ; renvoie un score de 0 sinon.
    
    `CorrectItems` : renvoie le nombre d'items corrects (bonnes réponses sélectionnées et mauvaises réponses non sélectionnées) moins deux fois le nombre d'items incorrects, le tout ramené entre 0 et 100.
    
    `RightMinusWrong` : renvoie le nombre de bonnes réponses sélectionnés moins le nombre de mauvaises réponses sélectionnées, le tout divisé par le nombre total de bonnes réponses et ramené sur 100.
