# Template d'exercices de programmation en C

Cette documentation explique le fonctionnement du template standard pour les exercices de 
programmation en C dans sa nouvelle version nommé **std_progC** et publiée au mois de juillet 2020. 
La nouvelle version, réécrite depuis zéro, enrichie les fonctionnalité de l'ancien template 
**stdsandboxC** vieux de 3 ans.

!!! Note
    Pour hériter de ce template, voici la commande nomtrant son chemin dans Yggdrazil :   
    `extends=/ComputerScience/C/template/std_progC.pl`

L'esprit du template est toujours d'exécuter du code étudiant ainsi qu'une solution enseignant
tout deux encapsulés dans des programmes (avec du code avant et du code après). Le template exécute
ses codes avec certains arguments et une entrée standard spécifiée, puis compare systématiquement
les sorties standards. Enfin le template termine en compilant une note et un feedback.

## Nouveautés dans cette refonte de template

* Utilisation de **subprocess** pour les exécutions et la compilation.
* Suppression du fichier hack student.c contenant seulement `#include "student.py"`.
* Builder/grader entièrement en python (sans injection de bash ou de C).
* Meilleure gestion des **signaux systèmes** durant les exécutions encapculées.
* Possibilité de customiser les **flags de compilation** dans les exercices finaux.
* Feedback compact en **javacript** via des fenêtres agrandir/réduire pour de nombreux items.
* Meilleure intégration dans PLaTon (notament vis à vis des tests de fichier `.pl`).
* Remplacement de l'ancien éditeur par le composant Angular `Code Editor`.
* Notation évoluée avec gestions du nombre de tentatives.
* Possibilité d'interdire toute occurence d'une **expression régulière** dans le code élève.

La notation finale est pourcentage qui est le produit de trois autres pourcentage.

`note_finale = note_compilation * note_tests * note_tentatives / 10000`

La note de compilation est de 100% si le compilateur de retourne ni warning, ni erreur. 
Une erreur (ou plus) de compilation donne la note de 0%. Chaque warning coute 10%. Ainsi, un 
code compilant sans erreur mais avec 10 warnings aura la note de 0%.

La note de test est construite avec deux entiers : `bon` le nombre de tests réussis et
`mauvais` le nombre de tests échoués. La note de test vaut alors,   
`note_tests = min( (bon*100) // (bon + mauvais) , 100 // (2**mauvais) )`   
Ainsi, si l'exercice a grand nombre de tests, c'est la seconde formule qui gagne le test,
chaque mauvais test divisant encore par deux la note pourcentage. Mais en imaginant qu'un
exerice ne possède qu'un seul test (hello word par exemple), cette formule donnerait
50% de réussite au test en les échouant tous. Le min avec la première formule évite cette
surcôte dans la notation.

!!! Note
    Ce **min** est pénible mais vraiment important. Certains exercices sont deux fois plus durs 
    quand on veut aussi réussir le dernier test. De ce fait, la seconde formule est la plus
    pédagogique en programmation. Mais elle surnote dans certains cas (notament, elle n'est 
    jamais nulle), ce qui contraint à utiliser un **min**.

Le nombre de tentatives donne une dernière note d'efficacité. À la première tentative, 
cette note vaut 100%, une autre tentative va enlever 10%, puis un peu moins, encore un 
peu moins pour s'amortir à 50% après un très grand nombre de tentatives. La formule 
suivie exacte est :   
`note_tentatives = 50 + ( 200 // (3 + nombre_de_tentatives) )`

!!! Note
    Un apprenant extrêment travailleur mais très très peu doué (typiquement qui travaille mal),
    pourra toujours obtenir 50% en note finale au pris de moult et moult tentative. C'est un 
    choix pédagogique discutable (à la hausse comme à la baisse). Peut-être même que ce choix 
    devrait être plus dynamique et exercice dépendant.


## Différences pour mettre à jour d'anciens exercices

Voici la liste complète des modifications (4) à apporter si des fois, vous voudriez adapter 
des exercices utilisant l'ancien template **stdsandboxC** vers le template **std_progC**.

* Bien sur la notification de l'héritage, les exercices ne doivent plus étendre **stdsandboxC**
mais il doivent maintenant contenir la ligne   
`extends=/ComputerScience/C/template/std_progC.pl`

* La clé `codebefore` est à renommer en `code_before`, c'est toujours du code contextuel 
préposé au code de l'élève ou au code `solution`.

!!! Attention
    Pour le moment, même si vous ne souhaitez pas inclure de code prépositionné dans votre exercice,
    vous devez tout de même définir la clé `code_before` avec pour contenu la chaîne vide.

* La clé `codeafter` est à renommer en `code_after`, c'est toujours du code contextuel 
postposé au code de l'élève ou au code `solution`. C'est l'endroit où l'on code la 
fonction `main` du programme quand ce n'est pas à l'élève de faire.

!!! Attention
    Pour le moment, même si vous ne souhaitez pas inclure de code prépositionné dans votre exercice,
    vous devez tout de même définir la clé `code_after` avec pour contenu la chaîne vide.

* Les données de tests ne doivent plus s'appeler `tests` car PLaTon l'utilise dans le module de 
test des fichiers d'extension `.pl` . Maintenant, les données de tests pour le grader sont 
à placer dans une clé `checks_args_stdin` et la sémantique à un peu changé. La clé 
`checks_args_stdin` doit maintenant suivre la structuration suivante :

```
[ ["Nom du premier test", ["arg1", "arg2", "arg3"], "sdtin du premier test"],
  ["Nom du second test", [], "sdtin du second test"],
  ["Nom du troisième test", ["arg1", "arg2"], ""]  ]
```

  Le second test est lancé sans argument, le dernier test a une entrée standard vide.

## Exemple commenté utilisant le template

L'exemple suivant peut être [testé en cliquant ici](https://pl.u-pem.fr/filebrowser/demo/24923/).   
Les parties cachées du code (le *main* avec sa gestion des arguments) sont juste là pour les 
entrées sorties et permettrent aux élèves de se concentrer sur la fonction à coder.

    # héritage du template
    extends=/ComputerScience/C/template/std_progC.pl
    
    # méta données primaires
    author=Nicolas Borie
    title=Moyenne des éléments positifs
    tag=function|array|type
    
    # augmentation de la taille par défault de l'éditeur de code
    editor.height=300px
    
    # énoncé et consignes de l'exercice
    text==
    Écrire une fonction C **mean_positive** qui prend en argument un tableau d'entiers 
    **array** ainsi que sa taille **size**. Votre fonction devra retourner la moyenne
    des éléments positifs ou nuls contenus dans le tableau. Cette moyenne devra être
    calculée et retournée dans les floattants C. Si le tableau ne contient aucun 
    élément positif ou nul, votre fonction devra alors retourner zéro (dans les 
    flottants toujours).
    ==
    
    # contenu par défault de l'éditeur de code
    editor.code==#|c|
    ... mean_positive(int* array, int size){
      /* Votre code ici... */
      return ...
    }
    ==
    
    # solution(cachée) du prof dont l'élève doit calquer le comportement
    solution==#|c|
    float mean_positive(int* array, int size){
      int i;
      int nb=0;
      float sum = 0.0;
    
      for (i=0 ; i<size ; i++){
        if (array[i] >= 0){
          sum += array[i];
          nb += 1;
        }
      }
      if (nb > 0)
        return sum / nb;
      return 0.0;
    }
    ==
    
    # code contextuel préposé
    code_before==#|c|
    #include <stdio.h>
    #include <stdlib.h>
    ==
    
    # code contextuel postposé
    code_after==#|c|
    int main(int argc, char* argv[]){
      int* array=NULL;
      int i;
    
      array = (int*)malloc(sizeof(int) * argc);
      for (i=1 ; i<argc ; i++)
        array[i] = atoi(argv[i]);
    
      printf("mean_positive( [");
      for (i=1 ; i<argc-1 ; i++)
        printf("%d, ", array[i]);
      if (argc > 0)
        printf("%d", array[argc-1]);
      printf("] ) : %f", mean_positive(array, argc-1));
    
      return 0;
    }
    ==
    
    # données des tests qui seront exécuté entre le code élève et la solution prof
    checks_args_stdin==#|python|
    [["Exemple simple", ["1", "2", "3"], ""],
     ["Tableau vide", [], ""],
     ["Que des négatifs", ["-1", "-1", "-321"], ""],
     ["Mélange de valeurs non nulles", ["-1", "3", "1", "-12", "2"], ""],
     ["Mélange de valeurs avec des zéros", ["-1", "3", "0", "1", "-12", "2", "0", "-3", "0"], ""],
     ["Test aléatoire 1", [str(randint(-100,100)) for i in range(randint(5, 10))], ""],
     ["Test aléatoire 2", [str(randint(-100,100)) for i in range(randint(11, 15))], ""],
     ["Test aléatoire 3", [str(randint(-100,100)) for i in range(randint(16, 20))], ""] ]
    ==

## Résumé rapide des informations minimales à fournir

Actuellement, toutes les clés sont requises (ceci devrait être assoupi). Même si vous souhaitez 
ne pas inclure de code contextuel, il faut quand même définir des `code_befre` et `code_after` vides.
Donc, globalement, un exercice atomique de programmation de C doit renseigner les clés suivantes :

!!! Note
    Le titre `title`, les tags `tag` ainsi que l'énoncé `text` contiennent des mots qui seront le
    support d'une bonne indexation dans le serveur central de ressources. Plus on soigne ces informations,
    plus on gagne du temps à l'avenir pour la qualité des ressources.

Liste minimale des clés standards à fournir et renseignées dans votre fichier `.pl` :

* `extends` : pour spécifier le template
* `title` : donner des titres précis à vos exercices
* `author` : optionnel, mais rien que des initiales aideront vos collègues à vous contacter pour la maintenance
* `tag` : des mots-clés qui faciliteront l'indexation de l'exercice dans le serveur de ressources
* `editor.code` : le code par défault dans l'éditeur élève, on y place souvent les contraintes (un prototype à respecter par exemple)
* `code_before` : le code à inclure avant le code élève pour le rendre compilable (souvent les bilbiothèques)
* `code_after` : le code à inclure après le code élèves pour le rendre compilable (souvent une fonction *main*)
* `checks_args_stdin` : les données de test en python telles que spécifiées plus haut. Tous les symboles de la bibliothèque *random* sont déjà chargés. 
* `taboo` : optionnel, une expression régulière pour imposer des contraintes dans les codes apprenants

!!! Attention
    A terme les champs `code_before` et `code_after` seront optionnel car définit par défault à la châine vide.
    
## Nouvelle fonctionnalité taboo (été 2020)

La clé optionnelle **taboo** permet à l'enseignant éditeur de spécifier une expression régulière dans 
l'exercice. Si cette clé existe et possède donc une valeur, un texte d'avertissement sera automatiquement
généré à la fin de l'énoncé avant la zone de saisie de code élève.

Lors de l'évaluation, le gradeur va alors vérifier que le code proposé par l'élève ne comporte aucune 
occurence de l'expression régulière **taboo** si cette dernière à été spécifiée. Si l'élève utilise 
un motif attrapé par l'expression régulière, alors il y aura un refus de compilation et une refus de 
lancer les tests. Ce refus coutera une tentative à l'élève qui aurait mieux dû lire l'énoncé (c'est 
un choix pédagogique, noter à -1 et ne pas compter de tentative serait un autre choix pédagogique 
différent).

Pour interdire une liste de mots : par exemple les 4 mots **string.h**, **strlen**, **stdlib.h**, **strdup**
votre expression régulière pourra être :


    # Pour interdire l'apparition de 4 mots dans le code élève
    taboo=string.h|strlen|stdlib.h|strdup


Le tout sans aucun espace final ou incis au milieu. Pour en savoir plus sur les expréssions régulière,
vous pouvez consulter la documentation du module **re** de **Python** ou encore la 
[page wikipédia](https://fr.wikipedia.org/wiki/Expression_r%C3%A9guli%C3%A8re).


## Nouvelle fonctionnalité Indices (été 2021)

La clé optionnelle **astuces** permet à l'enseignant éditeur de rajouter des indices libérables
durant la réalisation des exercices. Les anciens exercices, sans indice, restent compatibles avec 
l'ancienne version du template. Si vous décidez de rajouter une clé **astuces**, alors un nouveau
composant sera automatiquement ajouté dans votre exercices. L'apprenant pourra alors cliquer au
fur et à mesure pour obtenir de l'aide.

La note finale en sera aussi affectée. Sans indice, tous les points sont donnés à l'apprenant. Sinon,
un pourcentage de pondération sera appliqué sur la note. Le pourcentage vaut 100% si aucun indice
n'a été libéré et décroit linérairement vers 50% si tous les indices ont été relachés.

Voici un exemple avec une famille de 3 indices pour l'exercice consistant à code un hello world.

    astuces==#|python|
    [
      { "content": """Il suffit, dans cet exercice, d'utiliser une seule fois la fonction `printf` avec un seul argument : une chaîne de caractère statique bien préparé."""},
      { "content": """S'il vous semble que votre fonction fait ce qui est attendu mais que la plateforme vous compte une erreur, c'est que vous ne gérez pas correctement le retour à la ligne final. Et attention, ne rajoutez pas d'expace surperflu avant ce retour à la ligne."""},
      { "content": """`printf("Hello World!\n");` est l'unique instruction à insérer dans votre fonction `main`. N'oubliez pas non plus de retourner un entier : ici `0` car cette fonction se comporte normalement en opérant son affichage."""}
    ]
    ==
