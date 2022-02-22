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

La disposition des champs de réponse dans la page de l'exercice est définie dans la clé `inputblock` par du code HTML.

```
inputblock ==
<div style="display:flex; align-items: center; margin-bottom: 1em;">
  <div> France : </div>
  <div style="margin-left: 1em;"> {{ inputs[0]|component } }</div>
</div>
<div style="display:flex; align-items: center; margin-bottom: 1em;">
  <div> Italie : </div>
  <div style="margin-left: 1em;"> {{ inputs[1]|component }} </div>
</div>
==
```
