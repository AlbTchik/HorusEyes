# L'Oeil d'Horus

**Date de réalisation :** Septembre-Janvier 2023, projet personnel  
<br>
**Cadre du projet :** Reconnaissance automatique du type d'aéronefs sur des images satellites.  
<br>
**Mots-clés :** Réseaux de Neurones, Vision par Ordinateur, Imagerie Satellite, Cibles civiles et militaires  

## Présentation du projet
Ce projet a été réalisée sur mon temps libre, pendant mon Mastère Spécialisé en Intelligence Artificelle à Télécom Paris [[1]](#ref1).  
Celui-ci présente le développement d'un détecteur automatique d'avions à partir d'images satellites en utilisant un modèle d'apprentissage profond.
Vous trouverez ici une étude scientifique aboutissant sur une comparaison de modèles fonctionnels.
Dans celle-ci, on cherchera a mettre en place plusieurs modèles puis on comparera leurs performances avec celles de l'état de l'art, en émettant des critiques et en proposant des pistes d'interprétation. Commençons déja par une petite mise en contexte.  

## Contexte  
On cherche ici a démontrer l'importance du renseignement pour les armées, ainsi que son rôle dans la mise en place d'une stratégie pertiente. En guise d'introduction, on pourra réfléchir a la phrase suivante, énoncée dans l'Art de la Guerre[[2]](#ref2), de Sun Tzu : "l'opportunité de vaincre l'ennemi est fourni par l'ennemi lui-même". Celle-ci illustre bien la nécessitée d'observer le dispositif adverse afin d'y détecter une faille, et met en valeur l'importance de la prise d'information dans la victoire.  

### Le renseignement, un atout précieux  
On peut déja ségmenter le sujet en deux aspects, les renseignements nous possédons sur l'ennemi, et ceux que l'ennemi possède sur nous.  
Afin d'avoir une vue complète de la situation, il est nécessaire de subdiviser encore le problème, en définissant des sous-catégories propres à chacun des référentiels. Ainsi, on définit les renseignements que nous possèdons sur l'ennemi et ceux que l'on pense qu'il possède sur nous, de même, on définit les renseignements que l'ennemi possède sur nous, et ceux qu'il pense que nous possédons sur lui. L'analyse de ces quatre quantitées est essentielle pour appréhender le succès ou l'échec des plans mis en oeuvre. Interessons nous maintenant aux élements de notre référentiel. Les deux paragraphes qui vont suivre explorerons les avantages que l'on peut tirer d'une reconnaissance efficace et les dangers qui apparaissent lorsque celle-ci est négligée.  

On peut dès lors deviner que la capacité a dissimuler des informations est cruciale pour la mise en oeuvre d'une stratégie. Mais c'est d'abord en observant les failles que l'on pourra mettre en place un dispositif adapté, qu'il faudra ensuite dissimuler efficacement. Ainsi l'acquisition des renseignements est primordiale en ce qui concerne l'établissement d'une stratégie pertiente. Pour illustrer cela, on peut citer la bataille de Satala[[3]](#ref3), en 298, où l'Empereur Romain a observé le camp Sassanide de l'intérieur, déguisé en commerçant. Ou l'embuscade de Pressburg[[4]](#ref4), en 907, qui a vu les Hongrois anéantir une armée du Saint-Empire Germanique par une retraite feinte, menant à un piège.  

A l'opposée, l'histoire nous propose une multitude de batailles perdues a cause d'un mauvais usage des renseignements. Dans chacuns de ces cas, les informations possédés n'étaient pas conforme à la réalité, causant ainsi un problème de perception. Il arrive que nos secrets, que nous pensions a l'abri, soient finalement pleinement visibles, ou que nous négligions suffisement la reconnaissance pour que l'information cruciale nous échappe. Une situation de ce genre s'est présentée lors des batailles de Iéna-Auerstaedt[[5]](#ref5), en 1806, où Napoléon ordonne la concentration des corps d'armée au mauvais endroit, le désastre étant évité de justesse grâce à la bravoure du 3ème corps et du Maréchal Davoult.  

On comprend, dès lors, qu'une erreur stratégique est inévitable lorsque des décisions sont prises sur la base d'informations incorrectes. On voit ainsi que la capacité a obtenir du renseignement fiable est déterminante dans l'établissement d'une supériorité sur le terrain. Et même si la gloire revient souvent aux personnes qui implementent  le plan, il ne faut pas oublier que, quelque soit la situation, les informations pertinentes sont toujours à la base des stratégies victorieuses.  

### Le renseignement en pratique  
Historiquement, la prise de renseignement était réalisée par les éclaireurs, des régiments de cavalerie légère. De nos jours, cette tâche s'est adaptée à la guerre moderne, et est décomposé en 4 niveaux : Humain, Electromagnétique, Image et Cyber. On peut citer les 3 satellites CERES[[6]](#ref6), lancés récemment et chargés de collecter du renseignement d'origine électromagnétique. Pour ce projet, nous allons nous restreindre à une étude sur la partie Imagerie. Celle-ci est principalement réalisée par des drones et des satellites. Par exemple, l'OTAN possède actuellement 5 RQ-4 Global Hawk[[7]](#ref7), dont les optiques sont capables de surveiller l'Ukraine depuis la Roumanie et la Mer Noire. La France dispose également, grâce a Airbus, de la constellation des 2 satellites Pléiades[[8]](#ref8), capable de photographier jusqu'a 20km de terrain avec une précision de 50cm. 

En pratique, ces systèmes génèrent de nombreuses données. Et il est necessaire d'en extraire les informations d'intelligence stratégique, par des moyens humains ou algorithmiques. Une fois la vercité de ces informations attestée, elles sont transmises au commandement dans des rapports. Pour l'Armée Française et ses alliés, les rapports de reconnaissance suivent les normes au Standard OTAN, définies dans le document STANAG 3596[[9]](#ref9), établi en 2003.  

## Stratégie et hypothèses de l'étude
Le STANAG 3596 définie une importante quantité de cibles ainsi que plusieurs niveaux permettant de fournir une évaluation exploitable de leur état. Pour ce projet, nous allons nous concentrer sur les objets de type "aéronefs".
Les images utilisé seront prise selon un angle NADIR.
Données optiques
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

_ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ 

La suite de ces recherches n'est pas disponible dans sa version publique.
_ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ 


Il a été décidé que les techniques utilisées et leurs interprétations des résultats ne seraient pas dévoilés. Cependant, vous pouvez quand même observer les graphiques obtenus lors de l'entrainement d'un modèle pour la détection d'avions militaires américain. La précision étant supérieur à 95% sur les données de test, ces résultats permettent de repousser significativement les limites de l'état de l'art disponible publiquement : 

![EfficientNetV2L_0 9959_0 0095](https://user-images.githubusercontent.com/90097422/204082669-658562e3-bfe7-43ad-a545-48bd243e01f6.png)

![EfficientNetV2L_0 9959_0 0095(1)](https://user-images.githubusercontent.com/90097422/204082672-23b89528-88e6-45f0-9b1d-3a3c99e4275b.png)

![exemple F-4 Phantom](https://user-images.githubusercontent.com/90097422/216322917-d1b89fc9-dcf9-47ce-ad76-de1be410d55d.png)

![SUV_041_jpg rf daf1073e2f5cb4630bd7d1d996b2ae41](https://user-images.githubusercontent.com/90097422/215987708-336547bc-ebd9-4fa8-aad5-de1af5e5d43f.jpg)


Si vous souhaitez plus d'informations, vous pouvez demander l'accès a l'intégralité de mes recherches via l'adresse suivante : albantchik@gmail.com


## Bibliographie non scientifique

<a name="ref1">[1]</a> : [Contenu de la formation MS IA à Télécom](https://www.telecom-paris.fr/fr/masteres-specialises/formation-intelligence-artificielle)  
<a name="ref2">[2]</a> : [Résumé et critique de "L'Art de la Guerre"](https://www.getstoryshots.com/fr/books/the-art-of-war-summary/)  
<a name="ref3">[3]</a> : [Guerre Romano-Sassanide, Bataille de Satala, 298 après J.-C.](https://www.youtube.com/watch?v=T2571JUYAlI)  
<a name="ref4">[4]</a> : [Guerre Hongro-Germanique, Bataille de Pressburg, 907 après J.-C.](https://www.youtube.com/watch?v=VHUSCs4Nacg)  
<a name="ref5">[5]</a> : [Batailles de Iéna-Auerstaedt, 1806 après J.-C.](https://www.youtube.com/watch?v=odPUHTJO8to)  
<a name="ref6">[6]</a> : [Ecoute électromagnétique, Constellation CERES](https://www.defense.gouv.fr/drm/actualites/renseignement-dorigine-electromagnetique-satellites-ceres-france-se-dote-dun-systeme-unique-europe)  
<a name="ref7">[7]</a> : [Drone HALE (Haute Altitude, Longue Endurance) RQ-4 Global Hawk](https://www.avionslegendaires.net/2022/10/actu/loeil-volant-des-allies/?fbclid=IwAR3BfqGRQXVCfEkrNRzq246XAnPmke6V6o_yU0kvRv0cZ_pFD8Ucmfd5fHQ)  
<a name="ref8">[8]</a> : [Imagerie satellite, Constellation Pléiades](https://www.intelligence-airbusds.com/imagery/constellation/pleiades/)  
<a name="ref9">[9]</a> : [STANAG 3596, Standard OTAN (2003)](https://infostore.saiglobal.com/en-us/standards/stanag-3596-2003-735625_saig_nato_nato_1786746/)  

