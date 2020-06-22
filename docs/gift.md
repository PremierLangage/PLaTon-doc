# Exercice au format gift

Le format GIFT permet d'utiliser un éditeur de texte pour écrire des questions à choix multiple :
    - `vrai ou faux`
    - `réponse courte`
    - `choix multiple`
    - `mot manquant`
    - `Appariement`
    - `réponse numérique`
  
    
##  Titre, énoncé, champ de réponse

Le `titre` doit etre écrit entre "::"

~~~
::Titre::
~~~

L'énoncé est le texte qui est écris après le titre.
~~~
::Titre::Énoncé à écrire ici.
~~~

Les réponses doivent étre écrites entre  "{" et  "}"
~~~
::Titre::Énoncé à écrire ici.{Réponses possibles à écrire ici}
~~~

##  Les types de réponses :

### Vrai ou faux

La réponse indique si une proposition est vraie ou fausse.
possibilité d'ecrire : {TRUE}  {FALSE}  ou  {T} ou {F}. 
~~~
::Question 1 :: TODOO.{T}
::Question 2 ::TODO .{FALSE}
~~~


### Réponse courte
Format qui permet de définir plusieurs bonnes réponses pour une questions donnée
~~~
TODOO
~~~

### Choix multiple
Pour les questions à choix multiple, les mauvaises réponses sont précédées d'un tilde (~) et les bonnes réponses sont précédées d'un symbole d'égalité (=). 
~~~
TODOO
~~~
Choix multiple avec plusieurs bonnes réponses en précisant le pointage (positif ou négatif)
~~~
TODOO
}
~~~


### Mot manquant
Le format mot manquant insère automatiquement un trou au milieu d'une phrase.
Pour utiliser le format mot manquant, mettez les réponses où vous voulez qu'un trou se crée dans le texte.
~~~
::Question 1::todo
~~~

###  Appariement
Les différents appariements commencent par un symbole d'égalité (=) et sont séparés par ce symbole « -> »
~~~
::Question 1 ::Appariez les pays suivants avec les capitales correspondantes. {
   =Canada -> Ottawa
   =Italie -> Rome
   =Japon -> Tokyo
   =Inde -> New Delhi
}
~~~

### Réponse numérique 
La section réponse pour les questions à réponse numérique doivent commencer par un dièse (#)
`Marge d'erreur : ` avec le signe  ":"
~~~
::Question 1::Quelle est la valeur de pi (incluant 3 chiffres après la virgule) ? {#3,14159:0,0005}.
}
~~~
`Valeur minimale et maximale : ` avec le signe  ".."
~~~
::Question 1::Quelle est la valeur de pi (incluant 3 chiffres après la virgule) ?{#3,141..3,142}.
}
~~~
Les questions à réponse numérique ayant plusieurs réponses numériques
~~~
::Question 1::En quelle année est né Ulysses S. Grant ? {#
=1822:0
=%50%1822:2
}
~~~
## Feed-back

### Rétroaction 
Une rétroaction peut être incluse pour chaque réponse en plaçant un dièse à la suite de la réponse (#) suivi de la rétroaction. 
~~~
Quelle est la réponse à cette question à choix multiple ? {
~Mauvaise réponse#Rétroaction pour cette mauvaise réponse
~Autre mauvaise réponse#Rétroaction pour cette autre mauvaise réponse
=Bonne réponse#Très bien !
}
~~~

### Feed-back général

Le feed-back général peut être inclus pour chaque question en plaçant 4 dièses à la suite avant la parenthèse finale. 
~~~
::Question 1::Quelle est la réponse à cette question à choix multiple ? {
~Mauvaise réponse
~Autre mauvaise réponse
=Bonne réponse
####Feed-back général pour toute réponse donnée à cette question.
}
~~~

### Editer un fichier 

Pour editer un fichier il faut:
    - `créer un nouveau fichier sur l'éditeur`
    - `écrire l'ensemble des questions au format gift sur ce nouveau fichier `
    - `enregistrer le fichier avec l'extension .gift`
    
 Pour visualition les exercices au formation pltp il faut lancer les exercices avec le bouton play.
 Ensuite les fichiers contenant les exercices au format pltp seront créer.






