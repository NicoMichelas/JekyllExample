---
title: Utilisation
nav: Utilisation
nav_order: 2
---
Pour vous familiariser avec l'utilisation de notre programme, nous vous proposons dans cette section un descriptif de ce dernier.

Pour lancer une étude de performance, il vous suffit de renseigner la vidéo que vous souhaitez étudier, le bloc de traitement ainsi que le réseau de neuronne en argument de la fonction decode_loop(). 

Le programme éxécutera le bloc étudié tout en récupérant des données de performances qui seront par la suite [exportées](https://nicomichelas.github.io/JekyllExample/R%C3%A9sultats.html) sous forme d'image et de csv .

![alt](Alrgorigramme1.png)
<br>
<br>

# Description du processus des programmes
## Execution [programme principal](https://github.com/USMB-NS/VideoAnalyticsRD/blob/master/Anal_perf.py)
* On crée une instance de la classe Analyse_perf (LINK)  
* On découpe notre vidéo frame par frame puis on récupère les caractéristiques de notre vidéo.
* On lance la récupération des données (CPU,GPU,mémoires,temps) 
* On exécute le bloc étudié
* Lorsque l'exécution du blox est terminé, on arrête la récupération des données
* On effectue un traitement des données puis on exporte les différents rendus
<br>
<br>

## Execution du [programme d'analyse de performance](https://github.com/USMB-NS/VideoAnalyticsRD/blob/master/Analyse_perf.py)
Cette classe comporte de nombreuses méthodes qui nous permettent de récupérer les différentes données et de les traiter. 
Elle permet entre autres de lancer les threads CPU et GPU (réciproquement les classes [CPU_thread.py](https://github.com/USMB-NS/VideoAnalyticsRD/blob/master/CPU_thread.py) et [GPU_thread.py](https://github.com/USMB-NS/VideoAnalyticsRD/blob/master/GPU_thread.py)).

### 1. La première méthode appelée par le programme principal : print_param_video()
Elle permet d'obtenir, comme son nom l'indique, les paramètres de la vidéo (sa résolution, sa durée, le nombre de fps). 
<br>Ces paramètres sont par la suite affichés dans extraData.

### 2. La seconde méthode appelée par le programme principal: start()
Cette méthode sert de balise de lancement, elle indique que nous commençons à effectuer les différentes mesures:
* Acquérrir la date actuelle pour le calcul du temps d'exécution
* Lancer le calcul d'utilisation du CPU (la moyenne) 
* Lancer le thread du GPU
* Lancer le thread du CPU
* Récupérer l'état de la mémoire utilisée

### 3. La troisième méthode appelée par le programme principal: stop()
A l'instar de la méthode start(), stop() est également une balise dont le but est d'arrêter la prise de mesure:
* Acquérrir la date actuelle pour le calcul du temps d'exécution
* Arrêter la prise de mesure concernant la moyenne d'utilisation du CPU
* Arrêter le thread du GPU
* Arrêter le thread du CPU
* Récupérer l'état de la mémoire utilisée 

### 4. La quatrième méthode appelée par le programme principal: t_exec()
Cette méthode effectue les différents traitement sur les données acquises précédement afin de les exporter dans le fichier extraSData.csv . 
<br>Son fonctionnement est le suivant: 
* Elle calcule le temps d'éxecution du programme
* Elle met en forme les pourcentages de consomation des CPU et GPU
* Calcul la consommation de mémoire
* Elle exporte les données dans le fichier extraData (id, tempss, CPU%, Mémoire, GPU%, paramètres de vidéo)

### 5. 6. Les deux dernières fonctions appelées par le programme principal: cpu_exec() et gpu_exec()
Ces fonctions ont deux utilités: 
* exporter les données d'analyse dans des fichiers spécifiques
* créer les différents graphes
La fonction cpu est quelque peu plus complexe que celle du GPU car les données incluent celles des 4 CPU et sont ainsi représentés dans différents graphiques.
Ces graphiques servent à avoir une visualisation des consommations. Leurs caractéristiques sont expliqués dans la partie [résultat](https://nicomichelas.github.io/JekyllExample/R%C3%A9sultats.htm).

### +. Les autres fonctions:
#### pprint_ntuple() et print_memory()
L'utilité de ces fonctions concerne la mesure de l'état de mémoire RAM et SWAP. Par l'appel de la fonction print_memory() on appelle deux fois la fonction pprint_ntuples() en précisant en argument la RAM ou la Swap afin d'effectuer une conversion des données récupérées.

#### Frames
Les fonctions frame_start(), frame_stop() et frame_exec() ont à peu près la même utilité que les fonctions start(), stop() et t_exec(). Dans nos recherches nous voulions analyser le temps de traitement par image. Ainsi nous placions la fonction start en début de boucle et la fonction stop en fin de boucle afin de calculer le temps de traitement d'une frame. La fonction frame_exec() sert à:
* exporter les données dans un fichier dédié
* créer des graphiques
<br>
<br>

## Execution du thread GPU:
Lorsqu'on initialise ce thread dans le programme d'analyse de performance[link] on fait directement appel à la méthode run().
### La méthode run()
Cette méthode permet de remplir notre liste list_Gpu=[] avec des valeurs représentant la consommation actuelle du GPU grâce à la fonction gpu_tot_util() et cela tant que notre durant toute la durée du thread.

### La fonction gpu_tot_util()
Cette fonction permet d'accéder au fichier gpu.0 qui correspond à l'état du GPU en temps réel. La fonction nous renverra cette valeur.

### La méthode stop()
Comme sont nom l'indique, cette fonction arrête notre thread en envoyant une interruption. Nous effectuons par la suite un "échantillonnage" des données présente dans list_Gpu afin d'ajouter seulement une mesure sur 100 dans notre nouvelle liste list_Gpu_tiny. Ceci nous permet d'éviter d'avoir un trop grand nombre de valeurs à traiter.
<br>
<br>

## Execution du thread CPU:
Lorsqu'on initialise ce thread dans le programme d'analyse de performance[link] on fait directement appel à la méthode run().
### La méthode run()
Très similaire à la méthode run du thread GPU, à la différence que nous avons 4 listes au lieu d'une (une pour chaque coeur du CPU).

### La fonction cpu_tot_util()
Cette fonction utilise la fonctcion cpu_percent de la bibliothèque psutil qui permet de récupérer l'état des CPU sous formes de liste toutes les 0,1s.

### La méthode stop()
Egalement très similaire à la méthode stop du thread GPU.
<br>
<br>

### Note importante
La carte n'est pas capable de faire tourner d'autres réseaux que le Yolo_tiny. Faute de temps nous n'avons pas développer d'avantage sur ce point.