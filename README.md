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
## Scénario
Vous êtes un analyste de données junior travaillant dans l'équipe d'analystes marketing de Cyclistic, une société de vélos en libre-service à Chicago. Le directeur du marketing estime que le succès futur de l'entreprise dépend de la maximisation du nombre d'adhésions annuelles. Par conséquent, votre équipe veut comprendre comment les cyclistes occasionnels et les membres annuels utilisent les vélos Cyclistic de manière diﬀérente. À partir de ces informations, votre équipe concevra une nouvelle stratégie marketing pour convertir les usagers occasionnels en membres annuels. Mais d’abord, les dirigeants de Cyclistic doivent approuver vos recommandations, qui doivent donc être étayées par des aperçus de données convaincants et des visualisations de données professionnelles.

## Personnages et équipes
* Cyclistic
* Équipe d'analytique marketing Cyclistic 
* Équipe de direction Cyclistic 
* Lily Moreno : La directrice du marketing 

# Demander
Trois questions guideront le futur programme de marketing :
1.	Quelles sont les différences d’utilisation des vélos Cyclistic entre les membres annuels et les cyclistes occasionnels ?
2.	Pourquoi les cyclistes occasionnels achèteraient-ils des abonnements annuels à Cyclistic ?
3.	Comment Cyclistic peut-elle utiliser les médias numériques pour inﬂuencer les cyclistes occasionnels à devenir membres ?
 
Lily Moreno vous a assigné la première question à laquelle vous devez répondre : Quelles sont les différences d’utilisation des vélos Cyclistic entre les membres annuels et les cyclistes occasionnels ?

Plusieurs hypothèses peuvent être étudiés: 
* Il y a t'il des jours ou période de l'année ou l'utilisation du service est le plus solicité?
* Il y a t'il des stations très frequenté pour uun type particulier?
* Il y a t'il un type de vélo plus utilisé qu'un autre?
* Le temps d'utilisation differencie t'il le type d'utilisateur?


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

Je créer un nouveau projet que je nomme cyclistic-413112 et un nouvelle ensemble de données que je nomme cyclistique_2023
Je créé une table pour chaque fichier .csv en les nommant janvier_23 jusqu'à decembre_23. 

Je créer ensuite une table permettant de joindre toute les tables et la nomme Annee_23.
``` sql
create table 
`cyclistic-413112.cyclistique_2023.annuel_2023`
AS
  SELECT started_at, ended_at, start_station_name, start_station_id, end_station_name, end_station_id, start_lat, start_lng, end_lat, end_lng, member_casual, day_of_week_2, day_of_week
  FROM `cyclistique_2023.janvier_2023`
  UNION ALL

  SELECT started_at,ended_at, start_station_name, start_station_id, end_station_name, end_station_id, start_lat, start_lng, end_lat, end_lng, member_casual, day_of_week_2, day_of_week
  FROM `cyclistique_2023.fevrier_2023`
  UNION ALL

  SELECT started_at,ended_at, start_station_name, start_station_id, end_station_name, end_station_id, start_lat, start_lng, end_lat, end_lng, member_casual, day_of_week_2, day_of_week
  FROM `cyclistique_2023.mars_2023`
  UNION ALL

  SELECT started_at,ended_at, start_station_name, start_station_id, end_station_name, end_station_id, start_lat, start_lng, end_lat, end_lng, member_casual, day_of_week_2, day_of_week
  FROM `cyclistique_2023.avril_2023`
  UNION ALL

  SELECT started_at,ended_at, start_station_name, start_station_id, end_station_name, end_station_id, start_lat, start_lng, end_lat, end_lng, member_casual, day_of_week_2, day_of_week
  FROM `cyclistique_2023.mai_2023`
  UNION ALL

  SELECT started_at,ended_at, start_station_name, start_station_id, end_station_name, end_station_id, start_lat, start_lng, end_lat, end_lng, member_casual, day_of_week_2, day_of_week
  FROM `cyclistique_2023.juin_2023`
  UNION ALL

  SELECT started_at,ended_at, start_station_name, start_station_id, end_station_name, end_station_id, start_lat, start_lng, end_lat, end_lng, member_casual, day_of_week_2, day_of_week
  FROM `cyclistique_2023.juillet_2023`
  UNION ALL

  SELECT started_at,ended_at, start_station_name, start_station_id, end_station_name, end_station_id, start_lat, start_lng, end_lat, end_lng, member_casual, day_of_week_2, day_of_week
  FROM `cyclistique_2023.aout_2023`
  UNION ALL

  SELECT started_at,ended_at, start_station_name, start_station_id, end_station_name, end_station_id, start_lat, start_lng, end_lat, end_lng, member_casual, day_of_week_2, day_of_week
  FROM `cyclistique_2023.septembre_2023`
  UNION ALL

  SELECT started_at,ended_at, start_station_name, start_station_id, end_station_name, end_station_id, start_lat, start_lng, end_lat, end_lng, member_casual, day_of_week_2, day_of_week
  FROM `cyclistique_2023.octobre_2023`
  UNION ALL 

  SELECT started_at,ended_at, start_station_name, start_station_id, end_station_name, end_station_id, start_lat, start_lng, end_lat, end_lng, member_casual, day_of_week_2, day_of_week
  FROM `cyclistique_2023.novembre_2023`
  UNION ALL

  SELECT started_at,ended_at, start_station_name, start_station_id, end_station_name, end_station_id, start_lat, start_lng, end_lat, end_lng, member_casual, day_of_week_2, day_of_week
  FROM `cyclistique_2023.decembre_2023`
```

Je commence à supprimer toute les lignes où il y a des valeurs null pour les champs start_station_name, end_station_name, start_lat, start_lng, end_lat et end_lng. 
```sql
DELETE FROM `cyclistic-413112.cyclistique_2023.annuel_2023`
WHERE start_station_name IS NULL
OR end_station_name IS NULL
OR end_lat IS NULL
OR end_lng IS NULL
OR start_lat IS NULL
OR start_lng IS NULL;
```

Afin d'avoir des données representatif des utilisatuers je supprime les locations trop longue ( + 24h) et les locations trop courte ( - 1 minutes)
```sql
DELETE FROM `cyclistic-413112.cyclistique_2023.annuel_2023`
WHERE TIMESTAMP_DIFF( started_at,ended_at, SECOND) >= 86400 -- 24 heures en secondes
   OR TIMESTAMP_DIFF(ended_at, started_at, SECOND) <= 60; -- Durée négative
```

Je recré une colonne ride_length depuis BigQuery car lors de la jointure des tables j'ai eu une erreur pour calculer deouis la colonne ride_lebgth car certaine de mes tables n'ont pas été formaté correctement par Bigquery pour cette colonne.
```sql
CREATE OR REPLACE TABLE `cyclistic-413112.cyclistique_2023.annuel_2023` AS
SELECT
  *,
  STRING(
    TIME(
      TIMESTAMP_DIFF(ended_at, started_at, HOUR), 
      MOD(TIMESTAMP_DIFF(ended_at, started_at, MINUTE), 60), 
      MOD(TIMESTAMP_DIFF(ended_at, started_at, SECOND), 60)
    )
  ) AS ride_length
FROM
  `cyclistic-413112.cyclistique_2023.annuel_2023`;
```

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
![Capture d'écran 2024-02-02 102854](https://github.com/K3vinr974/Cyclistic-certification-Google/assets/154596716/32e2e257-517b-41a4-bfd6-c2a66b650ebc)

Afin d'avoir des premieres visualisation et déterminer plus facilement les tendances et differences entre les membres et les occasionels, je transfère la base de donnée sur Tableau et commence mes premiers visuels.

# Analyser

Je creer un visuel pour analyser le nombre d'utilisateurs occasionnel (casual) et le nombre d'utilisateurs abonnée (member). 
![repartition](https://github.com/K3vinr974/Cyclistic-certification-Google/assets/154596716/3d604ce7-b59d-49d4-97b2-a5594241a6f0)

Je créé un autre visuel pour les jours d'utilisation les plus fréquent par type d'utilisateur.
![jours](https://github.com/K3vinr974/Cyclistic-certification-Google/assets/154596716/f47ea621-ecde-4127-a2b6-e4fcf986bce7)

Apres avoir travaillé mes visuels et leur présentations je decide de les publier sur la plateforme Tableau

https://public.tableau.com/app/profile/kevin.richefeu/viz/Classeurcyclistic/Histoire1

Je créer ma presentation et décide donc de publier mon analyse.

# Publier

Je vous joins les liens vers ma présentation.

[Présentation.pdf](https://github.com/K3vinr974/Cyclistic-certification-Google/files/14168883/Presentation.pdf)


# Actionner

Suite à ma publication je peux donner plusieurs recommandations afin de permettre d'accroître le nombre de clients abonnés.

* Créer une période d'abonnement sur la période Avril à Octobre.

* Créer un abonnement spécifique pour les stations en centre ville qui sont les stations les plus frequentés du réseau de Cyclistic.

* Créer un abonnement suivant un temps d'utilisation journalier entre 09h et 19h.

* Créer un abonnement weekend.

* Combiner plusieurs des précédentes recommandations


# Conclusion
Cette presentation terminé, un suivi des résultats sera nécessaire pour connaître l'impact de la ou des recommandations appliqués.
