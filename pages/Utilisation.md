---
title: Utilisation
nav: Utilisation
nav_order: 2
---

Notre objectif étant de permettre l'étude des différents blocs du [projet d’analyse vidéo de monsieur Bronzino](https://github.com/USMB-NS/VideoAnalyticsRD), nous avons structuré notre programme principal (LINK) à l'aide d'une fonction d'analyse de performance qui vous permet de renseigner la vidéo, le bloc de traitement ainsi que le réseau de neuronne souhaités en argument.

![alt](Alrgorigramme1.png)

## Execution du programme principal
* On créé une instance de la classe Analyse_perf (LINK)  
* On "échantillone" notre vidéo image par image puis on récolte les caractéristiques de notre vidéo.
* On lance la prise des mesures (CPU,GPU,Mémoires) 
* On éxécute le bloc de traitement obj_detect.py [LINK]
* Lorsque la procédure du bloc de traitement est terminé, on stop la prise des mesures 
* On effectue un traitement des données (stockage dans des fichiers csv et réalisation des graphiques)

## Execution du programme d'analyse de performance
Ce programme inclut les nombreuses fonctions nous permettant d'analyser les performances du traitement. Créé sous forme de classe, ce dernier ainsi appelable dans notre main#Reformuler.
Lorsque ce dernier est appelé, il lance les threads CPU et GPU appartement réciproquement aux fichiers CPU_thread.py et GPU_thread.py.[Link] 

### La première fonction appelé par le programme principal : print_param_video()
Elle permet d'obtenir, comme son nom l'indique, les paramètres de la vidéo tel que la largeur, son poids, la hauteur et les fps. Ces paramètres sont utilisés dans le fichier principal d'analyse.

### La seconde fonction appelée par le programme principal: start()
Cette fonction permet de:
1. Récupèrer le temps à cet instant
2. Lancer la fonction CPU de psutil.cpu_percent
3. Lancer le thread du GPU
4. Lancer le thread du CPU
5. Récupère l'état de la mémoire utilisé

### La troisième fonction appelée par le programme principal: stop()
A l'inverse de la fonction start(), cette fonction permet de:
1. Récupèrer le temps à cet instant
2. Lancer la fonction CPU de psutil.cpu_percent qui arrête l'aquisition des données lancé depuis son premier appel
3. Arrête le thread du GPU
4. Arrête le thread du CPU
5. Récupère l'état de la mémoire utilisé à cet instant 

### La quatrième fonction appelée par le programme principal: t_exec()
Cette fonction effectue les différents traitement sur les données acquise précédement afin de les exporter dans le fichier principal expData.csv . 
1. Elle calcule le temps d'éxecution du programme
2. Elle met en forme les pourcentages de consomation des CPU et GPU
3. Calcul la consommation de mémoire
4. Elle exporte les données dans le fichier principal d'analyse (id, tempss, CPU%, Mémoire, GPU%, paramètres de vidéo)

### Les deux denrières fonction appelée par le programme principal: cpu_exec() et gpu_exec()
Ces fonctions ont deux utilités: 
* exporter les données d'analyse dans des fichiers spécifiques
* créer les graphiques 
La fonction cpu est quelque peu plus complexe que celle du gpu car les données inclut celles des 4 CPU et donc les représente dans différents graphique.
Ces graphiques servent à avoir une visualisation plus visuelles des consomations. Nous avons utilisé la bibliothèque Seaborn [link] pour les réaliser.

### Les autres fonctions:
#### pprint_ntuple() et print_memory()
L'utilité de ces fonctions concerne la mesure de l'état de mémoire RAM et SWAP. Par l'appel de la fonction print_memory() on appel deux fois la fonction pprint_ntuples() en précisant en argument la RAM ou la Swap afin d'effectuer une conversion des données récupéréés(àdévelopper).

#### Frames
Les fonctions frame_start(), frame_stop() et frame_exec() ont entre autre la même utilité que les fonctions start(), stop() et t_exec(). Dans nos recherches nous voulions analyser le temps de traitement par image. Ainsi nous plassion la fonction start en début de traitement de notre boucle(à bien présenter en amont et peut etre link) pour obtenir le temps initiale et, évidement, la fonction stop en fin de traitement de l'image pour calculer le temps entre ces deux instant. La fonction frame_exec() sert à:
* exporter les données dans un fichier dédié
* créer des graphiques


4. use customization options

See [docs/create-website.md](https://github.com/thecdil/bootstrap-template/blob/main/docs/create-website.md) for details!
