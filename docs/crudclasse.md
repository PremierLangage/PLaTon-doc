
# La Classe 


Une classe regroupe de faççon opérationnelle sur un serveur d'asset (serveur local):  
- une équipe enseignante (au moins un responsable, et des colaborateurs) qui accèdent avec l'interface enseignant  
- une ensemble d'élèves, organisés en groupes, qui accèdent avec l'interface etudiant.  
- un cours qui est construit comme un arbre d'élèment pédagogiques (documents, activités, exercices, AAV, évaluations)

Propriétés obligatoires de la classe :
un nom de la classe soyer concit et précis (pas plus de 30 caractères).
une description (elle est utilisé pour retrouver des classes similaires clustering) soyer donc généreux dans l'utilisation de mots clefs.

Une classe à un [niveau](../concept/niveau.md) : le niveau scolaire des élèves (liste déroulante + champs libre).

Une classe est liée a une [discipline](../concept/discipline.md), qui est la discipline "majeur" étudiée dans le cours (liste déroulante + un champs libre)
il est possible d'indiquer dasns le deuxième champs une liste de disciplines qui participe a cette classe.

Une classe est liée a au moins un [cercle](../concept/cercle.md) : Dans le cercle de la discpline il existe un cercle par niveau et dans cercle il y a un cercle lié à la classe grace au nom que vous avez donné.
Initialement ce cercle est temporaire puis en fonction des choix de gestion des cercles des responsables de la discipline,
 votre classe sera affecté ou non à un autre cercle. Ce cercle est important car il vous donne accès à des ressources qui corresponde à votre discipline.
 
Ne vous inquiétez pas cela ne vous empèchera pas d'accèder à des ressources Hors de la discipline de la classe si vous en avez besoin.

