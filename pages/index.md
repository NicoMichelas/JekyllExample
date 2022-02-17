---
---
# Introduction
Ce document à pour objectif de présenter notre projet d'analyse des performances (consommation de CPU,GPU et mémoire) d'une JetsonNano lors d'analyse vidéo.
Dans ce rapport vous pourrez ainsi découvrir des explications détaillés sur ce projet afin que vous puissiez comprendre et/ou l'utiliser
La structure de ce document est la suivante:
    * un protocole [d'installation](http://127.0.0.1:4000/video_analyse_performance_report/Installation.html) qui précise les étapes et points importants à prendre en compte pour mettre en place votre matériel: JetsonNano.
    * un protocle [d'utilisation](http://127.0.0.1:4000/video_analyse_performance_report/Utilisation.html)) qui présente la procédure d'éxécution du programme ainsi que les spécificités de chaques fichiers utilisés.
    * un présentation des [résultats](http://127.0.0.1:4000/video_analyse_performance_report/Utilisation.html)) obtenus lors d'une exécution ainsi qu'une présentation des résultats d'étude que nous avons menée.

# Contexte
Dans le cadre du projet de recherche et développement de notre formation SNI au sein de Polytech Annecy, nous avons décidé Nicolas MICHEL et Alexis GIUSEPPI de travailler sur ce sujet d’analyse vidéo. Sous la tutelle des professeurs chercheurs Hervé VERJUS et Francesco BRONZINO, ce projet c'est déroulé du 13/10/2021 au 18/02/2021.  
Tiré du [projet d’analyse vidéo de monsieur Bronzino](https://github.com/USMB-NS/VideoAnalyticsRD), ce projet à pour objectif d'évaluer les caractéristiques quantifiables d’entrée et de sortie d’un traitement vidéo. L'analyse de vidéo est principalement tourné vers le domaine du traffic automobile ainsi les blocs de traitements utilisé sont tel que de la détection d'objet, du calcul de trajectoire, de la détection de couleur de véhicule,...

## Le projet
![alt](illustration1.png){: width="1150" }
Suite au déroulement de nos recherches, ce projet c'est principalement basé sur l'analyse des performances de la carte par l'utilisation du bloc de traitement [obj-detect](https://github.com/USMB-NS/VideoAnalyticsRD/blob/master/blocks/obj_detect.py). 
Nous avons structuré le programme de manière à ce que son [utilisation](http://127.0.0.1:4000/video_analyse_performance_report/Utilisation.html). soit simple et rapide. De ce fait, dans le programme principale, vous avez juste à renseigner votre vidéo, votre réseau de neuronne ainsi que le bloc de traitement en argument de la fonction principale. Une fois exécuté, le programme exécute les différents sous programmes qui inclut les solutions suivantes:
* Calcul du temps d'éxécution 
* Calcul de la consommation des processeurs
* Calcul de la consommation de la carte graphique
* Calcul de la consommation de la mémoire
Finalement, ces données sont [exportés](http://127.0.0.1:4000/video_analyse_performance_report/Utilisation.html) dans différents fichiers qui vous permettront d'obtenir une vision global des performances utilisés.

