---
title: Résultats
nav: Résultats
nav_order: 3
---
Une fois que l'exécution du programme est terminé, les résultats d'analyses sont exportés dans plusieurs fichiers:
<br>
![image](csvDoc.png){: height="40px" width="30px" style="float: left; margin-right: 2em;margin-top: 2em;"}
* Le fichier extraDATA.csv qui comprend un résumé global. 
![image](expDATA.JPG){: height="40px" width="1000px" style="float: center; margin-right: 1em;"}

![image](csvDoc.png){: height="40px" width="30px" style="float: left; margin-right: 2em;"}

* Le fichier de données du CPU : extraCPU.csv qui comprend une liste de toutes les donnnées des CPU classées en colonne. 

![image](csvDoc.png){: height="40px" width="30px" style="float: left; margin-right: 2em;"}

* Le fichier de données du GPU : extraGPU.csv qui comprend une liste de toutes les donnnées du GPU. 

![image](jpegDocs.JPG){: height="300px" width="30px" style="float: left; margin-right: 2em;margin-top: 1em"}

* Les graphiques: extraCPU[1,4].jpeg et extraGPU.jpeg qui représentent les données sous forme de graphique:
<br>
![image](seabornExemple.JPG){: height="250px" width="150px" style="float: left; margin: 1em;"}
<br>
    
    * boxplot représente la distribution des données et permet de visualiser les quartiles et la médiane.
<br>
<br>
<br>
<br>
<br>

    * ecdf :"la fonction de répartion empirique" qui représente la proportion des données de manière quantitative. Ainsi on peut déterminer la densité (en ordonnée) des données correspondant au seuil (en abscisse) (exemples: on a 20% des données qui valent moins de 150, on a 80% de nos données qui valent moins de 215 )
<br>
<br>
<br>
<br>

# Interprétation de nos résultat d'étude
Pour analayser les performances de la carte nous avons choisi d'étudier l'impact de différentes résolutions d'une vidéo (1280x720px, 640x480px et 640x360px) sur le bloc de traitement obj_detect.py,que nous avons adapté de manière à ce qu'il traite l'entièreté de la vidéo (2 secondes), en utilisant le réseau de neuronne Yolo_tiny (qui est un réseau "limité"). Cette étude s'est réalisée en deux temps:
* Une première étude visant à analyser les différentes données de consommation de la carte.
* Une seconde étude focalisée sur la pertinence de détection.

Dans ces deux cas nous avons tenu à ce que la carte exécute le programme avec les mêmes conditions de performance, ainsi nous éteignions cette dernière entre chaque exécution. Nous appellerons cette condition la condition optimale.

### Notre première étude
Les résultats obtenus sont les suivants:
![image](DATAnalyseTT.PNG){: height="100px" width="1100px" style="float: center; margin-right: 1em;"}
 On a ainsi pu constater que en condition optimale d'analyse, la résolution a très peu d'impact sur les performances. En effet, lors de notre série d'étude nous n'avons pas relevé de différences majeures entre nos résultats. 

![image](Capture.PNG){: height="350px" width="600px" style="float: right ; margin: 1em;"}
<br>
<br>
 Cependant nous avons constaté que pour des conditions d'exécution différentes, les consommations peuvent fortement varier. Sur le graphiques ci-joint, réalisés avec des conditions différentes, on peut par exemple constater que la consommation des CPU avec la résolution 640x360 a nécessité moins de ressources. On ne sait comment interpréter les causes de ces variations, cependant nous tenions à les signaler.

![image](Capture.PNG){: height="350px" width="600px" style="float: left ; margin: 1em;"}
<br>
<br>
<br>
<br>
<br>
<br>
<br>

Concernant l'analyse de la consommation du GPU, on a remarqué que sa consommation est peu importante
<br>
<br>
<br>
<br>
<br>
<br>
<br>
<br>
<br>
<br>
<br>
<br>
<br>
<br>

### Notre deuxième étude
![image](AccuracyAnalyse.JPG){: height="350px" width="550px" style="float: left ; margin: 1em;"}
En relevant différents résultats d'analyse des précisions de détection on peut déduire les choses suivantes:

* Plus la résolution est bonne, moins le programme est amené à se tromper dans ses détections
* La répétabilité des valeurs de précision nous fait dire que cette caractérisitque est plutôt fidèle.

Cependant nous n'avons pas eu la possibilité de vérifier la cohérence de ces résultats. Nous aurions voulu confirmer ces derniers en développant une vidéo de sortie comprenant les blocs d'identifaications sur les véhicules mais par manque de temps nous n'avons pu le faire.
<br>
<br>
<br>
<br>
<br>

## Conclusion de nos études
D'après nos études, la résolution influt peu sur les performances de la carte mais influt sur la précision de détection. 
<br>
<br>
<br>
<br>
<br>

# Conclusion du projet
La solution que nous avons fourni est actuellement fonctionnelle et assez simple d'utilisation.
Les résultats exportables donnent assez de matières pour y effectuer des analyses. 


Pour aller plus loin, nous pourrions:
En terme de programme
* tester notre solutions sur d'autres blocs de traitements
* tenter d'exécuter notre solution avec d'autres réseaux de neuronnes

en terme d'analyse
* évaluer les performances sur d'autres blocs de traitement
* évaluer les performances avec d'autres réseaux de neuronnes
* évaluer l'impact en terme de ressources de notre "analyseur" sur le fonctionnement normal de la carte
* confirmer plus amplement les résultats de nos études (validation des identifications, valeurs de consommations)


