# Liste à ordonner

Le composant `SortList` permet de créer une liste à ordonner. Il possède les méthodes suivantes :
    - `loadlist`
    - `eval`

## Exemple

~~~
before ==
import random as rd

numbers = rd.sample(list(range(1,100)),5)
numbers.sort()

sortlist.loadlist([str(n) for n in numbers])
==
~~~

~~~
evaluator ==
grade = sortlist.eval()
==
~~~
