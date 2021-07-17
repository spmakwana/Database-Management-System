# SQL Commands

# What is SQL

*	SQL stands for Structured Query Language
*	SQL lets you access and manipulate databases
*	SQL became a standard of the American National Standards Institute (ANSI) in 1986, and of the International Organization for Standardization (ISO) in 1987

# What SQL can do?

*	SQL can execute queries against a database
*	SQL can retrieve data from a database
*	SQL can insert records in a database
*	SQL can update records in a database
*	SQL can delete records from a database
*	SQL can create new databases
*	SQL can create new tables in a database
*	SQL can create stored procedures in a database
*	SQL can create views in a database
*	SQL can set permissions on tables, procedures, and views

# Categories of SQL Command

* **Data Definition Language (DDL)**
  * Commands which are related to defining structues of database/tables/views etc. are known as Data Definition Language (DDL) Commands
  * e.g. Create, Drop, Alter, Truncate
* **Data Manipulation Language**
  * Commands which are related to manipulation of data of tables are kown as Data Manipulation Commands.
  * e.g. Insert, Update, Delete
* **Data Control Language**
  * Commands which are related to control the permission of database/tables/view etc are known as Data Control Commands
  * e.g. Grant, Revoke
* **Transaction Control Language**
  * Commands which are related to control the series of queries (Transaction) are known as Transaction Control Language
  * Commit, Rollback, Save Point
* **Data Query Language**
  * Commands which are used to quering (reading/fetching) data from database/tables/view etc are kown as Data Query Language
  * e.g. Select

# Data Types on Oracle
* CHARACTER/STRING Datatype
	* CHAR
	* VARCHAR2 and VARCHAR and NVARCHAR2
	* LONG 
* NUMERIC Datatypes
	* NUMBER
* DATE Datatypes
	* DATE
* Binary Datatypes
	* BLOB
	* BFILE
	* RAW
	* LONG RAW 


# Create Tables
Tables are the fundamental structure in database to store the data. Table compromises of rows and columns. Each column a data value which is to be stored, and each row represents one record of that table.

Tables can be created using Create command

**Syntax**
````
    create table table name
    (column1name datatype(size),
    column2name datatype(size),
    column3name datatype(size),...)
````

**Example**
````
    create table product
    (name varchar2(50),
    price number(10,2),
    description varchar2(150))
````
