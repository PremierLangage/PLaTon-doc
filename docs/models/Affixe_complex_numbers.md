# Affixe d'un nombre complexe

Exo qui consite à trouver l'affixe d'un nombre complexe donné sur un plan cartésien.  

Après validation de la réponse : 

"Bonne réponse." en vert  -> réponse correcte 

"Mauvaise réponse. " en rouge -> réponse fausse

Cliquer sur l'image suivante pour tester : 

[![image](Affixe_complex_numbers.png)](https://pl.u-pem.fr/filebrowser/option?name=test_pl&path=Yggdrasil/AAAA/Anna/Affixe.pl)

Voici le code de l'exemple : 

```{r}

extends = /Mathematics/exercises/complex_numbers/affixe.pl

before ==

xsol = randint(-4, 4, [0])

ysol = randint(-3, 3, [0])

z = xsol + ysol*I

jxg.setscript(script_init + script_aux)

==

```

Les paramètres à modifier pour modeler l'exercice sont **xsol** et **ysol**. Ils doivent être sous la forme randint(a, b, [0]) tel que [a,b] un intervalle et a > -5 et b < 5. 

*!NB : Respecter la syntaxe de PlaTon lors de l'édition du titre, de l'énoncé et des choix.*
