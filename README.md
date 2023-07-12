# Mysql-Redshift-Streaming-DataPipeine
This repo contain near real time streaming incremental load data pipeline code. 

Export data from mysql-database to AWS REDSHIFT using kafka.

![Data flow diagram](./diagram/dataflow-diagram.png)

Problem Statement:
We need to build an ETL pipeline to load mysql data base record to redshift using kafka
![MY SQL DATABASE](./diagram/mysql-oltp-database.png)


RedShift Dataware house
![Red Shift](./diagram/redshift-olap-diagram.png)
Approach
1. Read data from mysql and  send to kafka topic and from kafka topic we will load to s3 bucket
![mysql-kafka-s3](./diagram/mysql-kafka-s3.png)

2. Read data from s3 bucket and load in REDSHIFT
![s3-redshift](./diagram/s3-redshift.png)

Launch entire server setup
```
docker-compose up
```

Load data in mysql db
```
docker exec -i mysql sh -c 'exec mysql -uroot -p"$MYSQL_ROOT_PASSWORD"' < "./database-dump/mysqlsampledatabase.sql"
```



We will design Star Schema so that we can export above attached OLTP to OLAP

1. [Redshift setup](doc/REDSHIFT.md)
2. [Kafka setup](doc/CONFLUENT_KAFKA.md)

1. [MYSQL KAFKA S3](./mysql-kafka-s3/README.md) Project Description
2. [S3 Redshift](./kafka-redshift/README.md) Project Description


