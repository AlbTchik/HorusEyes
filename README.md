# L'Oeil d'Horus

**Date de réalisation :** Septembre-Decembre 2022, projet personnel
<br> <br>
**Cadre du projet :** Reconnaissance automatique d'objets sur des images satellites.
<br> <br>
**Mots-clés :** Neural Networks, Computer Vision, Satellite Imagery, Civilian & Military Targets
<br>
## Présentation du projet
Ce projet présente le développement d'un détecteur automatique d'avions, à partir d'images satellites, en utilisant un modèle de Deep Learning.
Le but est de réaliser une étude scientifique aboutissant sur un modèle fonctionnel.
Dans celle-ci, on cherchera a mettre en place un modèle puis on comparera les performances obtenus avec celles de l'état de l'art, en émettant des critiques et en proposant des pistes d'interprétation.
<br><br>
J'ai réalisé ce projet sur mon temps libre, pendant le premier trimestre de mon Mastère Spécialisé en Intelligence Artificelle à Télécom Paris [[1]](#ref1).
C'est un sujet qui présente beaucoup d'intérêt a mes yeux. Laissez moi vous expliquer pourquoi. 
<br>
## Contexte
Il y a plus de deux millénaires, Sun Tzu énonce le principe suivant : "l'opportunité de vaincre l'ennemi est fourni par l'ennemi lui-même" [[2]](#ref2).
Cela illustre bien la nécessitée d'observer le dispositif adverse, afin d'y détecter une faille.
Historiquement, cette mission était remplie par des régiments de cavalerie légère, appelée les Eclaireurs.
Ils étaient les yeux et les oreilles de l'armée, informant le commandement des moindres mouvements de l'ennemi.  

Au travers de l'histoire, on peut observer de nombreuses batailles perdues par la faute d'une reconnaissance insuffisante. Celle-ci ont souvent été gagnés, par l'autre camp, grace a un plan bien construit, basé sur une réelle faiblesse. On pourrai citer la bataille de Satala, en 298, où l'Empereur Romain lui-même s'est déguisé en commerçant pour observer le camp Sassanide [[3]](#ref3). Ou encore les nombreuses embuscades tendus par les nomades, comme celle de Pressburg, qui a vu les Hongrois triompher du Saint-Empire [[4]](#ref4).
<br>
<br>
De nos jours, cette tâche s'est adaptée à la guerre moderne et est réalisée en utilisant des drones et des satellites.
Ceux-ci génèrent de nombreuses images montrant l'état des zones observées. Des analystes bien entrainés peuvent ensuite les étudier, pour en extraire les informations d'intelligence stratégique, qui vont permettre au commandement de prendre les décisions adaptés. Les rapports de reconnaissance suivent les normes au Standard OTAN, définies dans la fiche STANAG 3596 établie en 2003 [[5]](#ref5).
<br>
## Stratégie et hypothèses de l'étude
<br>

## Problématique
Il y a une quantité très importante de données a analyser. Il faut environ une demi-journée à un analyste pour évaluer l'état d'un petit aéroport. De plus ces données sont renouvelées très rapidement, souvent une fois par jours, parfois plus.
Afin d'aider l'opérateur a prendre une décision rapide, on veut lui proposer une évaluation automatique des sites d'interêts.
Ce qui pose la question suivante : 
<br> <br>
**Comment modéliser et évaluer les performances d'un algorithme de reconnaissance d'objets appliqué a l'imagerie satellite et ses contraintes ?**
<br>

## Etat de l'art 
<br>


## Bibliographie 

<a name="ref1">[1]</a> : [Contenu de la formation MS IA à Télécom](https://www.telecom-paris.fr/fr/masteres-specialises/formation-intelligence-artificielle)  
<a name="ref2">[2]</a> : [Résumé et critique de "L'Art de la Guerre"](https://www.getstoryshots.com/fr/books/the-art-of-war-summary/)  
<a name="ref3">[3]</a> : [Guerre Romano-Sassanide, Bataille de Satala, 298 après J.-C.](https://www.youtube.com/watch?v=T2571JUYAlI)  
<a name="ref4">[4]</a> : [Guerre Hongroise-Germanique, Bataille de Pressburg, 907 après J.-C.](https://www.youtube.com/watch?v=VHUSCs4Nacg)  
<a name="ref5">[5]</a> : [Standard OTAN, STANAG 3596 (2003)](https://infostore.saiglobal.com/en-us/standards/stanag-3596-2003-735625_saig_nato_nato_1786746/)

