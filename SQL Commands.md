# SQL Commands
## Table of Contents
- [What is SQL](#what-is-sql)
- [What SQL can do?](#what-sql-can-do-)
- [Categories of SQL Command](#categories-of-sql-command)
- [Data Types on Oracle](#data-types-on-oracle)
- [Create Tables](#create-tables)
- [Inserting Data](#inserting-data)

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
```sql
    create table tablename
    (column1name datatype(size),
    column2name datatype(size),
    column3name datatype(size),...)
````

**Example**
```sql
    create table product
    (name varchar2(50),
    price number(10,2),
    description varchar2(150))
````

# Insert Data
We can insert the data into table using insert query.

**Syntax**
``` sql
insert into tablename (colname, colname, colname, ...) values (value, value, value)
```
**Example**
```sql
insert into product (name, price, description) values ('Laptop', '59999', "Laptop with i5 Processor and 4GB RAM')
```
If we do not want to enter data into all columns we can do it by skipping the column name in the query.
E.g. in below query we have not written description column and its value, as we do not want to enter the value of description.
```sql
insert into product (name, price) values ('Laptop', '59999')
```

Note if we want to insert data into all columns of the table we can skip the column names.

**Syntax**
```sql
insert into tablename values (value1, value2, value3, ...)
```
Above systanx only work when we want to enter data in all columns of the table. Also the sequence of the value should be same as column sequence.

**Example**
```sql
insert into product values ('Laptop', '59999', "Laptop with i5 Processor and 4GB RAM')
```

# Select Data

We can select (fetch) the data from table using select query. 

**Syntax**

```sql
select * from tablename
```

**Example**

```sql
select * from product
```

Above example will fetch all the records and all the attributes (columns) from the table product.

## Select selective attributes (columns)

**Syntax**

```sql
select columnname, columnname, ... from tablename
```

Instead of writing * sign we can specify the list of attributes separated by comma to fetch only selective attributes from the table.

**Example**

```sql
select name, price from product
```

Above example will fetch only name, and price attributes from the table product.

## Select selective records (rows)

**Syntax**

```sql
select * from tablename where condition
```

Instead of writing * sign we can specify the list of attributes separated by comma to fetch only selective attributes from the table. We can use any conditional operator (=, <, <=, >, >=, <>) to make any condition and also use any logical operator (and, or, not) to combine multiple conditions.

**Example**

```sql
select * from product where price > 5000
```

Above example will fetch those records whose price is greater than 5000.

```sql
select * from product where price < 50000 and name = 'Laptop'
```

Above example will fetch those records whose price is greater than 5000 and product name is Laptop.

## Select selective attributes (columns) and selective records (rows)

We can combine above two syntax to select selective attributes and selective records.

**Syntax**

```sql
select columnname, columnname, ... from tablename where condition
```

Instead of writing * sign we can specify the list of attributes separated by comma to fetch only selective attributes from the table.

**Example**

```sql
select name from product where price > 10000
```

Above example will records whose price is greater than 10000 and will only display name attribute.



