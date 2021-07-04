# Mise en forme de l'énoncé

L'énoncé (contenu dans la clé `question`) peut être mis en forme avec des balises [Markdown](https://fr.wikipedia.org/wiki/Markdown) ou HTML. Le plus souvent, l'énoncé ne nécessite pas de mise en forme complexe et les balises Markdown sont suffisantes.


### Paragraphes

Pour faire un nouveau paragraphe, il suffit d'insérer une ligne vide. Un simple retour à la ligne n'a aucun effet sur le texte mis en forme, le texte reste continu. 

```
question ==
Premier paragraphe

Deuxième paragraphe 
==
```

### Italique, gras, verbatim

les balises `*`, `**` et <code>`</code> permettent respectivement d'obtenir de l'italique, du gras et du verbatim.

```
question ==
*texte en italique*

**texte en gras**

`verbatim`
==
```

### Listes

```
question ==
Liste non-ordonnée:

* Item
* Item
    * Item
    * Item
* Item

Liste ordonnée:

1. Item
2. Item
3. Item
==
```
