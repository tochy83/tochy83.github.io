[some text](color: red)

<p>
Quack quack
<text color=red>ERROR</text>
</p>

# titre

Je vous propose dans ce guide, de vous expliquer comment domotiser les lumières de la maison tout en gardant en fonctionnement les interrupteurs existants pour ne pas être obligé de dégainer constamment son téléphone pour allumé une lumière ou tout simplement pour que les lumières continuent à fonctionner normalement même en cas de plantage de la domotique.
J'ai essayé d'écrire ce guide pour que même un débutant puisse s'y retrouver avec un minimum de matériel, aussi certaines parties pourront paraîtrent sans intérêt pour ceux ayant de bonnes connaisssances en électricité. 
<br><br>

## Le principe

Les cas les plus courants de branchement des lumières dans une maison sont les suivants.

**L'interrupteur simple**<br>
Un interrupteur pour commander un point lumineux

> *J'appelle point lumineux, une lumière seule ou un ensemble de lumières qui s'allument ensemble*

<p align="center"><img src="img/interrupteur.png"></p>

**Les interrupteurs en va et vient**<br>
Deux interrupteurs pour commander un point lumineux
<p align="center"><img src="img/va_et_vient.png"></p>

**Les boutons poussoirs et télérupteur**<br>
Un ou plusieurs boutons poussoirs et un télérupteur pour commander un point lumineux (On retrouve ici deux possibilités)
Les boutons poussoirs avec phase
<p align="center"><img src="img/telerupteur_phase_bp.png"></p>

**Les boutons poussoirs avec neutre**<br>
<p align="center"><img src="img/telerupteur_neutre_bp.png"></p>

Et pour finir un cas que l'on voit quand même moins souvent car remplacé, depuis pas mal de temps déjà, par les câblages avec télérupteurs
**Les interrupteurs en va et vient avec permutateur**<br>
<p align="center"><img src="img/permutateur.png"></p>

On peut voir sur les schémas précédents que dans tous les cas nous avons :
* Une arrivée électrique symbolisée par le disjoncteur (à gauche sur les schémas)
* Un bloc de commande (encadré en vert)
* Un point lumineux

On notera que quel que soit la complexité de la commande, vu du côté de la lampe la commande se comportera toujours comme un seul interrupteur. On appui ça s'allume, on appui à nouveau ça s'éteint.

**Pour pouvoir domotiser tout ça, il faut donc rajouter un module (smart switch) entre le bloc de commande et le point lumineux.**<br>
<p align="center"><img src="img/schema_de_principe.png"></p>
<br><br>

## Choix du module
J'ai choisi pour ce guide des modules de chez sonoff
<table align="center">
<thead>
<tr align="center">
<th>
<br><strong>Le ZBminiL2</strong><br><br>
</th>
<th>
<br><strong>Le ZBminiR2</strong><br><br>
</th>
</tr>
</thead>
<tbody>
<tr align="center">
<td>
<img src="img/zbminil2.jpg" width="25%" height="25%">
<br><a href="https://sonoff.tech/product/diy-smart-switches/zbmini-l2/">La fiche produit du zbminil2</a>
</td>
<td>
<img src="img/zbminir2.jpg" width="25%" height="25%">
<br><a href="https://sonoff.tech/product/diy-smart-switches/zbminir2/">La fiche produit du zbminir2</a>
</td>
</tr>
</tbody>
<thead>
<tr align="center">
<th>
<br><strong>Le MiniR4M</strong><br><br>
</th>
<th>
<br><strong>Le MiniR4</strong><br><br>
</th>
</tr>
</thead>
<tbody>
<tr align="center">
<td>
<img src="img/minir4m.jpg" width="25%" height="25%">
<br><a href="https://sonoff.tech/product/diy-smart-switches/minir4m/">La fiche produit du minir4m</a>
</td>
<td>
<img src="img/minir4.jpg" width="25%" height="25%">
<br><a href="https://sonoff.tech/product/diy-smart-switches/minir4/">La fiche produit du minir4</a>
</td>
</tr>
</tbody>
</table>
<br>

**Pourquoi ceux-ci et pas d'autres, me direz-vous ?**<br><br>
Parce que ce sont ceux que je connais le mieux, que j'ai pu avoir entre les mains pour certains d'entre eux.
Parce qu'ils acceptent sur leurs entrées aussi bien des interrupteurs que des boutons poussoirs et qu'ils peuvent se comporter sur leurs sorties comme des interrupteurs (les 4) ou comme des boutons poussoirs (à l'exception du ZBminiL2).

> [!note]
> Bien sur il est tout à fait possible de réaliser la même chose avec des modules d'autres marques à conditions qu'ils aient les mêmes possibilités que ceux présentés ici.
<br>

**Leurs différents schémas de câblage**<br><br>
ZBminiL2<br>
<p align="center"><img src="img/schema_zbminil2.png"><br><br></p>
ZBminiR2, MiniR4M et MiniR4<br>
<p align="center"><img src="img/schema_minir4.jpg"></p>
Ces schémas nous apprennent que pour pouvoir brancher les différents modules nous avons besoin d'identifier certains fils.<br>
La phase pour l'alimentation du module, le départ vers la lampe qui est également la sortie de " la commande " (interrupteur, va et vient etc...) dans le cas du ZBminiL2 et en plus le fil de neutre pour les 3 autres.
<br><br>

## Dans la pratique, comment faire<br>

C'est bien beau tous ces schémas car on voit tous les fils, mais en pratique on d'un côté le tableau électrique, le ou les boitiers d'encastrement avec les interrupteurs ou poussoirs et la lampe au plafond ou sur un mur.

Un seul point de commande<br>
<p align="center"><img src="img/boite_inter.png"></p>

> J'ai mis un fil bleu en pointillé dans la boite qui représente le fil de neutre car il n'est pas toujours présent. Je ne l'ai pas remis sur les schémas ci-dessous pour ne pas les surcharger

<br><br>
Deux (ou plus) point de commande<br>
<p align="center"><img src="img/boite_vv.png"></p>
<br><br>
<p align="center"><img src="img/boite_poussoir.png"></p>


**Comment s'y retrouver ?**
<br>

> [!CAUTION]
> Petit rappel ici, on ne joue pas avec l'électricité au risque dans le pire des cas d'y laisser la vie. Avant toute intervention dans le tableau électrique ou derrière une prise ou interrupteur on coupe le courant.

<br>
Je commence par identifier si mes points de commande sont des interrupteurs ou des boutons poussoirs.<br>
Pour ce faire il suffit d'appuyer dessus. Si une fois relâché il reste en position, c'est un interrupteur et si il revient à sa position initiale c'est alors un bouton poussoir. (Cela pourra aider pour paramétrer le module si besoin, ou encore appeler les choses par leurs noms en cas de question sur les forums).<br>
Dans le cas on l'on a des boutons poussoirs, c'est que l'on a forcément un télérupteur quelque part et il faudra également le retrouver. Celui peut être dans le tableau électrique mais on peut aussi en trouver dans des boites de dérivation dans les murs ou dans les combles.
<br><br>

Je vais à mon tableau électrique et je coupe le courant.<br>

Une fois le courant coupé je peux ouvrir mes interrupteurs ou poussoirs pour voir derrière ce que l'on va trouver comme fil et pouvoir les identifier. J’en profite pour faire une photo des différents branchements entre les fils et les interrupteurs.<br>

Je fais de même au niveau du ou des points lumineux pour voir les fils qui arrivent.<br>

Maintenant il va falloir identifier quel fil fait quoi.<br>

Si dans le cas d'un interrupteur simple c'est assez facile surtout si les couleurs de fil sont respectées cela peut vite devenir compliqué pour un débutant quand les couleurs ne correspondent pas au schémas et pire quand les fils sont tous de la même couleur (Déjà vu).
<br><br>

**Pour faire cette recherche nous allons avoir besoin d'un peu de matériel**
<br>

Des wagos ou domino.<br>
Une bonne longueur de fil.<br>
Du scotch d'électricien de préférence blanc.<br>
Un feutre ou stylo permettant d'écrire sur le scotch.<br>
Un multimètre (Avec la fonction continuité de préférence).<br>
<p align="center"><img src="img/testeur.jpg" width="20%" height="20%"></p>
<br><br>

## C'est parti !!!

**Commençons par le cas le plus simple avec un seul interrupteur**<br>
> [!CAUTION]
>Je rappelle que le courant est toujours coupé au tableau.

Je débranche les 2 fils présents sur mon interrupteur.<br>
Je mets mon multimètre en mode continuité et à l'aide de ces câbles je fais contact entre la borne de sortie phase du disjoncteur (Du circuit d'éclairage sur lequel je travaille) et un des fils coté interrupteur.<br>
Vous allez me dire mais les fils de mon multimètre ne sont pas assez longs pour aller du tableau électrique jusqu'à l'interrupteur. C'est là qu'entre en jeu les wagos et la bonne longueur de fil.<br>
On va faire une rallonge.

