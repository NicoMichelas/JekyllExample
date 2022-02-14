---
title: Utilisation
nav: Utilisation
nav_order: 2
---

Notre objectif étant de permettre l'étude des différents blocs du [projet d’analyse vidéo de monsieur Bronzino](https://github.com/USMB-NS/VideoAnalyticsRD), nous avons structuré notre programme principal (LINK) à l'aide d'une fonction d'analyse de performance qui vous permet de renseigner la vidéo, le bloc de traitement ainsi que le réseau de neuronne souhaités en argument.

![alt](Alrgorigramme1.png)

## Execution du programme
* On créé une instance de la classe Analyse_perf (LINK)  
* On "échantillone" notre vidéo image par image puis on récolte les caractéristiques de notre vidéo.
* On lance la prise des mesures (CPU,GPU,Mémoires) avant d'éxécuter le bloc de traitement obj_detect.py [LINK]
* Lorsque la procédure du bloc de traitement est terminé, on stop la prise des mesures 
* On effectue un traitement des données (stockage dans des fichiers csv et réalisation des graphiques)

Cette fonction fait ainsi appel

1. create repository from the template
2. edit _config.yml
3. edit content pages
4. use customization options

See [docs/create-website.md](https://github.com/thecdil/bootstrap-template/blob/main/docs/create-website.md) for details!
