# Question à choix multiples (radio)

## Premier exemple

On commence par créer un composant `RadioGroup`.

~~~
radio =: RadioGroup
~~~

On tire une liste 4 nombres au hasard entre 0 et 49. Avec la méthode `loadContent`, on charge cette liste de choix dans le composant.

~~~
before ==
import random as rd
numbers=rd.sample(list(range(50)),4)
radio.loadContent([str(item) for item in numbers])
sol = min(numbers)
radio.setSolByContent(str(sol))
==
~~~

~~~
text ==
Sélectionner le plus petit nombre.
==

form ==
{{ radio|component }}
==
~~~

~~~
evaluator ==
grade = radio.eval()
radio.disabled=True
==
~~~
