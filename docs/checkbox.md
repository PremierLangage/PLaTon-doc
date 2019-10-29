# Question à choix multiples (avec plusieurs bonnes réponses)

Basé sur le composant `CheckboxGroup`.

## Exemple 1 : Multiples de 3

[Tester l'exemple](https://pl.u-pem.fr/filebrowser/demo/6898/)

On commence par créer un composant `CheckboxGroup`.

~~~
checkbox =: CheckboxGroup
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
