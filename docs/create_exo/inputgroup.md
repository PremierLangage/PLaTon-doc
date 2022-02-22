# Exercices à plusieurs champs de réponse

Le modèle qui permet de fabriquer un exercice à plusieurs champs de réponse est le modèle `basic/inputgroup.pl`.

Chaque type de champ de réponse est associé à une classe Python :
- `Radio` : Choix multiple
- `Checkbox` : Choix multiple
- `TextInput` : Réponse textuelle
- etc.

Pour définir les champs de réponse de l'exercice, il faut créer dans le script `before` une liste `inputs` contenant des objets de type champ de réponse. Il faut ensuite configurer ces objets.

Par exemple, le script `before` suivant crée deux champs de réponse textuelle dont les solutions attendues dont `Paris` et `Rome`.
```
before ==
inputs = [TextInput(), TextInput()]
inputs[0].sol = "Paris"
inputs[1].sol = "Rome"
==
```

```
extends = /model/basic/inputgroup.pl

question ==
Quelles sont les capitales des pays suivants ?
==

before ==
inputs = [TextInput(), TextInput()]
inputs[0].sol = "Paris"
inputs[1].sol = "Rome"
==

inputblock ==
<div class="container">
  <div class="row py-2 align-items-center">
    <div class="col-md-auto">
        France :
    </div>
    <div class="col">
      {{ inputs[0]|component }}
    </div>
  </div>
  <div class="row py-2 align-items-center">
    <div class="col-md-auto">
      Italie :
    </div>
    <div class="col">
      {{ inputs[1]|component }}
    </div>
  </div>
</div>
==

```
