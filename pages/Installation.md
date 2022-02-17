---
title: Installation 
nav: installation
nav_order: 1
---
Si vous souhaitez mettre en oeuvre notre projet sans utiliser de docker (en utilisant VS), nous vous proposons la procédure suivante :

1.	Installer Visual Studio
2.	Synchroniser le dépôt [GitHub](https://github.com/USMB-NS/VideoAnalyticsRD.git) avec VSC 
3.	Faites un git pull pour télécharger/mettre à jour votre dépôt locale depuis GitHub
4.	À présent il vous faudra installer les différentes librairies pythons énumérés ci-dessous (pip3 install exemple):
*	cv2
*	pandas
*	numpy
*	ctypes
*	datetime
*	psutil
*	threading
*	time
*	csv
*	matplotlib
*	seaborn
5.	Pour compiler et exécuter le projet il faudra utiliser la commande suivante dans un terminal :
 *DARKNET_PATH=/**votreChemin**/VideoAnalyticsRD/blocks/libraries/darknet python3 /**votreChemin**/VideoAnalyticsRD/Anal_perf.py*
