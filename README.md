de# Cyclistic-certification-Google
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

Les données sont stockées en ligne. Elle sont au nombre de 12 fichier .csv, un pour chaque mois. Une conversion en format Excel et une première lecture des différent fichier me permet de voir l'architecture de ces données. Le nombre de ligne étant conséquent, je ne pourrais pas faire tout mon travail sur Excel et je vais devoir utiliser la plateforme BigQuery (SQL) ou Rstudio (R) pour pouvoir traiter tout ce jeu donnée. Mon choix se portera sur BigQuery et une visualisation sur Tableau.

Après vérification que toutes les colonnes correspondent entre les différents fichiers je constate qu'il y a des champs manquant sur certaines lignes pour les champs start_station_name et end_station_name. 

Un nettoyage puis un contrôle de donnée sera nécessaire afin de garantir une base de donnée ROCCC. Je rajoute deux colonnes afin de pouvoir faire mon analyse par la suite: une première qui calcul le temps de la location et une seconde me permettant d'avoir le jour de la semaine correspondant au jour de la location.

Je reconvertie mes fichiers en .csv afin de les transférer sur BigQuery pour un nettoyage et une analyse plus approfondie. 

# Nettoyer

Je créer un nouveau projet que je nomme ..... et un nouvelle ensemble de données que je nomme ......

 Je créé une table pour chaque fichier .csv en les nommant Janvier_23, Decembre_23. 

Je créer ensuite une table permettant de joindre toute les tables et la nomme Annee_23.

Je commence à supprimer toute les lignes où il y a des valeurs null pour les champs start_station_name et end_station_name. 


Je commence une pré-analyse en classant le temps de location par ordre décroissant


Des temps de location de plus de ... jours ressorte. Afin de pouvoir analyser une base de donnée ROCCC je décide d'enlever toute les lignes de location dépassant plus de 24h.


Une fois le nettoyage effectuer je peux garantir que mes données sont ROCCC:
* 1
* 2
* 3
* 4

# Analyser

Je commence par analyser le nombre d'utilisateurs occasionnel (casual) et le nombre d'utilisateurs abonnée (member). 

Je classe également les jours d'utilisation les plus fréquent par type d'utilisateur.

Je calcul le nombre de location de vélo par type de vélo et type d'utilisateur.

Afin d'avoir un premier visuel et déterminer plus facilement les tendances de location entre les membres je transfère la base de donnée sur Tableau et commence mes premier visuel.

Des premières tendances se font voir.



Je décide donc de publier mon analyse.

# Publier

Je vous joins les liens vers mes visuels Tableau et ma présentation.



# Actionner
