# Présentation de Premier Langage

Pourquoi ? Comment ? Et dans quels objectifs !

## Un nouvel environnement pédagogique

Premier Langage est une plateforme d'exercices en ligne en développement. Il utilise 
des technologies modernes pour permettre la mise en œuvre d'enseignements assistés par 
ordinateur. Nous avons prévus toutes sortes de situations d'apprentissage : avec ou sans encadrement,
à l'école ou à la maison, sur un ordinateur, un téléphone ou encore une tablette. Premier langage
se veut aussi une plateforme ouverte où la collaboration et le partage facilite le travail des 
enseignants et leur permet de faire monter la qualité des ressources pédagogiques.


## Constat et naissance de Premier Langage

Premier Langage est né en 2017 à l'université de Marne la Vallée à l'initiative de Dominique 
Revuz, maître de conférence en informatique à l'U.P.E.M. Partant du Constat qu'une trop large partie du temps
de l'enseignant, dans les premières années à l'université, consiste à répeter les
mêmes remarques pour les mêmes erreurs durant les travaux dirigés et travaux pratiques. Il se demande
alors comment automatiser cet encadrement à la fois important, utile mais 
terriblement prévisible. En tant qu'informaticien, il est naturel de scripter et d'automatiser les 
choses simples pour se concentrer sur les choses "évoluées". Il constitue également à l'augmentation contante des étudiants inscrits dans les filières informatiques de L'U.P.E.M., il fallait concevoir
un outil adapté.


## Des technologies déjà présentes

A notre connaissance, nous n'avons pas constaté l’existence d'une plateforme généraliste pouvant
à la fois s'interconnecter avec les outils standards (comme Moodle, Apogé, ...) mais surtout
tenir la charge de connexion en pouvant exécuter du code potentiellement dangereux fournis par les
apprenants. Il existe déjà quelques plateformes mais elles présentent toutes des défauts
et les adapter est soit techniquement impossible, soit ont un coût de 
développement similaire à repartir à zéro tout en gardant les handicaps des choix achitecturaux. Après quelques prototypes et expériences, des choix technologiques profonds sont apparus comme naturels :

* Python : le langage de programmation généraliste devenant référence dans l'enseignement (et uniquement dans les filières informatiques).  
* Django : pour la plateforme web. Rapide, simple, s'articulant avec Python et pouvant facilement tenir 
  la charge.  
* Docker : pour le déploiement, les machines virtuelles et la sécurité.  
* L.T.I. : Learning Tools Interoperability, pour le coté intégration et interopérabilité[^1] avec les outils
  existants des enseignants.  

Certains sites internet savent déjà exécuter de manière sécurisée des bouts de code soumis par les visiteurs, 
mais ces plateformes ne sont pas ouvertes à une école ou une université. L'authentification, le contrôle
et la sécurisation des données sont aussi des points que les structures d'enseignement françaises ne
peuvent pas ignorer.
Une plateforme raisonnable et pérenne doit rester sous le contrôle des enseignants utilisateurs.


## Modèle de partage

En plus d'un outil praticable, PL souhaite économiser du temps de travail pour les enseignants éditeurs
de ressources. L'objectif est donc de mettre en place des outils et pratiques favorisant les 
corrections, les améliorations et la réutilisation de manière générale. Toutes les sources d'informations
pédagogiques sont bonnes, c'est l'interopérabilité[^1] qui est difficile. Premier Langage incite au partage des
ressources pédagogiques et à leur structuration en termes de réutilisabilité. Ainsi, un énoncé spécifique
pourra utiliser un moteur générique pour dessiner une courbe et un programme de correction automatique
provenant d'une autre technologie. Pourvu que la courbe soit belle, l'enseignant en mathématique
préféra ce concentrer sur son énoncé et la formulation de ses questions plutôt que sur l'utilisation
de l'application JSXGraph dessinant les courbes et sur la programmation en Scipy pour programmer la 
correction automatique. PL propose des outils génériques à plusieurs niveaux, des outils extrêmement
généraux comme les QCM mais aussi des outils spécifiques à une matière comme un compilateur de code en
langage C.

Le modèle de mise en partage est toujours en phase de design mais l'objectif est de permettre à la fois 
à tout enseignant de pouvoir contribuer mais aussi de pouvoir réutiliser 
l'existant. Aussi, une telle technicité est d'ordinaire assuré en interne par des systèmes gestionnaires 
de versions dont l'utilisation est trop technique et trop lourde pour un enseignant. Nous élaborons
toujours une stratégie pour remplir cet objectif d'ouverture et de partage dans la simplicité.


## Objectifs sur le long terme

Sur le long terme, Premier Langage espère proposer un cadre robuste pour le déploiement de vos situations
pédagogiques. Premier Langage ne souhaite pas se spécialiser vers l'informatique ou les mathématiques. Le 
travail technique étant compliqué et coûteux. Si la montée en charge et la sécurité sont toutes deux garanties, 
Premier Langage espère pouvoir héberger toutes ressources issues de n'importe quel domaine. 

Premier Langage souhaite monter en fonctionnalité de suivi et pilotage pédagogique, des choses qui sont lourdes à
développer mais qui peuvent profiter à tout enseignant quel que soit la matière enseignée :

* Identification automatique des élèves en difficulté ou en retard. **Tableaux de Bord[^2]**.
* Statistiques sur les ressources pédagogiques proposées.  **Module de Stats**.
* Retour et conseil auto-généré pour permettre aux élèves d'appréhender la quantité et qualité de leurs 
  travaux par rapport à leur camarade, par rapport à ce qui est attendu.  **Recommandation**.
* Identification des lacunes de manière personnalisé. **Analyse Didactique** 
* Recommandation de ressources identifiées comme pédagogiquement performantes suivant les profils.  **Recommandation**.
* Construction de parcours de formation et adpatation, auto-construction de sa formation, **AAV, Design & Compose** 
* Un outil en mode **Saas** accessible de partout permettant  **partage** et **sécurité**.
* Une unique plateforme pour la création de **Cercles/communautés/équipes** pédagogiques et didactiques.

Aujoud'hui, dans de nombreuses formations, les enseignants ne sont pas assez nombreux pour pratiquer des 
suivis individualisés réguliers. Les retours à la fois automatisées et performants sont extrêment 
difficiles à concevoir mais sont possibles. Nous pensons que la stratégie de partage de Premier Langage
facilitera leur élaboration.


## Entrer dans Premier Langage

Si la philosophie et les technologies de Premier Langage vous
plaisent, [n'hésitez pas à nous rejoindre](contribuer.md) ! Pour
apprendre à utiliser premier langage, la prochaine étape consiste à
voir comment fabriquer un exercice minimal en consultant le premier
tutoriel.





[^1]: 
    Compatibilité des équipements, des procédures ou des organisations permettant à plusieurs systèmes, forces armées 
    ou  organismes d'agir ensemble : Interopérabilité des forces de l'OTAN.

[^2]: 
    Les tableaux de bord permettent à l'enseignant de visualiser les informations de sa classe d'un seul coup d'oeil. 
