# Template d'exercices de programmation en C

Cette documentation explique le fonctionnement du template standard pour les exercices de 
programmation en C dans sa nouvelle version **std_progC** publiée au mois de juillet 2020. 
Ce template, réécrit depuis zéro, enrichie les fonctionnalité de l'ancien template 
**stdsandboxC** vieux de 3 ans.

Pour hériter de ce template, voici la commande nomtrant son chemin dans Yggdrazil :

`extends=/ComputerScience/C/template/std_progC.pl`

L'esprit du template est toujours d'exécuter du code étudiant et une solution enseignant
encapsulé dans des programmes (avec du code avant et du code après). Le template exécute
ses code avec certains arguments et une entrée standard spécifiée, en comparant systématiquement
les sorties standards, le template termine en compilant une note et un feedback.

## Nouveautés dans cette refonte de template

* Utilisation de **subprocess** pour les exécutions et la compilation
* Builder/grader entièrement en python
* Meilleur gestion des **signaux systèmes** durant les exécutions encapculées
* Possibilité de customiser les **flags de compilation** dans les exercices finaux
* Feedback compact en **javacript** via des fenêtres agrandit/réduire
* Meilleure intégration dans PLaTon (notament vis à vis des tests d'exercices)
* Notation évoluée avec gestions du nombre de tentatives

La notation finale est pourcentage qui est le produit de trois autres pourcentage.

`note_finale = note_compilation * note_tests * note_tentatives / 10000`

La note de compilation est de 100% si le compilateur de retourne ni warning, ni erreur. 
Une erreur de compilation donne la note de 0%. Chaque warning coute 10%. Ainsi, un 
code compilant sans erreur mais avec 10 warnings aura la note de 0%.

La note de test est construite avec deux entiers : `bon` le nombre de tests réussis et
`mauvais` le nombre de tests échoués. La note de test vaut alors,   
`note_tests = min( (bon*100) // (bon + mauvais) , 100 // (2**mauvais) )`   
Ainsi, si l'exercice a grand nombre de tests, c'est la seconde formule qui gagne le test,
chaque mauvais test divisant encore par deux la note pourcentage. Mais en imaginant qu'un
exerice ne possède qu'un seul test (hello word par exemple), cette formule donnerait
50% de réussite au test en les échouant tous. Le min avec la première formule évite cette
surcôte dans la notation.

Le nombre de tentatives donne une dernière note d'efficacité. À la première tentative, 
cette note vaut 100%, une autre tentative va enlever 10%, puis un peu moins, encore un 
peu moins pour s'amortir à 50% après un très grand nombre de tentatives. La formule 
suivie exacte est :   
`note_tentatives = 50 + ( 200 // (3 + nombre_de_tentatives) )`


## Différences pour mettre à jour d'anciens exercices

Voici la liste des modifications à apporter si des fois, vous voudriez adapter des exercices 
utilisant l'ancien template **stdsandboxC** vers le template **std_progC**.

* Bien sur la notification de l'héritage, les exercices ne doivent plus étendre **stdsandboxC**
mais il doivent maintenant contenir la ligne   
`extends=/ComputerScience/C/template/std_progC.pl`

* La clé `codebefore` est à renommer en `code_before`, c'est toujours du code contextuel 
préposé au code de l'élève ou au code `solution`.

* La clé `codeafter` est à renommer en `code_after`, c'est toujours du code contextuel 
postposé au code de l'élève ou au code `solution`. C'est l'endroit où l'on code la 
fonction `main` du programme quand ce n'est pas à l'élève de faire.

* Les données de tests ne doivent plus s'appeler `tests` car PLaTon l'utilise dans le module de 
test des fichiers d'extension `.pl` . Maintenant, les données de tests pour le grader sont 
à placer dans une clé `checks_args_stdin` et la sémantique à un peu changé. La clé 
`checks_args_stdin` doit maintenant suivre la structuration suivante :

      [["Nom du premier test", ["arg1", "arg2", "arg3"], "sdtin du premier test"],
       ["Nom du second test", [], "sdtin du second test"],
       ["Nom du troisième test", ["arg1", "arg2"], ""]] 
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

## Résumé rapide des informations requises

Actuellement, toutes les clés sont requises (ceci devrait être assoupi). Même si vous souhaitez 
ne pas inclure de code contextuel, il faut quand même définir des `code_befre` et `code_after` vides.
Donc, globalement, un exercice atomique de programmation de C doit renseigner les clés suivantes :

* `extends` : pour spécifier le template
* `title` : donner des titres précis à vos exercices
* `author` : optionnel, mais rien que des initiales aideront vos collègues à vous contacter pour la maintenance
* `tag` : des mots-clés qui faciliteront l'indexation de l'exercice dans le serveur de ressources
* `editor.code` : le code par défault dans l'éditeur élève, on y place souvent les contraintes (un prototype à respecter par exemple)
* `code_before` : le code à inclure avant le code élève pour le rendre compilable (souvent les bilbiothèques)
* `code_after` : le code à inclure après le code élèves pour le rendre compilable (souvent une fonction *main*)
* `checks_args_stdin` : les données de test en python telles que spécifiées plus haut. Tous les symboles de la bibliothèque *random* sont déjà chargés. 

Warning

A terme les champs `code_before` et `code_after` seront optionnel car définit par défault 
à la châine vide.
