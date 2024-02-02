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
-> A COMPLETER

# Demander
-> A COMPLETER

# Préparer

Les données sont stockées en ligne. Elle sont au nombre de 12 fichier .csv, un pour chaque mois. Une conversion en format Excel et une première lecture des différent fichier me permet de voir l'architecture de ces données. Le nombre de ligne étant conséquent, je ne pourrais pas faire tout mon travail sur Excel et je vais devoir utiliser la plateforme BigQuery (SQL) ou Rstudio (R) pour pouvoir traiter tout ce jeu donnée. Mon choix se portera sur BigQuery et une visualisation sur Tableau.

![Capture d'écran depot_archive](https://github.com/K3vinr974/Cyclistic-certification-Google/assets/154596716/d43eca54-5b6e-461d-bd98-6dab772154a2)
Après vérification que toutes les colonnes correspondent entre les différents fichiers je constate qu'il y a des cellules vides sur certaines lignes pour les champs start_station_name et end_station_name. 

![Capture d'écran start_station](https://github.com/K3vinr974/Cyclistic-certification-Google/assets/154596716/6111ca75-0e18-4857-a686-4916e2f9d3e0)

![Capture d'écran end_station](https://github.com/K3vinr974/Cyclistic-certification-Google/assets/154596716/63271e53-cc25-4537-9170-12a417a87875)

Je constate également des temps de location de quelques secondes et d'autre sur plusieurs jours. 
![Capture d'écran tpscourt](https://github.com/K3vinr974/Cyclistic-certification-Google/assets/154596716/b6ea4d34-7cb1-4cc2-a529-3237a2e7a7bf)
![Capture d'écran tpslong](https://github.com/K3vinr974/Cyclistic-certification-Google/assets/154596716/8001251c-0a5d-4186-b7b2-893e246e7cd9)


Un nettoyage puis un contrôle des données sera nécessaire afin de garantir une base de donnée ROCCC. Je rajoute trois colonnes afin de pouvoir faire mon analyse par la suite: une première qui calcul le temps de la location et une seconde me permettant d'avoir le jour de la semaine correspondant au jour de la location. La troisième colonne me permet de faire le rapprochement du jour en toute lettre.

![Capture d'écran 3_col](https://github.com/K3vinr974/Cyclistic-certification-Google/assets/154596716/0566f47e-48eb-481c-a188-810aaa52a6a8)
 

![Capture d'écran formule1](https://github.com/K3vinr974/Cyclistic-certification-Google/assets/154596716/5c1ee324-363f-48f5-92a8-d3bf2f07fc6a)
 

![Capture d'écran formule2](https://github.com/K3vinr974/Cyclistic-certification-Google/assets/154596716/45975372-e328-4365-bfd7-1492b7622f70)
 

![Capture d'écran formule3](https://github.com/K3vinr974/Cyclistic-certification-Google/assets/154596716/cb556c59-e4d7-4042-9c69-8336dd01581b)
 

Je reconvertie mes fichiers en .csv afin de les transférer sur BigQuery pour un nettoyage et une analyse plus approfondie. 

![depot_csv_upload](https://github.com/K3vinr974/Cyclistic-certification-Google/assets/154596716/e8b3dabd-150f-45a5-8cd0-395003bc5304)

# Nettoyer

Je créer un nouveau projet que je nomme ..... et un nouvelle ensemble de données que je nomme ......
-> image depot bigquery

Je créé une table pour chaque fichier .csv en les nommant Janvier_23, Decembre_23. 
-> image table

Je créer ensuite une table permettant de joindre toute les tables et la nomme Annee_23.
-> image table jointe + requete jointure

Je commence à supprimer toute les lignes où il y a des valeurs null pour les champs start_station_name et end_station_name. 
-> requete suppression

Afin d'avoir des données representatif des utilisatuers je supprime les locations trop longue ( + 24h) et les locations trop courte ( - 5 minutes)
-> requete suppression

Une fois le nettoyage effectuer je peux garantir que mes données sont ROCCC:
* Fiable: 
Les données proviennent de la societé Cyclistic
* Original: 
Les données on été relevé par la société Cyclistic
* Complet: 
le jeu de donnée est sans erreur de saisie ou valeur nulle
* Actuel: 
Le jeu de donnée provient de l'année 2023, année la plus récente disponible.
* Cité: 
Les jeux de données originals peuvent être disponible depuis ce dépôt :
![Capture d'écran depot_archive](https://github.com/K3vinr974/Cyclistic-certification-Google/assets/154596716/d27fe668-0b74-4982-96f4-92792c584731)


# Analyser

Je commence par analyser le nombre d'utilisateurs occasionnel (casual) et le nombre d'utilisateurs abonnée (member). 
-> requete 

Je classe également les jours d'utilisation les plus fréquent par type d'utilisateur.
-> requete 

Je calcul le nombre de location de vélo par type de vélo et type d'utilisateur.
-> requete 

Afin d'avoir des premieres visualisation et déterminer plus facilement les tendances de location entre les membres et les occasionels, je transfère la base de donnée sur Tableau et commence mes premiers visuels.
-> requete transfer json
-> process Tableau

Je décide donc de publier mon analyse.

# Publier

Je vous joins les liens vers mes visuels Tableau et ma présentation.

-> lien analyse

# Actionner

Suite à ma publication je peux donner plusieurs recommandations afin de permettre d'accroître le nombre de clients abonnés.

* Créer une période d'abonnement sur la période....

* Créer un abonnement hebdomadaire du ... au ...

* Créer un abonnement spécifique pour les stations .... qui sont les stations les plus frequenté du réseau de Cyclistic.

* Créer un abonnement suivant un temps d'utilisation journalier

* Combiner plusieurs des précédentes recommandations


# Conclusion
Cette presentation terminé, un suivi des résultats sera nécessaire pour connaître l'impact du ou des recommandations appliqué.
