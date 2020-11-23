# Termes techniques et notions dans PLaTon


À la fois index et Lexique, cette page a vocation à recenser les clés et termes importants utilisés
dans les ressources de Premier Langage. Si vous programmez de nouvelles ressources, en imaginant de nouveaux
templates ou en définissant de nouvelles clés, il vous sera demandé de mettre cette page à jour. La description
des items présents n'est pas forcement complète ; il vous faut surtout résumer rapidement le rôle d'une clé et 
de sa valeur ou encore décrire rapidement les termes et notions relatif à Premier Langage. C'est une page de
documentation pour les gens pressés mais aussi un point d'entré vers d'autres pages de documentation.


## author

author est le nom de la `clé` à définir dans les **fichiers ressources** d'extension `pl`
pour renseigner l'auteur original d'un document. Ainsi, si vous vous appelez Dominique Revuz, 
pour informer les futurs utilisateurs et relecteurs que vous avez produit un fichier, 
une pratique saine consiste à y placer la ligne :

    author=Dominique Revuz

Spécifier un auteur et une licence (CC-By-SA 3.0 est un excellent choix de licence) est 
important pour assurer la pérennité du projet **PLaTon**.


## before

Losqu'une ressource utilise le [builder `before`](before.md), elle doit alors absolument 
définir une clé `before`. Cette balise, souvent sur plusieurs lignes, devra contenir un 
petit script Python exécuté une seule fois à la construction. Pour utilisez cette clef il faut avoir la ligne 
```
@ /builder/before.py [builder.py]
```

## builder

Le builder est un programme python exécuté avant que l'exercice soit proposé à l'apprenant.
Le builder sert à rendre les exercices plus dynamiques notament en y insérant des parties
aléatoires.
Sans builder déclaré dans une ressource, l'étape de construction ne modifie pas l'exercice. 


## code_before

Dans le template `std_progC.pl`, `code_before` est utilisé pour inclure du code avant le code
réponse proposé par l'apprenant. Si par exemple, l'exercice en C demande d'écrire une fonction
utilisant une nouvelle structure `Node`, alors pour une bonne compilation, la définition de cette 
structure doit être insérer avant le code rendu par l'apprenant. `code_before` permet de faire 
cette discrète insertion.


## code_after

Dans le template `std_progC.pl`, la clé `code_after` permet de rajouter du code C à la suite du 
code proposé par l'apprenant et cela avant compilation. Quand un exercice demande de coder une
fonction et que les tests mettent en jeu un programme, `code_after` permet à l'enseignant de 
rajouter une fonction main permettant de tester correctement le code rendu par l'apprenant.


## composant

[Les composants](https://pl.u-pem.fr/components/intro) (components en anglais) sont des utilitaires
d'interactions avec les élèves. Tous les exercices comportent des formulaires ou des parties à cliquer, 
ces parties des exercices à receuillir les réponses, les idées ou encore les décisions des apprenants.
Les composants sont principalement des morceaux à inclure dans vos exercices pour receuillir le travail
des élèves avant évaluation. Ainsi, les formulaires à cliquer, les zones de texte ou de code, les cliquer
glisser dans une liste ordonnée, etc... sont tous des composants, codé à l'aide de la technologie Angular
pour augmenter la puissance des interaction entre les apprenants et les ressources pédagogiques.


## extends

Cette balise `extends` permet d'importer automatiquement des informations issus d'un [[template]] ou 
encore d'un autre exercice. C'est comme une inclusion ou encore un copier-coller. Tout ce qui 
se trouvait dans la source va se retrouver dans la cible et il reste toutefois possible de 
redéfinir les valeurs des clés importées. C'est ce qu'on appelle l'héritage (de manière générale 
en informatique). La cible hérite de la source. C'est très puissant dans le sens que ça permet
de créer très rapidement des clônes, puis de modifier les clônes créés.

Voici un exemple :
```python
  # ceci est dans le fichier deuxieme.pl 
  extend= premier.pl 
```
La ligne précédente a pour effet d'ajouter dans le dictionnaire de l'exercice 
_deuxieme_ les clefs de l'exercice _premier_.


## form

Le formulaire de l'exercice. L'idée est que l'on veux une action de l'utilisateur et donc que l'on souhaite lui fournir des input html pour cela. La gestion de la form est laissé à PL il vous suffit de définir les **input** souhaités dans la balise form. Par exemple pour une response textuelle simple:
```python
form==
<input type="text" name="form_answer" >
==
```

## grader

On désigne par le terme de `grader` le programme Python qui doit corriger
les réponses de l'apprenant. Le grader assure en fait deux missions :

* Il établit une note entre 0 et 100 en analysant les réponses de l'apprenant.
* Il prépare des feedbacks adaptés suivant les réponses de l'apprenant.

La clé `grader` est donc obligatoire dans tout exercice PL. Soit le grader est défini sur
place localement dans l'exercice mais comme l'écriture d'un grader demande un peu d'expérience
avec PL, le plus simple est souvent d'utiliser un template pour hériter de son grader.

Exemple:
```
@ /grader/executor.py [grader.py]
```


## jinja

Jinja est un moteur de templates pour le langage de programmation [[python]]. Il s'agit
d'une technologie relativement avancée (pour les utilisateurs à l'aise avec l'informatique) 
pour générer des contenu web avec des variables [[python]].


## latex

Latex est un système de composition de documents scientifiques. C'est un outil technique
mais puissant pour générer des supports pédagogiques mais aussi des articles de recherches.
Latex est globalement une collection de commandes de type macros et de balises. C'est un 
outil central pour produire des documents comportant symboles mathématiques de qualité 
professionelle. Latex permet aussi, grace à ses nombreux packages tiers, de générer des
graphiques et des images vectorielles. 


## LMS

LMS est l'acronyme anglais de Learning Management System. C'est un logiciel qui accompagne 
et gère un processus d'apprentissage ou un parcours pédagogique. En français, on parle 
de **plateforme d'apprentissage**, de **système de gestion de l'apprentissage**, 
**plate-forme e-learning**, on encore **formation ouverte et à distance** (FOAD).

**Moodle** est un exemple de LMS libre. Ce dernier n'est pas orienté exerciseur mais 
reste très complet en terme d'authentification, gestion de classes et gestion de contenu
statique. **PLaTon** se place actuellement en complément de **Moodle** pour augmenter ses 
capacités d'exerciseurs (**Moodle** ou un autre LMS utilisant le protocole LTI ( voir [[lti]] ).


## LTI

LTI est l'acronyme anglais de Learning Tools Interoperability. C'est un protocole, donc un 
ensemble de règles de communication, permettant à plusieurs logiciels au service de 
l'enseignement de communiquer entre eux. Pour le projet **PLaTon**, ce protocole est 
important car il permet notament de sous-traiter l'authentification au LMS (voir [[lms]] ).
Toujours dans un objectif de réutilisabilité, un protocole est une spécification 
technique un peu pénible mais qui permet d'éviter de devoir réinventer la roue.

Aussi, LTI est un choix raisonnable dans le sens que le projet **PLaTon** ne force 
absolument pas l'utilisation de **Moodle** en particulier. Tout LMS (voir [[lms]] ) 
utilisant le protocole LTI s'interface avec **PLaTon**.


## Markdown

Markdown est un langage de balisage léger. Markdown permet d'écrire des documents et
des présentations sans compétances techniques particulières et en y incluant du 
formatage et une mise en page légère. Voici un bout de markdown :

```mardown
### titre de niveau 3

Et puis voici un **petit texte** associé *à ce titre*. 
Ceci est ~~vachement dur~~ simple à taper.
```
Voici maintenant l'effet final de ces sources au format markdown :

### titre de niveau 3

Et puis voici un **petit texte** associé *à ce titre*. 
Ceci est <del>vachement dur</del> simple à taper.


## Premier Langage

Premier Langage est le premier nom porté par le projet **PLaTon**. Originellement, la 
plateforme devait répondre à la très grande tension dûe aux manques d'enseignants en 
informatique pour les premières années dans le supérieur. Monopolisés à répéter toujours 
les mêmes consignes et à corriger les mêmes erreurs, les enseignants ont senti le besoin 
de mettre en place une plateforme pour apprendre son premier langage de programmation. 
L'objectif était d'automatiser les exercices simples et standard autour des premiers pas 
avec **Python**. La plateforme s'est très rapidement ouverte vers d'autres matières car 
les capacités du coeur technique de la plateforme se généralisaient trivialement vers 
toute matière.


## Python

**Python** est langage de programmation généraliste. Longtemps considéré seulement comme 
un langage de script, **Python** permet aujourd'hui, grace à ses nombreux framework
dérivés, de produire des projets ambitieux comme **PLaTon**. **Python** est aussi 
devenu, petit à petit, une référence dans l'enseignement. C'est le langage à privilégier
pour les permières et terminales dans les lycées français ainsi que dans les classes
préparatoires aux grandes écoles. Aussi, dans le supérieur, **Python** est considéré
comme un langage particulièrement adapté pour les enseignements en algorithmique. Dans 
le monde de la recherche (principalement informatique et mathématique), **Python** est
reconnu comme un langage très efficace pour l'exploration informatique et la constitution 
de POC (Proof Of Concept). Ce n'est pas un langage produisant des programmes rapides
et efficace mais c'est un langage permettant de produire des choses très évoluées en 
peu de lignes de code.


## sandboxio.py 

**Module python pour fabriquer un nouveau `grader` (niveau avancé)**

sandboxio.py est un module Python pour les utilisateurs experts voulant coder leur propre
grader. A minima, ces personnes doivent être capables de programmer des entrées sorties 
en Python. Le module sandboxio.py propose trois fonctions d'A.P.I.
pour écrire des `grader`. Ces trois fonctions de sandboxio.py vont gérer les entrées/sorties et la restitution au
système du couple (note, feedback) tout en updatant le contexte. Un grader écrit en
utilisant les entrées/sorties définies avec sandboxio.py a plus de chances d'être PL-compatible.


## solution

Dans le template `std_progC.pl`, la clé `solution` permet de définir une solution enseignant
invisible pour les apprenants. Le contenu de cette clé est alors utilisé par le template pour
produire les sorties attendues des tests. Le template réalisant la comparaisont avec les réponses de l'élève.


## taboo

La clé `taboo` permet, dans certains templates, d'interdire l'utilisation de certaines choses à
l'apprenant. Dans un contexte d'exercice de programmation, dans le template `std_progC.pl`, 
définir un `taboo` permet à l'enseignant d'interdire l'accès à certaines bibliothèques ou bien
d'interdire l'utilisation de certaines fonctions. L'usage prototypique est par exemple de demander 
à l'apprenant de recoder une fonction C calculant la longueur d'une chaine de caractères en lui 
interdisant l'utilisation de la fonction **strlen**. L'usage et le traitement de cette clé dépend
complètement du template utilisé par l'exercice (vérification, notation et représailles). Pour
plus de détails, référez-vous à la documentation de votre template.


## title

La valeur associé à la clé `title` donne un titre à l'exerice PL. Si vous définissez cette balise
dans une activité, alors vous lui spécifierez un titre.
Un bon titre est juste une chaîne de caratères qui décrit simplement le contenu de l'exercice.
Les bons titres pleins de sens facilitent les recherches et la réutilisabilité des ressources.
Eviter les titres du genre : exo1, exo2 ,exo3 ... exo7 (particulièrment dangereux).



## template

Un template ou patron est un fichier ressource (normalement d'extension .pl) qui contient 
des informations génériques pour la fabrication d'un certain type d'exercices. On dit qu'un template
est paramètrable ou déclinable en un exercice. C'est une notion fondamentale pour la réutilisabilité
et la factorisation des ressources pédagogiques. Faire des templates permet de gagner du temps,
de mutualiser les tâches de développement techniques pour produire plus de ressources avec
moins de travail.

Prenons un exemple, si un QCM bien adapté est souvent une série de 10 questions choisies
au hasard dans un très grand ensemble de questions avec réponses mélangées mais une correction
dynamique adaptée à la série tirée ; et bien ici on n'a pas précisé la matière du QCM (math, 
info, biologie). En effet, les tirages aléatoires sont des tâches génériques et techniques
qui peuvent être partagées pour tous les enseignants. Ainsi, le QCM ainsi décrit peut-être
un template qui peut être décliné avec l'aide d'un ensemble de questions. Un enseignant peut
alors produire un QCM dédié à son besoin en héritant du template avec [[extends]] puis en
y greffant les questions à choix multiples spécifiques à son enseignement.

Les templates et l'héritage constitue un mécanisme inportant pour assurer le découplage
des ressources pédagogiques (pérenne) et du moteur interne de la plateforme (qui a une durée 
de vie limité comme tout logiciel).


## text

`text` est une clé obligatoirement renseignée dans un exercice **PLaTon**. Le contenue de 
cette clé est une chaîne de caractères possiblement très longue. La clé à vocation à contenir 
le corps de l'énoncé de l'exercice dans un exercice PL. C'est donc l'ensemble des consignes
que vous souhaitez transmettre à votre apprenant avant qu'il remplisse le formulaire de 
l'exercice et qu'il soumette sa réponse. Techniquement, la clé `text` peut contenir du texte 
simple et plus généralement du [[markdown]] mais aussi du [[latex]] et des 
templates [[jinja]] .
