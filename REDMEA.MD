# Big Data Pyspark

```
TP: pyspark
```
*  Vous créez la base de données et les tables:

```
show()
```

![image](https://github.com/BeidjaCheikh/TP_sparkSQL/blob/master/images/img3.png)
![image](https://github.com/BeidjaCheikh/TP_sparkSQL/blob/master/images/img3.png)

```
   df1.groupBy(col("DATE_CONSULTATION").alias("DATE de CONSULTATION")).count().show();
```