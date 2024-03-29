# Configuration de l'environnement de test Platon sur Postman

Postman est un outil très utile pour le développement d'application REST. 
Il permet d'éxecuter des requêtes HTTP depuis une interface graphique. 
Ces requêtes peuvent-être personnalisées (choix de la méthode http, les headers, les params etc...).

Platon fournit tout une suite de test pour d'effectuer des requêtes sur les api de l'application.
Dans cette documentation nous verrons comment mettre en place l'environnement de test Platon sur Postman.

## Fichiers essentiels 

Il faut tout d'abord récupérer trois fichiers JSON correspondant aux tests d'api du back-end, de la sandbox et des variables d'environnements (URL de base et token JWT)
* [platon](https://github.com/PremierLangage/PLaTon-doc/blob/master/postman_testing/PLaTon.postman_collection.json)
* [sandbox](https://github.com/PremierLangage/PLaTon-doc/blob/master/postman_testing/Sandbox.postman_collection.json)
* [variables d'environnements](https://github.com/PremierLangage/PLaTon-doc/blob/master/postman_testing/platon_variables.postman_environment.json)

## Import des fichiers

Pour importer des fichiers : ``import -> file -> upload files `` et sélectionner les trois fichiers JSON que vous venez de télécharger. 

## Activation des variables d'environnements

Dans l'onglet collection, cliquer sur Platon_local et cocher toutes les variables d'environnements.
