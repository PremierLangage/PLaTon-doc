
# Associations 

Exercice d'association de pairs. 

[![](match.png)](https://pl.u-pem.fr/filebrowser/demo/32826/)


Un premier modèle qui utilise le caractère '§' pour séparer les élèments des pairs.

```
extends = /model/matchlist/matchlist.pl

pairs ==
Nourriture pour chat§chat
Nourriture pour chien§chien
Nourriture pour oiseaux§oiseaux
==

text = Associez les bons annimaux aux bonnes nourritures  

title = Nourrire vos animaux 
```

Bien entendu vous pouvez utiliser un script dans la balise **before** pour produire votre liste de paires. 

[Un exemple sur les dérivées](https://pl.u-pem.fr/filebrowser/demo/32908/)

```
author=DD and DR
extends= /model/math.pl
extends= simplematchlist.pl

before==

var('x')

f=[sin(x),cos(x),x**2,x**3, log(x)/log(2), exp(x),127]
gf=[ f"$!{latex(fi)}!$" for fi in f]
df=[  f"$!{latex(diff(U,x))}!$" for U in f]

pairs= [ TT for TT in zip(gf,df)]

# Dans une version future les lignes suivantes ne seront plus nécessaires 
if type(pairs)==list:
    matchlist.setdata_from_matches(pairs)
else:
    if "delimiter" not in globals():
      delimiter='§'
    # ne prend que les lignes avec un délimiter et construit une paire avec la chaine.
    matchlist.setdata_from_matches([ l.split(delimiter) for l in  pairs.splitlines() if delimiter in l ])

==

text==
Associez chaque fonction à sa dérivée.
==

```



Un deuxième modèle qui utilise le caractère définie par la balise **delimiter** pour séparer les élèments des pairs.

A venir.
