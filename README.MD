# Big Data Pyspark
[Partie 1](#partie1)
[Partie 2](#partie2)

## partie1
```
TP: pyspark
```
*  Vous créez la base de données et les tables:

```
show()
```

![image](https://github.com/BeidjaCheikh/pyspark/blob/master/images/img3.png)
![image](https://github.com/BeidjaCheikh/pyspark/blob/master/images/img4.png)

* 1. Afficher les projets en cours de réalisation.

```
  >>> dfVols = spark.read.format("jdbc").option("driver", "com.mysql.cj.jdbc.Driver").option("url", "jdbc:mysql://localhost:3306/db_imomaroc").option("user", "root").option("password", "").option("query", "SELECT *FROM projets WHERE current_date() BETWEEN date_debut AND date_fin").load() 
   >>> dfVols.show()       
```
![image](https://github.com/BeidjaCheikh/pyspark/blob/master/images/img1.png)

*  2. Afficher pour chaque projet, le nombre de tâches dont la durée dépasse un mois. Le format
      d’affichage est le suivant:
```
  ID_PROJET | TITRE | NOMBRE
```
```
 >>> dfVols = spark.read.format("jdbc").option("driver", "com.mysql.cj.jdbc.Driver").option("url", "jdbc:mysql://localhost:3306/db_imomaroc").option("user", "root").option("password", "").option("query", "SELECT projets.id_projet, projets.titre, COUNT(*) AS nombre FROM projets INNER JOIN taches ON projets.id_projet = taches.id_p WHERE TIMESTAMPDIFF(MONTH, taches.date_debut_taches, taches.date_fin_taches) > 1 GROUP BY projets.id_projet, projets.titre").load()
 >>> dfVols.show() 
```
![image](https://github.com/BeidjaCheikh/pyspark/blob/master/images/img5.png)

* 3. Afficher pour chaque projet les tâches en retard (avec la durée de retard).

```
  >>> dfVols = spark.read.format("jdbc").option("driver", "com.mysql.cj.jdbc.Driver").option("url", "jdbc:mysql://localhost:3306/db_imomaroc").option("user", "root").option("password", "").option("query", "SELECT projets.id_projet, projets.titre, taches.tite AS titre_tache, taches.date_debut_taches, taches.date_fin_taches, CURRENT_DATE() AS date_actuelle, TIMESTAMPDIFF(DAY, taches.date_fin_taches, CURRENT_DATE()) AS retard FROM projets INNER JOIN taches ON projets.id_projet = taches.id_p WHERE taches.date_fin_taches < CURRENT_DATE()").load()
  >>> dfVols.show() 
```
![image](https://github.com/BeidjaCheikh/pyspark/blob/master/images/img6.png)

## partie2
### II. Traitement de données stockées dans un fichier Json.
* Démarrage de pyspark
![image](https://github.com/BeidjaCheikh/pyspark/blob/master/images/img7.png)

* 1. Afficher les deux première villes ou l’entreprise a réalisé plus de ventes (en terme de revenues).
```
  schow()
```
![image](https://github.com/BeidjaCheikh/pyspark/blob/master/images/img8.png)

* 2. Afficher la liste des clients qui possèdent plus qu’un appartement à rabat.

```
  schow()
```
![image](https://github.com/BeidjaCheikh/pyspark/blob/master/images/img9.png)

* 3. Afficher le nombre d’appartements vendues à Casablanca.

```
  schow()
```
![image](https://github.com/BeidjaCheikh/pyspark/blob/master/images/img10.png)