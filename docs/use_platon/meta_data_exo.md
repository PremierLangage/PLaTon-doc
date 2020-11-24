# Soigner les méta données de ses productions

Pouquoi le faire ?

* Faciliter l'**indexation** de vos productions.
* Permettre des **recherches** plus performantes sur la base de données.
* Augmenter la **réutilisabilité** de vos productions.
* Favoriser l'amélioration et la **curation** de vos productions.
* Permettre de sous traiter le maintiens de vos productions à une **communuté**.
* Expliciter vos intentions et votre **stratégie pédagogique**.
* ...

Tout le monde gagne à avoir des ressources bien renseignées en termes de 
meta données, pas seulement vous.

# Qu'est ce que c'est que ces méta données ?

**Réponse rapide :** C'est des informations pédagogiques contextuelles pour
permettre à la plateforme **PLaTon** d'être plus intelligente.

Un exercice contient bien sûr un minimum d'information pour être fonctionnel 
avec les apprenants : un énoncé ou des consignes, une zone de réponse et
une manière de noter (souvent plus dans les faits). Une fois un exercice 
fonctionnel, tenttez de vous mettre dans la peau d'un collègue qui
tomberait par hasard sur votre fichier. 

Pour faciliter la compréhension, le pourquoi et le comment de votre 
exercice, mettez-y des métas données. Parmi les informations les
plus cruciales

* Qu'attendez vous vraiment des élèves ?
* Pour quel niveau ou type de promotion cet exercice est-il adapté ?
* Cette exercice est-il simple ou complexe ?
* Quel acquis d'apprentissage visez-vous avec l'exercice ?
* Quels sont les notions que l'apprenant travaille avec cet exercice ?
* L'exercice a-t-il des faiblesses identifiés ?
* ... toute information qui conseilleraient un collègue ...


# Où sont et où mettre les méta données ?

Les méta données sont renseignées dans certaines clés bien identifiées : 

`title` : Le titre de l'exercice. Soyez précis dans les titres et évitez 
absolument les titres du genre `Exercice 1`. Les mots dans les titres sont
des mots clés qui pèsent lourd dans les recherches.

`author` : L'auteur originel donne souvent beaucoup d'information sur les
motivations derrière l'exercice. Outre connaitre l'utilisateur à contacter
en cas d'interrogation, mettre votre nom permet de vous renseigner comme
un ayant droit sur les ressources pédagogiques. Ainsi **PLaTon** est
pérénisé comme un projet ouvert et public.

`text` : L'énoncéd'un exercice contient souvent de nombreux mots dans la
langue de l'exercice, ces mots sont aussi des méta données potentielles.

`tag` : une liste de mots clé, plutôt orienté notion séparé par des barres
verticales (appelé caractère pipe `|`). Voici un exemple où l'exercice
original demandait à l'apprenant de compter les étiquettes paires d'un
arbre binaire.

    tag=arbre|algo|récursivité|parité|étiquette|entier

`cercle` : à venir (version 1.0)

`aav` : à venir et à discuter avec les enseignants

... surement plus à venir ...

Des commentaires dans vos fichier peuvent être aussi considérés comme
des méta données. Consignez et prendre le temps d'écrire tout ce qui 
vaut le coup d'être consigné est une saine pratique.

Comme **PLaTon** est un jeune projet, l'état de l'art des méta données évolue
encore avec l'apparition de nouvelles fonctinnalité.
