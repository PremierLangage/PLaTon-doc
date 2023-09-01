Les enseignants utilisent **PLaTon** dans le cadre de deux grandes activités principales:  


- **L'édition de ressources pédagogiques partagées** ainsi que la curation de des dernières.
  Sur le serveur central de ressources, vous participez à l'édition des exercices, activités 
  ou cours. Durant cette activité, vous prenez le rôle de contributeur éditeur de ressources.   


- **Le déployment et la maintenance de ressources pédagogiques PLaTon dans le cadre d'un cours.**
  Sur un serveur d'asset (le serveur d'asset de votre institution éducative le cas échéant), 
  vous avez selectionné des ressources que vous soumettez à vos élèves dans le cadre d'un cours.
  Durant ce déployment, vous monitores et surveillez l'activité de vos élèves. Vous maintenez et
  enrichissez dans le temps les ressources déployés pour vos élèves. Durant cette activité, vous
  prenez le rôle d'enseignant sous PLaTon (soit vous réutilisez, soit vous êtes vous-même auteur 
  des ressources déployées, ou encore un mélande des deux...).


# Installer un serveur

Pour utiliser **PLaTon**, il faut avoir accès à un serveur avec **PLaTon** d'installé et 
quelques sandbox opérationnelles. Peut-être vous avez la chance d'avoir un service 
informatique dédié dans votre institution alors nous vous conseillons de leur transmettre
un lien vers cette page. Installer un serveur est une tâche plutôt adaptée pour les 
informaticiens avancés. 

**prérequis :** Un LMS ( voir [[lms]] ) utilisant le protocole LTI ( voir  [[lti]] )

* [Installer un serveur PLaTon](install_platon.md) pour votre institution.

# Connecter votre LMS à Platon 

Pour connecter votre LMS à au serveur platon Eiffel il faut demander une paire clef,password à dominique.revuz (at) univ (-) eiffel.fr.
Titre du message CLEF-PLATON. 
Sinon il faut définir dans l'interface administrateur de votre installation platon vos propre identifiants. 

## Le cas moodle

Dans un cours ou vous souhaiter ajouter des feuilles d'exercices platon. 
En mode Edition ajouter un "outil externe". 
Précisez l'URL de votre serveur Platon. 
Précisez le couple d'identifiants. 
Et voila !
à la Première connection le cours platon sera créer.






# Création et édition de ressources 

Voici une introduction rapide sur les types de ressources actuelles. Toutes les grandes 
sections restantes de cette documentation sont justement focalisées sur l'édition 
de ressources. Les trois pages qui suivent vous présenteront l'éditeur de ressources,
feront une introduction au vocabulaire autour des exercices et des activités **PLaTon**
et présenteront des conseils pour structurer et insérer efficacement dans la base de 
données vos travaux.

* [L'éditeur de ressources intégré](editor.md) 
* [Les exercices et les TP](pl_pltp.md)
* [Soignez les méta-données des ressources](meta_data_exo.md)


# Déployements en classes

* [Notion de classe](crudclasse.md) dans la plateforme **PLaTon**.
* [TODO : Comment déployé le premier `pltp` d'un cours ?]()
* [TODO : Ajouter des `pltp` à un cours existant dans **PLaTon** ?]()
* [TODO : Manager son cours]() en termes de contenus, de visibilité, d'avancement et d'extraction des notes.


# PLaTon version 1.0

Pour le moment les trois activités suivantes sont en cours de conception. 

* [TODO : Le Search&Compose](), outil pour composer graphiquement ses contenus 
pédagogiques à partir de la base de données.
* [TODO : Comment instancier une ressources vers un serveur d'asset]() nouveau mode
de déployement des ressources de la prochaine version.
* [TODO : Manager en continu les contenus des cours]() nouveau mode d'édition et
de management des assets déployés.

