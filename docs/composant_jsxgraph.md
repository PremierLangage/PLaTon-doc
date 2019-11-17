# Composant JSXGraph

Basé sur la bibliothèque JavaScript JSXGraph.

[Site officiel](https://jsxgraph.org)

[Wiki avec de nombreux exemples](https://jsxgraph.uni-bayreuth.de/wiki/index.php/Main_Page)

## Exemple 1 : Un histogramme

[Tester l'exemple](https://pl.u-pem.fr/filebrowser/demo/8200/)

~~~
extends = /template/basic.pl

title = Histogramme (statique)

jxg =: MathDrawer

jxg.attributes %=
{"showNavigation" : false,
"keepaspectratio" : false}
==

jxg.script ==
board.setBoundingBox([-1,10,5,-1]);
board.create('chart', [5,7,4,9], {chartStyle:'bar',color:'blue',width:0.6});
==

text ==
{{ jxg | component }}
==
~~~
