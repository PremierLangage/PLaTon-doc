# Question à choix multiples (plusieurs choix sélectionnables)

## Composant `CheckboxGroup`

Le composant `CheckboxGroup` permet de créer un champ de réponse à choix multiples avec plusieurs choix sélectionnables. Des méthodes Python (utilisables dans les scripts `before` et `evaluator`) facilitent la manipulation de ce composant.

  * `setitems` : définit la liste des choix.
  * `setsol_from_index` : définit les solutions à partir de leurs indices dans la liste des choix.
  * `setsol_from_content` : définit les solutions à partir de leur contenu.
  * `setdata_from_right_wrong` : définit la liste de choix et les solutions à partir d'une liste de bonnes réponses et d'une liste de mauvaises réponses.
  * `shuffle` : mélange la liste des choix.
  * `sort` : trie la liste des choix par ordre alphabétique.
  * `eval` : évalue la réponse de l'élève (en comparant eux solutions préalablement définies) et affiche éventuellement une correction visuelle.
 
    
## Exemple : Multiples de 3

Dans cet exercice, on demande à l'élève de sélectionner les multiples de 3 parmi une liste de nombres. Les données sont générées aléatoirement.

[Tester l'exemple](https://pl.u-pem.fr/filebrowser/demo/6926/)

On commence par hériter du modèle d'exercice `basic.pl`.

~~~
extends = /model/basic.pl
~~~

On crée un composant de type `CheckboxGroup` qu'on appelle `checkbox`.

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
