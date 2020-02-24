# Exercice au format gift

Le format GIFT permet d'utiliser un éditeur de texte pour écrire des questions à choix multiple :
    - `vrai ou faux`
    - `réponse courte
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

Les réponses doivent commencer par "{" et finir par "}"
~~~
::Titre::Énoncé à écrire ici.{Réponses possibles à écrire ici}
~~~

##  Les types de questions :

### Vrai ou faux

La réponse indique si une proposition est vraie ou fausse.
possibilité d'ecrire : {TRUE}  {FALSE}  ou  {T} ou {F}. 
~~~
::Question 1 :: le soleil se lève à l'est.{T}

::Question 2 ::le soleil se lève à l'ouest .{FALSE}
~~~


### Réponse courte
Format qui permet de définir plusieurs bonnes réponses pour une questions donnée
~~~
Deux plus deux égalent {=quatre =4 =IV}
~~~

### Choix multiple
Pour les questions à choix multiple, les mauvaises réponses sont précédées d'un tilde (~) et les bonnes réponses sont précédées d'un symbole d'égalité (=). 
~~~
Qui repose dans la Grant's tomb ? {=Grant ~Personne ~Napoléon ~Churchill ~Mère Teresa}
~~~
Choix multiple avec plusieurs bonnes réponses en précisant le pointage (positif ou négatif)
~~~
Qui sont les deux personnes qui sont enterrés dans la Grant's tomb ? {
~%-50%Personne
~%50%Grant
~%50%L'épouse de Grant
~%-50%Le père de Grant
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







