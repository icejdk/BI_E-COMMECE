#!/bin/sh

## Write your code here to load the data from sales_data table in Mysql server to a sales.csv.
## Select the data which is not more than 4 hours old from the current time.
 # Set the current time
current_time=$(date +"%Y-%m-%dT%H:%M:%S")

# Calculate the 4 hour cutoff
cutoff_time=$(date -d "$current_time - 4 hours" +"%Y-%m-%dT%H:%M:%S")

# Connect to the MySQL database
mysql --host=127.0.0.1 --port=3306 --user=root --password='MjE3MDQtam9zYXBo' -e "USE sales;
SELECT * INTO OUTFILE '/home/project/sales.csv' 
FIELDS TERMINATED BY ','
FROM sales_data WHERE timestamp > '$cutoff_time';"

# Select the data from the sales_data table that is not older than the cutoff time



 export PGPASSWORD=MzEyNzAtam9zYXBo;



psql --username=postgres --host=localhost --dbname=sales_new -c "\COPY sales_data(rowid,product_id,customer_id,price,quantity,timestamp) FROM '/home/project/sales.csv' delimiter ',' CSV HEADER ;" 

 ## Delete sales.csv present in location /home/project
 rm /home/project/sales.csv;
 ## Write your code here to load the DimDate table from the data present in sales_data table

psql --username=postgres --host=localhost --dbname=sales_new -c  "INSERT INTO DimDate (select dateid,to_char(timestamp, 'dd'),to_char(timestamp, 'mm'),to_char(timestamp, 'yyyy') from sales_data );"

## Write your code here to load the FactSales table from the data present in sales_data table

psql --username=postgres --host=localhost --dbname=sales_new -c  "INSERT INTO FactSales (select rowid,product_id,customer_id,price,price*quantity as total_price from sales_data);"

 ## Write your code here to export DimDate table to a csv

 psql --username=postgres --host=localhost --dbname=sales_new -c "\COPY dimdate TO '/home/project/dimdate.csv' DELIMITER ',' CSV HEADER;"

 ## Write your code here to export FactSales table to a csv
 
 psql --username=postgres --host=localhost --dbname=sales_new -c "\COPY factsales TO '/home/project/factsales.csv' DELIMITER ',' CSV HEADER;"

