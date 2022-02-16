---
title: Résultats
nav: Résultats
nav_order: 3
---
Pour étudier les résultats de nos analyses, nous avons créé plusieurs fichiers:
<br>
![image](csvDoc.png){: height="40px" width="30px" style="float: left; margin-right: 2em;margin-top: 2em;"}
* Le fichier principal d'analyse : expDATA.csv qui comprend un résumé global de nos performances. 
![image](expDATA.JPG){: height="40px" width="1000px" style="float: center; margin-right: 1em;"}

![image](csvDoc.png){: height="40px" width="30px" style="float: left; margin-right: 2em;"}

* Le fichier de données du CPU : expCPU.csv qui comprend une liste de toutes les donnnées des CPU classée en colonne. 

![image](csvDoc.png){: height="40px" width="30px" style="float: left; margin-right: 2em;"}

* Le fichier de données du GPU : expGPU.csv qui comprend une liste de toutes les donnnées du GPU. 

![image](jpegDocs.JPG){: height="300px" width="30px" style="float: left; margin-right: 2em;margin-top: 1em"}

* Les graphiques: extraCPU[1,4].jpeg et extraGPU.jpeg qui représentent les données sous forme de graphique:
<br>
![image](seabornExemple.JPG){: height="250px" width="150px" style="float: left; margin: 1em;"}
<br>
    
    * boxplot : qui représente la distribution des données et permet de visualiser les quartiles et la médiane.
<br>
<br>
<br>
<br>
<br>

    * ecdf : la "fonction de répartion empirique" qui représente la proportion des données de manière quantitatives. Ainsi on peut déterminer la densité (en ordonnée) des données correspondant au seuil (en abscisse) (exemples: on a 20% des données qui valent moins de 150, on a 80% de nos données qui valent moins de 215 )
<br>
<br>
<br>
<br>

# Interprétation de nos résultat d'étude
L'objectif de notre projet d'étude était d'analayser les performances de la carte. Ainsi nous avons étudié l'impact de la résolution de vidéo sur le bloc de traitement obj_detect.py par le biais du réseau de neuronne Darknet. Cette étude s'est réalisé en deux temps:
* Une première étude visant à analyser les différentes données de consommation de la carte.
* Une seconde étude focalisé sur la pertinance de détection.

Dans ces deux cas nous avons tenu à ce que la carte exécute le programme avec les mêmes conditions de performance, ainsi nous éteignions cette dernière entre chaque exécution. 

### Notre première étude
![image](DATAnalyseTotal.PNG){: height="100px" width="1100px" style="float: center; margin-right: 1em;"}
A l'aide des résultats obtenus, nous avons comparer ces données dans un fichier excel. On a ainsi pu constater que:
* le temps d'éxécution n'était pas réellement impacté par la résolution. De plus, ce temps varie selon les exécution, on pense qu'il est ainsi difficile d'évaluer sa pertinence.


### Présentation de nos résultats