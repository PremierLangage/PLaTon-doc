# Question à choix multiples (avec plusieurs bonnes réponses)

Basé sur le composant `CheckboxGroup`.

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
mult3 = [n for n in range(50,100) if n%3 == 0]
other = [n for n in range(50,100) if n%3 != 0]
nchoices = 5
nright = rd.randint(1,nchoices-1)
choices = rd.sample(mult3,nright)+rd.sample(other,nchoices-nright)
checkbox.loadContent([str(number) for number in choices])
checkbox.setSolByIndex(list(range(nright)))
checkbox.shuffle()
checkbox.grading="RightMinusWrong"
==
~~~



La réponse de l'élève est évaluée grâce à la méthode `eval` du composant. Celle-ci renvoie... Par ailleurs, cette méthode modifie l'apparence du champ de réponse : les bonnes réponses cochées sont colorées en vert, les bonnes réponses non cochées sont encadrées en vert et les mauvaises réponses cochées sont colorées en rouge. Enfin, le composant est désactivé en mettant à `True` la valeur de l'attribut `disabled` : l'élève ne peut plus modifier les réponses cochées.

~~~
evaluator ==
grade = checkbox.eval()
checkbox.disabled=True
==
~~~

## Template `checkbox.pl`

~~~
extends = basic.pl

checkbox =: CheckboxGroup

form ==
{{ checkbox | component }}
==

evaluator ==
grade = checkbox.eval()
checkbox.disabled=True
==
~~~
