# L'Oeil d'Horus

**Date de réalisation :** Septembre-Decembre 2022, projet personnel
<br> <br>
**Cadre du projet :** Reconnaissance automatique d'objets sur des images satellites.
<br> <br>
**Mots-clés :** Neural Networks, Computer Vision, Satellite Imagery, Civilian & Military Targets
<br>
## Présentation du projet
J'ai réalisé ce projet sur mon temps libre, pendant le premier trimestre de mon Mastère Spécialisé en Intelligence Artificelle à Télécom Paris [[1]](#ref1).  
Celui-ci présente le développement d'un détecteur automatique d'avions à partir d'images satellites en utilisant un modèle de Deep Learning.
Vous trouverez ici une étude scientifique aboutissant sur une comparaison de modèles fonctionnels.
Dans celle-ci, on cherchera a mettre en place plusieurs modèles puis on comparera leurs performances avec celles de l'état de l'art, en émettant des critiques et en proposant des pistes d'interprétation. Commençons déja par une petite mise en contexte. 
<br>
## Contexte  
### Le renseignement, un atout précieux  
On cherche ici a démontrer l'importance du renseignement pour les armées, ainsi que son rôle dans la mise en place d'une stratégie pertiente. En guise d'introduction, on pourra réflechir a la phrase suivante : "l'opportunité de vaincre l'ennemi est fourni par l'ennemi lui-même" énoncée dans l'Art de la Guerre[[2]](#ref2), de Sun Tzu.
Celle-ci illustre la nécessitée d'observer le dispositif adverse afin d'y détecter une faille, et met en valeur l'importance de la prise d'information dans la victoire. 

On peut déja ségmenter le sujet en deux aspects, les renseignements que l'ennemi possède sur nous, et ceux que nous possédons sur l'ennemi. Pour avoir une vue complète de la situation, il est adapté de subdiviser encore le problème, en définissant des sous catégories propre a chacun des référentiels. Ainsi, il y a les renseignements que l'ennemi possède sur nous, et ceux que l'on pense qu'il possède sur nous, de même, il y a les renseignements que nous possèdons sur l'ennemi et ceux qu'il pense que nous possédons sur lui. C'est de l'analyse de ces quatre quantités dont découle la résolution d'un affrontement, ce qui rend finalement cette résolution prévisible. Les deux paragraphes qui vont suivre explorerons les avantages que l'on peut tirer d'une reconnaissance efficace et les dangers qui apparaissent lorsque celle-ci est négligée.  

Il est évident que la capacité a dissimuler les informations est cruciale dans la mise en place d'une stratégie. Mais c'est d'abord en observant, que l'on pourra mettre en place le dispositif qu'il faudra ensuite dissimuler. Ainsi l'acquisition des renseignements est primordiale en ce qui concerne l'établissement d'une stratégie pertiente. Pour illustrer cela, on peut citer la bataille de Satala[[3]](#ref3), en 298, où l'Empereur Romain observer le camp Sassanide de l'intérieur en étant déguisé. Ou l'embuscade de Pressburg[[4]](#ref4), en 907, qui a vu les Hongrois anéantir une armée du Saint-Empire Germanique par une retraite feinte menant à un piège.  

A l'opposée, l'histoire nous propose une multitude de batailles perdues par un mauvais usage des renseignements. Dans ce cas, l'information possédé n'est pas conforme à la réalité et dans tout les cas, il y a quelque chose qui n'as pas été perçu. C'est d'ailleurs, très souvent, une erreur d'orgeuil. Car il arrive que nos secrets, que nous pensions a l'abri, soient finalement pleinement visibles, ou que nous négligions tellement la reconnaissance que l'information cruciale nous échappe. On peut citer les batailles de Iéna-Auerstaedt[[5]](#ref5), en 1806, où Napoléon ordonne la concentration des corps d'armée au mauvais endroit, le désastre étant évité de justesse grâce à la bravoure du 3ème corps et du Maréchal Davoult. On comprend, dès lors, qu'une erreur stratégique est inévitable lorsque des décisions sont prises sur la base d'informations incorrectes.  
<br>
### Le renseignement en pratique  
Historiquement, la reconnaissance était réalisée par les éclaireurs, des régiments de cavalerie légère. De nos jours, cette tâche s'est adaptée à la guerre moderne, et est décomposé en 4 niveaux : Humain, Electromagnétique, Image et Cyber. En ce qui concerne notre projet, la partie imagerie est principalement réalisée par des drones et des satellites. Par exemple, l'OTAN déploie actuellement 5 RQ-4 Global Hawk[[6]](#ref6) pour surveiller l'Ukraine depuis la Roumanie et la Mer Noire. La France dispose également, grâce a Airbus, de la constellation des 2 satellites Pléiades[[7]](#ref7), capable de photographier jusqu'a 20km de terrain avec une précision de 50cm, ainsi que des 3 satellites CERES[[8]](#ref8), chargés de collecter du renseignement d'origine électromagnétique.

Ces systèmes génèrent de nombreuses données, dont il faut extraire les informations d'intelligence stratégique. Pour l'Armée Française et ses alliés, les rapports de reconnaissance suivent les normes au Standard OTAN, définies dans le document STANAG 3596[[9]](#ref9), établi en 2003.
<br>
## Stratégie et hypothèses de l'étude
Le STANAG 3596 définie une importante quantité de cibles ainsi que plusieurs niveaux permettant de fournir une évaluation exploitable de leur état. 
Les images utilisé seront prise selon un angle NADIR.
On se concentre uniquement sur les images satellites pour les avions
On cherche a reconnaire le type d'avions
<br>
## Problématique
Il y a une quantité très importante de données a analyser. Il faut environ une demi-journée à un analyste pour évaluer l'état d'un petit aéroport. De plus ces données sont renouvelées très rapidement, souvent une fois par jours, parfois plus.
Afin d'aider l'opérateur a prendre une décision rapide, on veut lui proposer une évaluation automatique des sites d'interêts.
Ce qui pose la question suivante : 
<br> <br>
**Comment modéliser et évaluer les performances d'un algorithme de reconnaissance d'aéronefs appliqué a l'imagerie satellite et ses contraintes ?**
<br>

## Etat de l'art 
<br>


## Bibliographie de l'introduction

<a name="ref1">[1]</a> : [Contenu de la formation MS IA à Télécom](https://www.telecom-paris.fr/fr/masteres-specialises/formation-intelligence-artificielle)  
<a name="ref2">[2]</a> : [Résumé et critique de "L'Art de la Guerre"](https://www.getstoryshots.com/fr/books/the-art-of-war-summary/)  
<a name="ref3">[3]</a> : [Guerre Romano-Sassanide, Bataille de Satala, 298 après J.-C.](https://www.youtube.com/watch?v=T2571JUYAlI)  
<a name="ref4">[4]</a> : [Guerre Hongro-Germanique, Bataille de Pressburg, 907 après J.-C.](https://www.youtube.com/watch?v=VHUSCs4Nacg)  
<a name="ref5">[5]</a> : [Batailles de Iéna-Auerstaedt, 1806 après J.-C.](https://www.youtube.com/watch?v=odPUHTJO8to)  
<a name="ref6">[6]</a> : [Drone HALE (Haute Altitude, Longue Endurance) RQ-4 Global Hawk](https://www.avionslegendaires.net/2022/10/actu/loeil-volant-des-allies/?fbclid=IwAR3BfqGRQXVCfEkrNRzq246XAnPmke6V6o_yU0kvRv0cZ_pFD8Ucmfd5fHQ)  
<a name="ref7">[7]</a> : [Imagerie satellite, Constellation Pléiades](https://www.intelligence-airbusds.com/imagery/constellation/pleiades/)  
<a name="ref8">[8]</a> : [Ecoute électromagnétique, Constellation CERES](https://www.defense.gouv.fr/drm/actualites/renseignement-dorigine-electromagnetique-satellites-ceres-france-se-dote-dun-systeme-unique-europe)  
<a name="ref9">[9]</a> : [STANAG 3596, Standard OTAN (2003)](https://infostore.saiglobal.com/en-us/standards/stanag-3596-2003-735625_saig_nato_nato_1786746/)  

