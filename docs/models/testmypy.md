
# (doc)Tester vote code python 

Quand on programme sérieusement en python on utilise des doctest pour controler que l'on écrit bien ce que l'on souhaite écrire ...

Quand vous mettez au point un fichier outils contenant du python il est pénible de naviguer de votre ordinateur à PLATON. 
Nous avons prévu dans un prochain deployement de vous proposer une commande permettant de lancer un doctest sur un fichier python de la plateforme.
Mais pour le moment Nous utiliserons le modèle d'exercice **test my Py** pour tester notre code.

Supposons que vous souhaitez tester votre fichier */AAAA/chermoi/moncode.py*, alors créez le fichier testeur.pl suivant 

```
extends = /utils/python/exemple_testmypy.pl
@ /AAAA/chermoi/moncode.py [code.py]
```
La preview de cet exercice vous affichera l'exécution des tests sur votre fichier .
