# Interface de réponse

L'interface de réponse est à définir dans la clé `form`. Pour faciliter la création de cette interface de réponse, la plateforme PLaTon propose une bibliothèque de composants web qui comprend de nombreux types de champs de réponse.

Voilà la liste des composants implémentant les champs de réponse de base.
- **Input** : champ de réponse textuel ou numérique
- **Radio Group** : champ de réponse à choix multiples avec un seul choix sélectionnable
- **Checkbox Group** : champ de réponse à choix multiples avec un seul choix sélectionnable
- **Match List** : éléments à mettre en correspondance
- **Sort List** : liste à ordonner
- **Drag & Drop** : étiquettes à placer
- **Text Select** : unités à sélectionner dans un texte

## Création d'un composant

Dans la syntaxe PL, un composant est un objet (au sens JSON) possédant une propriété `cid` et une propriété `selector`. La valeur de `cid` est un identifiant unique du composant tandis que la valeur de `selector` indique le type du composant. Par exemple, la ligne suivante définit un composant nommé `mycomponent`, de type `Input` et dont l'identifiant est `myid`.

```
mycomponent = {"cid": "myid", "selector": "c-input"}
```

L'opérateur `=:` permet de définir plus simplement les composants. Par exemple, la ligne suivante définit un composant nommé `mycomponent`, de type `Input`, avec un identifiant unique généré automatiquement.

```
mycomponent =: Input
```

## Paramétrage d'un composant

Chaque type de composant possède un certain nombre de propriétés paramétrables. Par exemple, le composant `Input` possède une propriété `type` qui peut prendre la valeur `"text"` ou `"number"`.

```
mycomponent =: Input
mycomponent.type = "number"
```

## Insertion d'un composant dans l'interface de réponse

```
form ==
<c-input cid="mycid"> <c-input/>
==
```

Pour rendre plus simple et plus lisible l'insertion des composants, l'environnement Jinja utilisé pour la mise en forme des clés dispose d'un filtre `component`. Ce filtre permet d'insérer un composant en indiquant simplement son nom.

```
form ==
{{ mycomponent|component }}
==
```
