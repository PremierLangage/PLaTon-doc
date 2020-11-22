
# Présentation sous Platon 

Ceci est un POC (proof of concept).

Si vous penser que c'est important il faut voter sur l'ISSUE https://github.com/PremierLangage/Yggdrasil/issues/97

Une Démo :
https://pl.u-pem.fr/filebrowser/demo/32800/

Il suffit de créer pour votre présentation XXX.md un fichier pl comme ceci :

```
extends= /model/markdown/slideshow.pl
@ XXX.md [slides.md]
```

!!! Rappel: extends permet de définir le modèle à utiliser 
   Le caractère @ permet d'ajouter le fichier XXX.md dans l'environement sous le nom slides.md
