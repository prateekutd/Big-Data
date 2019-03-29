Performed data extraction and analytics using Big Data technologies such as Sqoop,Hive,Spark,Flume
Q1) 
Using sqoop, import orders table into hdfs to folders /user/cloudera/problem1/orders. File should be loaded as Avro File and use snappy compression.
Using sqoop, import order_items  table into hdfs to folders /user/cloudera/problem1/order-items. Files should be loaded as avro file and use snappy compression.
Using Spark Scala load data at /user/cloudera/problem1/orders and /user/cloudera/problem1/orders-items items as dataframes. 
Expected Intermediate Result: Order_Date , Order_status, total_orders, total_amount. In plain english, please find total orders and total amount per status per day. The result should be sorted by order date in descending, order status in ascending and total amount in descending and total orders in ascending. Aggregation should be done using below methods. However, sorting can be done using a dataframe or RDD.
Store the result as parquet file into hdfs using gzip compression under folder.
Store the result as parquet file into hdfs using snappy compression under folder
Store the result as CSV file into hdfs using No compression under folder.
create a mysql table named result and load data from /user/cloudera/problem1/result4a-csv to mysql table named result.

Q2)
Using sqoop copy data available in mysql products table to folder /user/cloudera/products on hdfs as text file. columns should be delimited by pipe '|'
move all the files from /user/cloudera/products folder to /user/cloudera/problem2/products folder
Change permissions of all the files under /user/cloudera/problem2/products such that owner has read,write and execute permissions, group has read and write permissions whereas others have just read and execute permissions
read data in /user/cloudera/problem2/products and do the following operations using a) dataframes api b) spark sql c) RDDs aggregateByKey method. Your solution should have three sets of steps. Sort the resultant dataset by category id
filter such that your RDD\DF has products whose price is lesser than 100 USD
on the filtered data set find out the higest value in the product_price column under each category
on the filtered data set also find out total products under each category
on the filtered data set also find out the average price of the product under each category
on the filtered data set also find out the minimum price of the product under each category
store the result in avro file using snappy compression under these folders respectively
/user/cloudera/problem2/products/result-df
/user/cloudera/problem2/products/result-sql
/user/cloudera/problem2/products/result-rdd

Q3)
Import all tables from mysql database into hdfs as avro data files. use compression and the compression codec should be snappy. data warehouse directory should be retail_stage.db
Create a metastore table that should point to the orders data imported by sqoop job above. Name the table orders_sqoop. 
Write query in hive that shows all orders belonging to a certain day. This day is when the most orders were placed. select data from orders_sqoop. 
query table in impala that shows all orders belonging to a certain day. This day is when the most orders were placed. select data from order_sqoop. 
Now create a table named retail.orders_avro in hive stored as avro, the table should have same table definition as order_sqoop. Additionally, this new table should be partitioned by the order month i.e -> year-order_month.(example: 2014-01)
Load data into orders_avro table from orders_sqoop table.
Write query in hive that shows all orders belonging to a certain day. This day is when the most orders were placed. select data from orders_avro
evolve the avro schema related to orders_sqoop table by adding more fields named (order_style String, order_zone Integer)
insert two more records into orders_sqoop table. 
Write query in hive that shows all orders belonging to a certain day. This day is when the most orders were placed. select data from orders_sqoop
query table in impala that shows all orders belonging to a certain day. This day is when the most orders were placed. select data from orders_sqoop

Q4)
Import orders table from mysql as text file to the destination /user/cloudera/problem5/text. Fields should be terminated by a tab character ("\t") character and lines should be terminated by new line character ("\n"). 
Import orders table from mysql  into hdfs to the destination /user/cloudera/problem5/avro. File should be stored as avro file.
Import orders table from mysql  into hdfs  to folders /user/cloudera/problem5/parquet. File should be stored as parquet file.
Transform/Convert data-files at /user/cloudera/problem5/avro and store the converted file at the following locations and file formats
save the data to hdfs using snappy compression as parquet file at /user/cloudera/problem5/parquet-snappy-compress
save the data to hdfs using gzip compression as text file at /user/cloudera/problem5/text-gzip-compress
save the data to hdfs using no compression as sequence file at /user/cloudera/problem5/sequence
save the data to hdfs using snappy compression as text file at /user/cloudera/problem5/text-snappy-compress
Transform/Convert data-files at /user/cloudera/problem5/parquet-snappy-compress and store the converted file at the following locations and file formats
save the data to hdfs using no compression as parquet file at /user/cloudera/problem5/parquet-no-compress
save the data to hdfs using snappy compression as avro file at /user/cloudera/problem5/avro-snappy
Transform/Convert data-files at /user/cloudera/problem5/avro-snappy and store the converted file at the following locations and file formats
save the data to hdfs using no compression as json file at /user/cloudera/problem5/json-no-compress
save the data to hdfs using gzip compression as json file at /user/cloudera/problem5/json-gzip
Transform/Convert data-files at  /user/cloudera/problem5/json-gzip and store the converted file at the following locations and file formats
save the data to as comma separated text using gzip compression at   /user/cloudera/problem5/csv-gzip
Using spark access data at /user/cloudera/problem5/sequence and stored it back to hdfs using no compression as ORC file to HDFS to destination /user/cloudera/problem5/orc 

Q5)
Using sqoop, import products_replica table from MYSQL into hdfs such that fields are separated by a '|' and lines are separated by '\n'. Null values are represented as -1 for numbers and "NOT-AVAILABLE" for strings. Only records with product id greater than or equal to 1 and less than or equal to 1000 should be imported and use 3 mappers for importing. The destination file should be stored as a text file to directory  /user/cloudera/problem5/products-text. 
Using sqoop, import products_replica table from MYSQL into hdfs such that fields are separated by a '*' and lines are separated by '\n'. Null values are represented as -1000 for numbers and "NA" for strings. Only records with product id less than or equal to 1111 should be imported and use 2 mappers for importing. The destination file should be stored as a text file to directory  /user/cloudera/problem5/products-text-part1. 
Using sqoop, import products_replica table from MYSQL into hdfs such that fields are separated by a '*' and lines are separated by '\n'. Null values are represented as -1000 for numbers and "NA" for strings. Only records with product id greater than 1111 should be imported and use 5 mappers for importing. The destination file should be stored as a text file to directory  /user/cloudera/problem5/products-text-part2.
Using sqoop merge data available in /user/cloudera/problem5/products-text-part1 and /user/cloudera/problem5/products-text-part2 to produce a new set of files in /user/cloudera/problem5/products-text-both-parts
Using sqoop do the following. Read the entire steps before you create the sqoop job.
create a sqoop job Import Products_replica table as text file to directory /user/cloudera/problem5/products-incremental. Import all the records.
insert three more records to Products_replica from mysql
run the sqoop job again so that only newly added records can be pulled from mysql
insert 2 more records to Products_replica from mysql
run the sqoop job again so that only newly added records can be pulled from mysql
Validate to make sure the records have not be duplicated in HDFS
Using sqoop do the following. Read the entire steps before you create the sqoop job.
create a hive table in database named problem5 using below command 
create table products_hive  (product_id int, product_category_id int, product_name string, product_description string, product_price float, product_imaage string,product_grade int,  product_sentiment string);
create a sqoop job Import Products_replica table as hive table to database named problem5. name the table as products_hive. 
insert three more records to Products_replica from mysql
run the sqoop job again so that only newly added records can be pulled from mysql
insert 2 more records to Products_replica from mysql
run the sqoop job again so that only newly added records can be pulled from mysql
Validate to make sure the records have not been duplicated in Hive table
Using sqoop do the following. .
insert 2 more records into products_hive table using hive. 
create table in mysql using below command   
create table products_external  (product_id int(11) primary Key, product_grade int(11), product_category_id int(11), product_name varchar(100), product_description varchar(100), product_price float, product_impage varchar(500), product_sentiment varchar(100));
export data from products_hive (hive) table to (mysql) products_external table. 
insert 2 more records to Products_hive table from hive
export data from products_hive table to products_external table. 
Validate to make sure the records have not be duplicated in mysql table

Q6)
Using HIVE QL over Hive Context
Using Spark SQL over Spark SQL Context or by using RDDs
create a hive meta store database named problem6 and import all tables from mysql retail_db database into hive meta store. 
On spark shell use data available on meta store as source and perform step 3,4,5 and 6. [this proves your ability to use meta store as a source]  
Rank products within department by price and order by department ascending and rank descending [this proves you can produce ranked and sorted data on joined data sets]
find top 10 customers with most unique product purchases. if more than one customer has the same number of product purchases then the customer with the lowest customer_id will take precedence [this proves you can produce aggregate statistics on joined datasets]
On dataset from step 3, apply filter such that only products less than 100 are extracted [this proves you can use subqueries and also filter data]
On dataset from step 4, extract details of products purchased by top 10 customers which are priced at less than 100 USD per unit [this proves you can use subqueries and also filter data]
Store the result of 5 and 6 in new meta store tables within hive.
