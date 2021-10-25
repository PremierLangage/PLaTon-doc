# *FROZEN_RESSOURCE*

Les ressources qui sont sur le server sont des données modifiables. Pour garder une version non mutables, on les stocke sous forme de frozen_ressource dans la sandbox.
On peut ainsi effectuer deux principales opérations : passer de données représentant une ressource donnée à une frozen-ressource et récupérer les informations d'une frozen ressource.

## *FROM RESSOURCE TO `FROZEN_RESSOURCE`*

Cette opération se fait par la fonction *post* (dans le fichier /sandbox/api_server/views.py) qui est chargée de réceptionner les données de la ressource et de les stocker en frozen_ressource dans la sandbox.

### Fonctionnement

1_ Elle  reçoit des données au format JSON.  
2_ Elle fait un hachage de ces données et les enregistre en base de données si elles ne sont pas présentes.  
3_ Elle renvoie un code `200` et la **FrozenResource** si tout s'est bien passé, un code `-1` et la **FrozenResource** si elle était déja présente.
   Si les données ne sont pas présentes ou ne sont pas au format Json, les codes d'erreur sont respectivement `-2` et `-3`.

## *RECEVOIR LES INFORMATIONS D'UNE FROZEN_RESSOURCE* 

Cette opération se fait par la fonction *get* (dans le fichier /sandbox/api_server/views.py) qui est chargée de renvoyer les données de la frozen_ressource demandée (identifiée par son id).

### Fonctionnement

1_ Elle Reçoit l'`id` d'une **FrozenResource** par url.  
2_ Elle renvoie la **FrozenResource** si cette dernière est présente, sinon renvoie un code d'erreur `-4`. 

## Clés spécifiques

- server
- frozen_ressource
- ressource
- JSON
