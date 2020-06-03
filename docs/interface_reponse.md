# Interface de réponse

L'interface de réponse est à définir dans la clé `form`. Pour faciliter la création de cette interface de réponse, la plateforme PLaTon propose une bibliothèque de composants web qui comprend de nombreux types de champs de réponse.


## Création d'un composant

Dans la syntaxe PL, un composant est un objet (au sens JSON) possédant une clé `cid` et une clé `selector`. La valeur de `cid` est un identifiant unique du composant tandis que la valeur de `selector` indique le type du composant. Par exemple, la ligne suivante définit un composant nommé `mycomponent`, de type `Input` et dont l'identifiant est `myid`.

```
mycomponent = {"cid": "myid", "selector": "c-input"}
```

Chaque type de composant possède un certain nombre de propriétés paramétrables.

```
mycomponent = {"cid": "myid", "selector": "c-input", "type": "number"}
```

L'opérateur `=:` permet de définir plus simplement les composants : il allège la syntaxe requise et s'occupe de générer aléatoirement l'identifiant du composant. Par exemple, la ligne suivante définit un composant nommé `mycomponent`, de type `Input`, avec un identifiant généré automatiquement.

```
mycomponent =: Input
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
