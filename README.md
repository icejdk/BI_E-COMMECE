# BI_E-COMMECE
Environment:
This document introduces you to the data platform architecture of an ecommerce company named SoftCart.

SoftCart uses a hybrid architecture, with some of its databases on premises and some on cloud.

Tools and Technologies:
OLTP database - MySQL
Production Data warehouse – DB2 on Cloud
Staging - Data warehouse – PostgreSQL
Business Intelligence Dashboard - IBM Cognos Analytics

Process:
SoftCart's online presence is primarily through its website, which customers access using a variety of devices like laptops, mobiles and tablets.

All the catalog data of the products and transactional data like inventory and sales are stored in the MySQL database server.

SoftCart's webserver is driven entirely by this database.

Data is periodically extracted from this database and put into the staging data warehouse running on PostgreSQL.

Production data warehouse is on the cloud instance of IBM DB2 server.

BI teams connect to the IBM DB2 for operational dashboard creation. IBM Cognos Analytics is used to create dashboards.

An ETL process using a shell script is set up to extract new transactional data for each day from the OLTP database and load it into the staging data warehouse.
