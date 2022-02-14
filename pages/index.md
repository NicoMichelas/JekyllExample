---
title: Contexte

---

Dans le cadre du projet de recherche et développement de ce semestre 9, au sein de Polytech Annecy, nous avons décidé Nicolas MICHEL et Alexis GIUSEPPI de travailler sur ce sujet d’analyse vidéo. Sous la tutelle des professeurs chercheurs Hervé VERJUS et Francesco BRONZINO, ce projet c'est déroulé du 13/10/2021 au 18/02/2021. Ce document à pour objectif de présenter notre travail effectué afin que tout le monde puisse comprendre et/ou utiliser ce dernier (cf onglets [d'installation](http://127.0.0.1:4000/video_analyse_performance_report/Installation.html) et [d'utilisation](http://127.0.0.1:4000/video_analyse_performance_report/Utilisation.html) )

## Objectif
Tiré du [projet d’analyse vidéo de monsieur Bronzino](https://github.com/USMB-NS/VideoAnalyticsRD), ce projet à pour objectif d'évaluer les caractéristiques quantifiables d’entrée et de sortie lors d’un traitement vidéo.
Suite au déroulement de nos recherches, ce projet c'est principalement basé sur l'analyse des performance du bloc [obj-detect](https://github.com/USMB-NS/VideoAnalyticsRD/blob/master/blocks/obj_detect.py). 
![alt](illustration1.png){: width="1150" }

Nous avons donc mis en place différentes fonctions permettant d'analyser:
* le temps d'éxécution du traitement
* la consommation des processeurs
* la consommation de la carte graphique
* la consommation de la mémoire

Le programme est structuré de manière à ce qu'à l'avenir, il puisse traiter aisément d'autres blocs. Sa structure est détaillé en détail dans l'onglet [d'utilisation](http://127.0.0.1:4000/video_analyse_performance_report/Utilisation.html).

Les résultats de notre étude, réalisé sur une Jetson Nano sont présent dans l'onglet [de résultat](http://127.0.0.1:4000/video_analyse_performance_report/R%C3%A9sultats.html).
