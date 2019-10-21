
# Questions à Choix Multiples

Les questions a choix mulitples de la plateforme sont aléatoires vous spécifiez 
le nombre de proposition et le nombre de réponse exactes souhaités.

Pour choisir le template comme toujours la balise **extends** qui nous permet ici de choisir le template d'exercice de QCM.

      extends=/ComputerScience/python/template/qcm_template.pl

Un titre (**title**) comme dans tout les exercices

      title= Exemple de QCM

Vous pouvez changer le texte de l'énoncé dans la balise **text**.

      text= Cochez les affirmations correctes.

Voici deux balises spécifiques aux qcm **nb** et **nbtrue**

      # Nombre de proposition au total par défaut toutes les valeurs de **good** et **bad**
      nb=4
      # Nombre minimal de lignes "vraies" (qu'il faut cocher pour faire une bonne réponse) 
      nbtrues=2
      # si nbtrues==0 un nombre aléatoire entre 1 et nb
      # si pas défini un nombre aléatoire de réponses à cocher

La liste des réponses qu'il faut cocher

      good==
      La Lune tourne
      0 est plus petit que 1 
      Mars est dite: la planète rouge 
      le sucre est blanc
      le cheval blanc de Henri VI est blanc
      ==

Le délimiteur par défaut est linefeed vous pouvez le modifier :

      delimiter = $

Le separator par défaut est le pipe | il permet d'ajouter un feed back si la réponse est fausse. 

      bad==
      La terre est plate | vous exagerez  
      Le soleil tourtne autour de la terre 
      Les satellites de la lune sont rouges.
      1 est plus petit que 0

      ==

      before==

      bad+=" Très mauvaise affirmation"
      good += "\n celle ci est bonne par contre "
      ==

      feedback=show
