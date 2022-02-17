---
---
![alt](Procss.JPG){: height="150px" width="350px" style="float: right ; "}

# Introduction
<br>
Ce document à pour objectif de présenter notre projet d'analyse des performances (consommation en temps, mémoire, utilisation du GPU et du CPU) de différents blocs d'analyse vidéo en utilisant une Jetson nano.
<br>
<br>Dans ce rapport vous aurez l'occasion de vous familiariser avec l'ensemble de ce projet.
Vous trouverez différentes rubriques dans ce document, à savoir:
* un protocole [d'installation](https://nicomichelas.github.io/JekyllExample/Installation.html) qui précise les étapes les plus importantes afin de mettre en oeuvre ce projet.
* un protocle [d'utilisation](https://nicomichelas.github.io/JekyllExample/Utilisation.html) qui présente la procédure d'éxécution du programme ainsi que les spécificités des différentes fonctions et scripts du projet.
* un présentation des [résultats](https://nicomichelas.github.io/JekyllExample/R%C3%A9sultats.html) obtenus lors d'une exécution type suivi d'une présentation de résultats obtenus suite à une étude que nous avons mené.

# Contexte
Dans le cadre de ce projet de recherche et développement ancré dans notre formation au sein de Polytech Annecy-Chambéry, nous avons décidé (Nicolas MICHEL et Alexis GIUSEPPI) de travailler sur ce sujet d’analyse vidéo sous la tutelle des professeurs chercheurs Hervé VERJUS et Francesco BRONZINO, ce projet s'est déroulé du 13/10/2021 au 18/02/2021.  
Tiré du [projet d’analyse vidéo de monsieur Bronzino](https://github.com/USMB-NS/VideoAnalyticsRD), ce projet a pour objectif d'évaluer les caractéristiques quantifiables en entrée et en sortie d’un traitement vidéo. L'analyse vidéo dans ce projet est principalement orienté vers le domaine du trafic automobile.
<br>Il en découle que les blocs de traitement utilisés sont de la détection d'objet, du calcul de trajectoire, de la détection de couleur de véhicule,...
![alt](Processus.JPG){: height="300px" width="600px" style="float: right ; margin: 1em;"}
## Le projet

Suite à une première période de recherche et de prise en main du projet, nous nous sommes principalement intéressé à l'analyse des performances de la carte sur l'utilisation du bloc de traitement [obj-detect](https://github.com/USMB-NS/VideoAnalyticsRD/blob/master/blocks/obj_detect.py). 
Le programme a été structuré de manière à ce que son [utilisation](https://nicomichelas.github.io/JekyllExample/Installation.html) soit la plus simple possible. 
<br>De ce fait l'analyse d'un bloc se fait très simplement, vous avez juste à renseigner votre vidéo, votre réseau de neuronne ainsi que le bloc de traitement que vous souhaitez analyser. 
<br><br>Une fois exécuté, le programme fait appel à nos scripts qui permettent :
* Le calcul du temps d'éxécution 
* Le calcul de la consommation des processeurs
* Le calcul de la consommation de la carte graphique
* Le calcul de la consommation de la mémoire (RAM/Swap)
Finalement, ces données sont [exportés](https://nicomichelas.github.io/JekyllExample/Installation.html) dans différents fichiers qui vous permettront d'obtenir une vision global des performances utilisés.

