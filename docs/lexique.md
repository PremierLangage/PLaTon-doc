# Lexiques et notions dans PLaTon


À la fois index et Lexique, cette page a vocation à recenser les clés et termes importants utilisés
dans les ressources de Premier Langage. Si vous programmez de nouvelles ressources, en imaginant de nouveaux
templates ou en définissant de nouvelles clés, il vous sera demandé de mettre cette page à jour. La description
des items présents n'est pas forcement complète ; il vous faut surtout résumer rapidement le rôle d'une clé et 
de sa valeur ou encore décrire rapidement les termes et notions relatif à Premier Langage. C'est une page de
documentation pour les gens pressés mais aussi un point d'entré vers d'autres pages de documentation.


## author

La valeur de cette `clé` permet de spéficier un auteur ou plusieurs auteurs. Comme dans toute
communauté, l'auteur d'une ressource est toujours un bon juge pour en arbitrer les améliorations
proposés par la communauté. C'est une saine pratique de préciser les auteurs.


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

La balise extend permet d'importer automatiquement des informations issus d'un template ou 
encore d'un autre exercice. C'est comme une inclusion ou encore un copier coller. Tout ce qui 
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

Même chose que la baslise [[extends]]
Extends est en fait plus général (extends permet d'hériter de n'importe quel type de ressource). Si
vous souhaitez hériter d'un template, alors utiliser plutôt la clé template que la clé extends, c'est
plus propre et plus clair, vous spécifié alors vraiment votre ressource comme étant un certain 
type d'exercice.


## text

La clé `text` est très souvent définie sur plusieurs ligne. La balise à vocation à contenir 
le corps de l'énoncé de l'exercice dans un exercice PL. C'est donc l'ensemble des consignes
que vous souhaitez transmettre à votre apprenant avant qu'il remplisse le formulaire de 
l'exercice et qu'il soumette sa réponse. 
