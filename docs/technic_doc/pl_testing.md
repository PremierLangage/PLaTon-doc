# Ecriture d'un test

(Version 0.6.2 minimum)

L'objectif est d'apprendre à écrire des tests automatiques pour vos PL afin de vérifier que les réponses données par un étudiant donnent bien le feedback et la note attendus.

## La balise tests

Cette balise est obligatoire pour écrire et pouvoir lancer vos tests. Elle doit contenir un dictionnaire (json) dont chaque élément est un test. 

Chaque test doit obligatoirement comporter un élément `response` qui comporte un dictionnaire des réponse de l'élèves de type `input_name`:`input_value`.

Par exemple, il y a deux manières d'écrire des tests pour un formulaire contenant un seul input dont le nom est answer:

* `tests.test1.response = a
tests.test2.response = b`

* `tests %= {
	"test1" : {
		"response" : {
			"answer" : "a"
		}
	},
	"test2" : {
		"response" : {
			"answer" : "b"
		}
	}
}
==`

De plus,vous pouvez tester le grade et le feedback renvoyé par une réponse avec deux balises optionnelles pour chaque test, `grade` et `feedback`. Par exemple:

`tests.test1.response.answer= a
tests.test1.feedback = ok
tests.test2.response.answer = b
tests.test2.grade = 100`

Enfin, vous pouvez fixer la seed utilisée pour un test grace à la balise test:

`tests.test1.response = a
tests.test1.seed = 15`


## Exemple concret de test:
`
tests %=
{
    "correct" : {
        "response" : {
            "answer" : 7
        },
        "grade" : 100,
        "feedback" : "Bonne réponse\n",
        "seed" : 15
    },
    "incorrect" : {
        "response" : {
            "answer" : 8
        },
        "grade" : 0,
        "feedback" : "Mauvaise réponse\n"
    },
}
==`

## Lancer vos tests

Si votre pl contient une balise tests, lors de la preview, vous aurez à disposition un bouton **Tester** qui permet de les lancer.

Chaque test sera alors exécuté comme si un élève répondait à l'exercice, et un nouvel onglet sera ouvert avec les résultats des tests.
