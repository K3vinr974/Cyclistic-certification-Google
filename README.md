# Cyclistic-certification-Google
Analyse Capstone Google Data Analytics Certification

Ce dépot contient mon analyse d'un projet proposé pour valider mon certificat de Data Analyst.

Je vous joins ma partie data (nettoyage, analyse) en SQL (BigQuery) ainsi qu'une partie visualisation sur Tableau.

# Contenue
* ### Présentation du Projet
* ### Demander
* ### Préparer
* ### Nettoyer
* ### Analyser
* ### Publier
* ### Actionner


# Présentation du projet


# Demander


# Préparer
Les données sont stockées en ligne. Elle sont au nombre de 12 fichier .csv, un pour chaque mois. Une conversion en format Excel et une première lecture des différent fichier me permet de voir l'architecture de ces données. Le nombre de ligne étant conséquent, je ne pourrais pas continuer sur excel et je vais devoir utiliser la plateforme BigQuery (SQL) ou Rstudio (R) pour pouvoir traiter tout ce jeu donnée. Après vérification que toutes les colonnes correspondent entre les différents fichiers je constate qu'il y a des champs manquant sur certaines lignes pour les champs start_station_name et end_station_name. Un nettoyage puis un contrôle de donnée sera nécessaire afin de rendre la base de donnée ROCCC. Je rajoute deux colonnes afin de pouvoir faire mon analyse par la suite: une première qui calcul le temps de la location et une seconde me permettant d'avoir le jour de la semaine correspondant au jour de la location. Je reconvertie mes fichiers en .csv afin de les transférer sur BigQuery pour un nettoyage et une analyse plus approfondie. 

# Nettoyer
Je creer un nouveau projet que je nomme ..... et un nouvelle ensemble de données que je nomme .....
''r
Create Table 
''

# Analyser


# Publier


# Actionner
