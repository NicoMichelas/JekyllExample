---
title: Utilisation
nav: Utilisation
nav_order: 2
---
Pour vous familiariser avec l'utilisation de notre programme, nous vous proposons ce descriptif qui vous permettra d'utiliser et comprendre le fonctionnement de ce dernier.

Pour lancer une étude de performance, il vous suffit de renseigner la vidéo, le bloc de traitement ainsi que le réseau de neuronne en argument de la fonction du programme prnicipale. Ainsi le programme éxécutera le bloc de traitement en parallèle d'une récupération des données de la carte qui sont [exportés](https://nicomichelas.github.io/JekyllExample/R%C3%A9sultats.html) en fin de programme .


![alt](Alrgorigramme1.png)

## Execution [programme principal](https://github.com/USMB-NS/VideoAnalyticsRD/blob/master/Anal_perf.py)
* On créé une instance de la classe Analyse_perf (LINK)  
* On "échantillone" notre vidéo image par image puis on récupère les caractéristiques de notre vidéo.
* On lance la récupérations des données (CPU,GPU,Mémoires) 
* On éxécute le bloc de traitement
* Lorsque la procédure du bloc de traitement est terminé, on stop la récupérations des données
* On effectue un traitement des données (stockage dans des fichiers csv et réalisation des graphiques)

## Execution du [programme d'analyse de performance](https://github.com/USMB-NS/VideoAnalyticsRD/blob/master/Analyse_perf.py)
Ce programme inclut les nombreuses fonctions nous permettant de récupérer les données de performances du traitement. 

0. Lorsque ce programme est appelé, il lance les threads CPU et GPU appartement réciproquement aux fichiers [CPU_thread.py](https://github.com/USMB-NS/VideoAnalyticsRD/blob/master/CPU_thread.py) et [GPU_thread.py](https://github.com/USMB-NS/VideoAnalyticsRD/blob/master/GPU_thread.py).

### 1. La première fonction appelé par le programme principal : print_param_video()
Elle permet d'obtenir, comme son nom l'indique, les paramètres de la vidéo tel que la largeur, son poids, la hauteur et les fps. Ces paramètres sont utilisés dans le fichier principal d'analyse.

### 2. La seconde fonction appelée par le programme principal: start()
Cette fonction permet de:
* Récuperer le temps à cet instant
* Lancer la fonction CPU de psutil.cpu_percent
* Lancer le thread du GPU
* Lancer le thread du CPU
* Récuperer l'état de la mémoire utilisée

### 3. La troisième fonction appelée par le programme principal: stop()
A l'inverse de la fonction start(), cette fonction permet de:
* Récuperer le temps à cet instant
* Lancer la fonction CPU de psutil.cpu_percent qui arrête l'aquisition des données lancée depuis son premier appel
* Arrêter le thread du GPU
* Arrêter le thread du CPU
* Récuperer l'état de la mémoire utilisée 

### 4. La quatrième fonction appelée par le programme principal: t_exec()
Cette fonction effectue les différents traitement sur les données acquises précédement afin de les exporter dans le fichier principal expData.csv . Son fonctionnement est le suivant: 
* Elle calcule le temps d'éxecution du programme
* Elle met en forme les pourcentages de consomation des CPU et GPU
* Calcul la consommation de mémoire
* Elle exporte les données dans le fichier principal d'analyse (id, tempss, CPU%, Mémoire, GPU%, paramètres de vidéo)

### 5. 6. Les deux dernières fonctions appelées par le programme principal: cpu_exec() et gpu_exec()
Ces fonctions ont deux utilités: 
* exporter les données d'analyse dans des fichiers spécifiques
* créer les graphiques 
La fonction cpu est quelque peu plus complexe que celle du GPU car les données incluent celles des 4 CPU et sont ainsi représenté dans différents graphiques.
Ces graphiques servent à avoir une visualisation des consomations. Leurs caractéristiques sont expliqués dans la partie [résultat](https://nicomichelas.github.io/JekyllExample/R%C3%A9sultats.htm).

### +. Les autres fonctions:
#### pprint_ntuple() et print_memory()
L'utilité de ces fonctions concerne la mesure de l'état de mémoire RAM et SWAP. Par l'appel de la fonction print_memory() on appel deux fois la fonction pprint_ntuples() en précisant en argument la RAM ou la Swap afin d'effectuer une conversion des données récupéréés(àdévelopper).

#### Frames
Les fonctions frame_start(), frame_stop() et frame_exec() ont entre autre la même utilité que les fonctions start(), stop() et t_exec(). Dans nos recherches nous voulions analyser le temps de traitement par image. Ainsi nous plassion la fonction start en début de traitement de notre boucle(à bien présenter en amont et peut etre link) pour obtenir le temps initiale et, évidement, la fonction stop en fin de traitement de l'image pour calculer le temps entre ces deux instant. La fonction frame_exec() sert à:
* exporter les données dans un fichier dédié
* créer des graphiques


## Execution du thread GPU:
Lorsque l'on lance ce thread dans le programme d'analyse de performance[link] on fait directement appel à la fonction run().
### La fonction run()
Cette fonction créée une liste list_Gpu=[] ainsi qu'une variable gpu_calc initialisé à 1 qui permet d'entrer dans la boucle qui ajoute la consommation actuelle du GPU dans notre list_Gpu grâce à la fonction gpu_tot_util() et cela tant que notre variable gpu_calc vaut 1.

### La fonction gpu_tot_util()
Cette fonction permet d'accéder au fichier gpu.0 qui correspond à l'état du GPU en temps réel. Ainsi on récupère cette valeur qu'on retourne grâce à la variable load.

### La fonction stop()
Comme sont nom l'indique, cette fonction arrête notre thread grâce à la variable gpu_calc que l'on passe à 0 et qui va en parallèle stopper la boucle while présente dans la fonction run(). Ensuite on effectue un "échantillonnage" des données présente dans list_Gpu afin d'ajouter seulement une mesure sur 100 dans notre nouvelle liste list_Gpu_tiny. Ceci nous permet d'éviter d'avoir un trop grand nombre de valeur à exploiter par la suite.


## Execution du thread CPU:
Lorsque l'on lance ce thread dans le programme d'analyse de performance[link] on fait directement appel à la fonction run().
### La fonction run()
On commence par créé 5 listes, dont une totale et 4 dédiés à nos 4 CPU et une variable cpu_calc initilisé à 1 pour servir de condition à notre boucle while qui suit. Dans cette boucle, on récupère l'état de nos CPU à l'aide de la fonction cpu_tot_util() que l'on ajoute dans la liste totale. Puis on ajoute dans les différentes listes les valeurs de cpu correspondante.

### La fonction cpu_tot_util()
Cette fonction utilise la fonctcion cpu_percent de la bibliothèque psutil qui permet de récupérer l'état des CPU sous formes de liste grâce au paramètre percpu=True et 0,1 en seconde qui est le temps d'acquisition minimum possible.

### La fonction stop()
Premièrement, on initialise la varaible cpu_calc à 0 pour stopper la boucle de la fonction run(). Ensuite on calcul la consommation moyenne de chaque CPU ainsi que la consommation moyenne totale.

.