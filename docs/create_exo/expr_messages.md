# Modifier les informations de correction

Il existe deux types d'informations de correction :

* les messages d'avertissement et d'erreur ;
* la solution détaillée.

## Messages d'avertissement et d'erreur

Les messages d'avertissement et d'erreur sont définies dans la clé `message`. Cette clé prend la forme d'un dictionnaire où chaque message d'avertissement ou d'erreur est associé à un code.

| Code | Message prédéfini |
|:-------- | :--------|
|`NotExpr`|La réponse doit être une expression mathématique.|
|`NotRatSimp`|L'expression peut encore être simplifiée.|
|`NotEqual`|La réponse n'est pas égale à la solution.|

Pour modifier un message d'avertissement ou d'erreur, il suffit donc de modifier la valeur associée au code correspondant dans la clé `message`.

```
message.NotEqual = "La réponse n'est pas une primitive."
```

## Solution détaillée

La solution détaillée est définie dans la clé `solution`.

Pour modifier la solution détaillée, il suffit de redéfinir la clé `solution`.

```
solution ==
Une primitive de la fonction $! f !$ est {{ sol|latex }}.
==
```
