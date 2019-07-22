# Fraud Transaction Monitor

## Business problem and motivation
Credit card fraud transaction are common and can cause a huge loss to the companies.
However they can be easily tracked on the basis of cutomers prior spending habits data such as comman merchants, purchase items,
spending amount, location,etc.

## Solution
The aim of the project is to build a model based on customers data.
This model is used to identify if the transaction is fraud or not at real time and display under fraud transactions. 

## Data
Customer - File includes customer data with following attributes
Customer_number ,First_Name, Last_Name, Gender, Street, City, State, Zip, Latitude , Longititude , Job, date_of_Birth

Transactions - File includes past customer transactions indicating the transactions which were fraud
Customer_number ,First_Name, Last_Name, Trans_num, Trans_date, Trans_time, unix_time, Category, Merchant,amt,merch_lat,merch_long,is_fraud

## Pipeline

![alt text](https://github.com/SainathDutkar/Fraud_Transaction_Monitor/blob/master/images/pipeline.PNG)

- Past transaction data is read using Spark SQL and stored in Cassandara database
- On the bases of data in Cassandra a ML model is build using Spark MLib
- Kafka is used to randomly produce a transaction which are consumed by Spark Streaming
- Spark Streaming runs the transaction through ML model to verify if the transacion is fraud
- Fraud transactions are saved in Cassandra table
- Data from fraud transaction tables are showed on the front end at real time

## Tools and technologies used
 - Apache Spark SQL
 - Apache Spark Streaming
 - Apache Spark Mlib
 - Kafka
 - Cassandra
