# titre

Je vous propose dans ce guide, de vous expliquer comment domotiser les lumières de la maison tout en gardant en fonctionnement les interrupteurs existants pour ne pas être obligé de dégainer constamment son téléphone pour allumé une lumière ou tout simplement pour que les lumières continuent à fonctionner normalement même en cas de plantage de la domotique.
<br>

[u][size=4]**Principe :**[/size][/u]

Les cas les plus courants de branchement des lumières dans une maison sont les suivants.

**L'interrupteur simple**
Un interrupteur pour commander un point lumineux

> *J'appelle point lumineux, une lumière seule ou un ensemble de lumières qui s'allument ensemble*

<p align="center"><img src="/img/interrupteur.png"></p>

**Les interrupteurs en va et vient**
Deux interrupteurs pour commander un point lumineux
[center]![Va et vient|690x187](upload://2PhGfKcS4CrNBch6rMXDS8ANKNy.png)[/center]

**Les boutons poussoirs et télérupteur**
Un ou plusieurs boutons poussoirs et un télérupteur pour commander un point lumineux (On retrouve ici deux possibilités)
Les boutons poussoirs avec phase
![Telerupteur phase bp|690x213](upload://1s17HhsldrJsrNQpn6gixFv0zXQ.png)

**Les boutons poussoirs avec neutre**
[center]![Telerupteur neutre bp|690x213](upload://mOftesYWSWgh5bNjDRS1Nl6p8Oj.png)[/center]

Et pour finir un cas que l'on voit quand même moins souvent car remplacé, depuis pas mal de temps déjà, par les câblages avec télérupteurs
**Les interrupteurs en va et vient avec permutateur**
[center]![Permutateur|690x186](upload://jAqOgGnImDuUjJmlOR8f59fzXRe.png)[/center]

On peut voir sur les schémas précédents que dans tous les cas nous avons :
* Une arrivée électrique symbolisée par le disjoncteur (à gauche sur les schémas)
* Un bloc de commande (encadré en vert)
* Un point lumineux

On notera que quel que soit la complexité de la commande, vu du côté de la lampe la commande se comportera toujours comme un seul interrupteur. On appui ça s'allume, on appui à nouveau ça s'éteint.

**Pour pouvoir domotiser tout ça, il faut donc rajouter un module (smart switch) entre le bloc de commande et le point lumineux.**
[center]![schema de principe|690x175](upload://lufB9EMzMuzOzU38Y4pJEmCEfCF.png)[/center]
<br>

**[size=4]Choix du module :[/size]**
J'ai choisi pour ce guide des modules de chez sonoff
* [Le ZBminiL2](https://sonoff.tech/product/diy-smart-switches/zbmini-l2/)
https://www.domadoo.fr/fr/peripheriques/6619-sonoff-commutateur-intelligent-sans-neutre-zigbee-30-zbminil2-6920075778298.html
[center] ![ZBMINIL2|500x500, 25%](upload://a7wLa0buPY3QPQ82QUWwiaF8UM.jpeg)[/center]

* [Le ZBminiR2](https://sonoff.tech/product/diy-smart-switches/zbminir2/)
https://www.domadoo.fr/fr/peripheriques/7474-sonoff-module-zigbee-commutateur-10a-zbminir2.html
[center]![ZBMINIR2|500x500, 25%](upload://so7pI97IbybtKsWx5ULpOIHL4Zx.jpeg)[/center]

* [Le MiniR4M](https://sonoff.tech/product/diy-smart-switches/minir4m/)
https://www.domadoo.fr/fr/eclairage-connecte/6783-sonoff-module-connecte-onoff-matter-10a-minir4m.html
[center]![MINIR4M|500x500, 25%](upload://30PRZLRp6cgqClEF38czB7CRLnY.jpeg)[/center]

* [Le MiniR4](https://sonoff.tech/product/diy-smart-switches/minir4/)
https://www.domadoo.fr/fr/peripheriques/6600-sonoff-module-commutateur-connecte-wi-fi-10a-minir4.html
[center]![MINIR4|500x500, 25%](upload://aqBxTxM65541EiuNDVZ8akbZSar.jpeg)[/center]

**Pourquoi ceux-ci et pas d'autres, me direz-vous ?**
Parce que ce sont ceux que je connais le mieux, que j'ai pu avoir entre les mains pour certains d'entre eux.
Parce qu'ils acceptent sur leurs entrées aussi bien des interrupteurs que des boutons poussoirs et qu'ils peuvent se comporter sur leurs sorties comme des interrupteurs (les 4) ou comme des boutons poussoirs (à l'exception du ZBminiL2).

> Bien sur il est tout à fait possible de réaliser la même chose avec des modules d'autres marques à conditions qu'ils aient les mêmes possibilités que ceux présentés ici.

**Leurs différents schémas de câblage**
ZBminiL2
[center]![ZBMINIL2-schema|690x148](upload://roWOfta1OabR6CPTzqnzWlqQcxP.png)[/center]

ZBminiR2, MiniR4M et MiniR4
[center]![ZBminiR4-schema|690x203](upload://1cIDXFBYa0Cma88TYFdDQe4A7Vb.jpeg)[/center]

Ces schémas nous apprennent que pour pouvoir brancher les différents modules nous avons besoin d'identifier certains fils.
La phase pour l'alimentation du module, le départ vers la lampe qui est également la sortie de " la commande " (interrupteur, va et vient etc...) dans le cas du ZBminiL2 et en plus le fil de neutre pour les 3 autres.
<br>

[u]**[size=4]Dans la pratique, comment faire :[/size]**[/u]

C'est bien beau tous ces schémas car on voit tous les fils, mais en pratique on d'un côté le tableau électrique, le ou les boitiers d'encastrement avec les interrupteurs ou poussoirs et la lampe au plafond ou sur un mur.

Un seul point de commande
[center]![boite_inter|690x174](upload://vjBLl1qMDHKD5ZNEq269rUNU6ro.png)[/center]
J'ai mis un fil bleu en pointillé dans la boite qui représente le fil de neutre car il n'est pas toujours présent. Je ne l'ai pas remis sur les schémas ci-dessous pour ne pas les surcharger

Deux (ou plus) point de commande
[center]![boite_vv|690x174](upload://rAQKFlp938V6UPptVqrkV6LZUCG.png)[/center]

[center]![boite_poussoir|690x174](upload://a75x30mvHg6Oz4oURbr54iaUDY0.png)[/center]


**Comment s'y retrouver ?**

[color=red]Petit rappel ici, on ne joue pas avec l'électricité au risque dans le pire des cas d'y laisser la vie. Avant toute intervention dans le tableau électrique ou derrière une prise ou interrupteur on coupe le courant.[/color]

Je commence par identifier si mes points de commande sont des interrupteurs ou des boutons poussoirs. Pour ce faire il suffit d'appuyer dessus. Si une fois relâché il reste en position, c'est un interrupteur et si il revient à sa position initiale c'est alors un bouton poussoir. (Cela pourra aider pour paramétrer le module si besoin, ou encore appeler les choses par leurs noms en cas de question sur les forums)
Dans le cas on l'on a des boutons poussoirs, c'est que l'on a forcément un télérupteur (ou minuterie) quelque part et il faudra également le retrouver. Celui peut être dans le tableau électrique mais on peut aussi en trouver dans des boites de dérivation dans les murs ou dans les combles. 

Je vais à mon tableau électrique et je coupe le courant de la ligne concerné (En cas de doute, on coupe le général). Une fois le disjoncteur coupé je retourne appuyer sur l'interrupteur sur lequel je travaille et j'appuie dessus pour m'assurer que la lumière reste bien éteinte. Si ce n'est pas le cas c'est que je n'ai pas coupé le bon circuit.

Une fois le courant coupé je peux ouvrir mes interrupteurs ou poussoirs pour voir derrière ce que l'on va trouver comme fil et pouvoir les identifier. J’en profite pour faire une photo des différents branchements entre les fils et les interrupteurs.

Je fais de même au niveau du ou des points lumineux pour voir les fils qui arrivent.

Maintenant il va falloir identifier quel fil fait quoi.
Si dans le cas d'un interrupteur simple c'est assez facile surtout si les couleurs de fil sont respectées cela peut vite devenir compliqué pour un débutant quand les couleurs ne correspondent pas au schémas et pire quand les fils sont tous de la même couleur (Déjà vu).

Pour faire cette recherche nous allons avoir besoin d'un peu de matériel.
Des wagos ou domino.
Une bonne longueur de fil.
Du scotch d'électricien de préférence blanc.
Un feutre ou stylo permettant d'écrire sur le scotch.
Un multimètre (Avec la fonction continuité de préférence).
[center]![testeur|342x370, 50%](upload://qVUR0hKSo2gWZcA4WM6KqmDfEAT.jpeg)[/center]


**C'est parti !!!**

Commençons par le cas le plus simple avec un seul interrupteur.
Je rappelle que le courant est toujours coupé au tableau.
Je débranche les 2 fils présents sur mon interrupteur.
Je mets mon multimètre en mode continuité et à l'aide de ces câbles je fais contact entre la borne de sortie phase du disjoncteur (Du circuit d'éclairage sur lequel je travaille) et un des fils coté interrupteur.
Vous allez me dire mais les fils de mon multimètre ne sont pas assez longs pour aller du tableau électrique jusqu'à l'interrupteur. C'est là qu'entre en jeu les wagos et la bonne longueur de fil. On va faire une rallonge.

