# Mise en forme de l'énoncé

L'énoncé (contenu dans la clé `question`) peut être mis en forme avec des balises [Markdown](https://fr.wikipedia.org/wiki/Markdown) ou HTML. Le plus souvent, l'énoncé ne nécessite pas de mise en forme complexe et les balises Markdown sont suffisantes.

En Markdown, pour faire un nouveau paragraphe, il suffit de laisser une ligne vide avant ce nouveau paragraphe. Un simple retour à la ligne n'aura aucun effet à l'affichage (l'affichage sera en continu). 

```
question ==
Premier paragraphe

Deuxième paragraphe 
==
```

```
question ==
*texte en italique*

**texte en gras**

`verbatim`
==
```

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
