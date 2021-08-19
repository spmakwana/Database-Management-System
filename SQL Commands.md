# Table of contents

- [What is SQL](#what-is-sql)
- [What SQL can do?](#what-sql-can-do)
- [Categories of SQL Command](#categories-of-sql-command)
- [Data Types in Oracle](#data-types-in-oracle)
- [Create Tables](#create-tables)
- [Modify Table Structure](#modify-table-structure)
  - [Add Column to Table](#add-column-to-table)
  - [Remove Column from Table](#remove-column-from-table)
  - [Modify Column Datatype](#modify-column-datatype)
  - [Rename Column](#rename-column)
  - [Rename Table](#rename-table)
- [Insert Data](#insert-data)
- [Select Data](#select-data)
  - [Select all attributes (columns) and records (rows)](#select-all-attributes-columns-and-records-rows)
  - [Select selective attributes (columns)](#select-selective-attributes-columns)
  - [Select selective records (rows)](#select-selective-records-rows)
  - [Select selective attributes (columns) and selective records (rows)](#select-selective-attributes-columns-and-selective-records-rows)
- [Update Data](#update-data)
- [Delete Data](#delete-data)
- [SQL Constraints](#sql-constraints)
- [NOT NULL Constraint](#not-null-constraint)
  - [Apply NOT NULL constraint when creating a new table](#apply-not-null-constraint-when-creating-a-new-table)
  - [Apply NOT NULL constraint on already created table](#apply-not-null-constraint-on-already-created-table)
  - [Remove NOT NULL Constraint](#remove-not-null-constraint)
- [UNIQUE Constraint](#unique-constraint)
  - [Apply UNIQUE constraint when creating a new table](#apply-unique-constraint-when-creating-a-new-table)
  - [Apply UNIQUE constraint on already created table](#apply-unique-constraint-on-already-created-table)
  - [Remove UNIQUE Constraint](#remove-unique-constraint)
- [PRIMARY KEY Constraint](#primary-key-constraint)
  - [Apply PRIMARY KEY Constraint when creating a new table](#apply-primary-key-constraint-when-creating-a-new-table)
  - [Apply PRIMARY KEY constraint on already created table](#apply-primary-key-constraint-on-already-created-table)
  - [Remove PRIMARY KEY constraint](#remove-primary-key-constraint)

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
* **Data Manipulation Language (DML)**
  * Commands which are related to manipulation of data of tables are kown as Data Manipulation Commands.
  * e.g. Insert, Update, Delete
* **Data Control Language (DCL)**
  * Commands which are related to control the permission of database/tables/view etc are known as Data Control Commands
  * e.g. Grant, Revoke
* **Transaction Control Language (TCL)**
  * Commands which are related to control the series of queries (Transaction) are known as Transaction Control Language
  * Commit, Rollback, Save Point
* **Data Query Language (DQL)**
  * Commands which are used to quering (reading/fetching) data from database/tables/view etc are kown as Data Query Language
  * e.g. Select

# Data Types in Oracle
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
    CREATE TABLE table_name
    (
        column1_name DATATYPE(SIZE),
    	column2_name DATATYPE(SIZE),
    	column3_name DATATYPE(SIZE),
        ...
    )
````

**Example**
```sql
    CREATE TABLE product
    (
        name VARCHAR2(50),
    	price NUMBER(10,2),
    	description VARCHAR2(150)
    )
````

# Modify Table Structure

After the table is created, if we wanted to make changes with table structure like adding new column, removing existing columns, changing data types of column etc. we can use Alter command to to modification with table structure.

## Add Column to Table

Below syntax can be used to add new column to an existing table.

**Syntax**

```sql
ALTER TABLE table_name
ADD column_name DATATYPE(SIZE)
```

**Example**

```sql
ALTER TABLE student
ADD mobile_no VARCHAR2(10)
```

Above example will add new column with name mobile_no with datatype varchar2(10) to table student.

## Remove Column from Table

Below syntax can be used to remove existing column from a table. When we delete any column and if the column has some data, then data of that column will be permanently lost and can not be undone.

**Syntax**

```sql
ALTER TABLE table_name
DROP COLUMN column_name
```

**Example**

```sql
ALTER TABLE student
DROP COLUMN mobile_no
```

Above example will remove column mobile_no from the table student. 

## Modify Column Datatype

If we want to modify the datatype or size of the column, below syntax can be used.

**Syntax**

```sql
-- Syntax for older version of Database
ALTER TABLE table_name
MODIFY COLUMN column_name DATATYPE(SIZE)

-- Syntax for newer version of Database
ALTER TABLE table_name
MODIFY column_name DATATYPE(SIZE)
```

**Example**

```sql
ALTER TABLE student
MODIFY mobile_no VARCHAR2(12)
```

Above example will modify the datatype of column mobile_no to varchar2 with the size to 12 in student table.

## Rename Column

If we want to rename an existing table column, below syntax can be used.

**Syntax**

```sql
ALTER TABLE table_name
RENAME COLUMN old_column_name TO new_column_name
```

**Example**

```sql
ALTER TABLE student
RENAME COLUMN mobile_no to phone_no
```

Above example will rename column mobile_no to phone_no in the student table.

## Rename Table

If we want to rename an table, below syntax can be used.

**Syntax**

```sql
ALTER TABLE table_name
RENAME to new_table_name
```

**Example**

```sql
ALTER TABLE student
RENAME to student_detail
```

Above example will rename table student to student_detail.

# Insert Data

We can insert the data into table using insert query.

**Syntax**
``` sql
INSERT INTO table_name (column_name, column_name, column_name, ...) VALUES (value, value, value)
```
**Example**
```sql
INSERT INTO product (name, price, description) VALUES ('Laptop', '59999', "Laptop with i5 Processor and 4GB RAM')
```
If we do not want to enter data into all columns we can do it by skipping the column name in the query.
E.g. in below query we have not written description column and its value, as we do not want to enter the value of description.

```sql
INSERT INTO product VALUES (name, price) values ('Laptop', '59999')
```

Note if we want to insert data into all columns of the table we can skip the column names.

**Syntax**
```sql
INSERT INTO table_name VALUES (value1, value2, value3, ...)
```
Above systanx only work when we want to enter data in all columns of the table. Also the sequence of the value should be same as column sequence.

**Example**
```sql
INSERT INTO product VALUES ('Laptop', '59999', "Laptop with i5 Processor and 4GB RAM')
```

# Select Data

We can select (fetch) the data from table using select query. 

## Select all attributes (columns) and records (rows)

**Syntax**

```sql
SELECT * FROM table_name
```

**Example**

```sql
SELECT * FROM product
```

Above example will fetch all the records and all the attributes (columns) from the table product.

## Select selective attributes (columns)

**Syntax**

```sql
SELECT column_name, column_name, ... FROM table_name
```

Instead of writing * sign in select query, we can specify the list of attributes separated by comma to fetch only selective attributes from the table.

**Example**

```sql
SELECT name, price FROM product
```

Above example will fetch only name, and price attributes from the table product.

## Select selective records (rows)

**Syntax**

```sql
SELECT * FROM table_name WHERE condition
```

Instead of writing * sign we can specify the list of attributes separated by comma to fetch only selective attributes from the table. We can use any conditional operator (=, <, <=, >, >=, <>) to make any condition and also use any logical operator (and, or, not) to combine multiple conditions.

**Example**

```sql
SELECT * FROM product WHERE price > 5000
```

Above example will fetch those records whose price is greater than 5000.

```sql
SELECT * FROM product WHERE price < 50000 AND name = 'Laptop'
```

Above example will fetch those records whose price is greater than 5000 and product name is Laptop.

## Select selective attributes (columns) and selective records (rows)

We can combine above two syntax to select selective attributes and selective records.

**Syntax**

```sql
SELECT column_name, column_name, ... FROM table_name WHERE condition
```

Instead of writing * sign in select query we can specify the list of attributes separated by comma to fetch only selective attributes from the table.

**Example**

```sql
SELECT name FROM product WHERE price > 10000
```

Above example will records whose price is greater than 10000 and will only display name attribute.

# Update Data

To update (modify) the existing data of table we can use update query.

**Syntax**

```sql
-- To update only single attribute (column)
UPDATE table_name SET column_name = 'new_value' WHERE condition

-- To update multiple attribute (columns)
UPDATE tablename SET column_name = 'new_value', column_name = 'new_value' WHERE condition
```

**Example**

```sql
update product set price = '5000'
```

In above example we have updated the price attribute of the product table. Above query will set the price value to 5000 in all records. Because by default update query affect all the records if no condition is specified.  

But most of the times we don't want to update all the records but we only want to update the selective records. To update selective records we can append the condition in update query. Only those records which satisfy the query will be updated.

**Example**

```sql
UPDATE product SET price = '50000' WHERE name = 'Laptop'
```

Above example will set the price attribute to 50000 only in those records whose name attribute is 'Laptop'.

We can also update the multiple attribute in a single query by specifying multiple attribute-value pair separated by comma.

**Example**

```sql
UPDATE product SET price = '50000', description = 'Laptop with 16GB RAM' WHERE name = 'Laptop'
```

Above example will set the new value to price and description attribute in those records whose name attribute is 'Laptop'

# Delete Data

To delete the data (records) from the table we can use delete query.

**Syntax**

```sql
DELETE FROM table_name WHERE condition
```

**Example**

```sql
DELETE FROM product
```

Above example will delete all the records from the table product. 

If we want to delete only some records we can specify the condition. When condition is specified only those records which satisfy the condition will be deleted.

```sql
DELETE FROM product where name = 'Laptop'
```

Above example will delete the records from product table where the value of name attribute is 'Laptop'

# SQL Constraints

- Constraints is rules specified for the data in a table. constraints can be given to single attribute or group of attributes of a table. 

- Constraints are used to limit or validate the data in which can be inserted into a table.
- Constraints ensure the reliability of the data, if one tries to enter the data which does not satisfy the rule specified in constraints, the operation is aborted and the data will not be inserted.

Below are various constraints available in SQL

- NOT NULL
- UNIQUE
- PRIMARY KEY
- FOREIGN KEY
- CHECK
- DEFAULT
- CREATE INDEX

# NOT NULL Constraint

By default any column can hold null value.  Means we can left that column when inserting the data.

NOT NULL constraint enforce the column to not accept the NULL value. It means we must have to enter the value into that column whenever inserting a record.

## Apply NOT NULL constraint when creating a new table

**Syntax**

```sql
CREATE TABLE tablename
(
    column_name DATATYPE(SIZE) NOT NULL,
    column_name DATATYPE(SIZE) NOT NULL,
    ...
)
```

**Example**

```sql
CREATE TABLE product
(
    name VARCHAR2(50) NOT NULL,
    price NUMBER(10,2) NOT NULL,
    description VARCHAR2(150)
)
```

In above example for name and price column NOT NULL constraint is enforced. This will ensure that name and price column does not accept null value. So we must enter the value of name and price when inserting the data into the table.

## Apply NOT NULL constraint on already created table

If table is already created, we can add NOT NULL constraint to column or multiple columns using alter table command.

**Syntax**

```sql
ALTER TABLE table_name MODIFY column_name NOT NULL
```

**Example**

```sql
ALTER TABLE product MODIFY name NOT NULL
```

In above example, we have added NOT NULL constraint to name attribute in table product which was already created.

## Remove NOT NULL Constraint

NOT NULL constraint can be removed using below syntax

**Syntax**

```sql
ALTER TABLE table_name MODIFY column_name NULL
```

**Example**

```sql
ALTER TABLE product MODIFY name NULL
```

# UNIQUE Constraint

When we apply UNIQUE constraint to any attribute, it enforce below rules.

Can not enter duplicate value in attribute in which UNIQUE constraint is applied. But unique column accepts NULL value.

## Apply UNIQUE constraint when creating a new table

```sql
CREATE TABLE table_name
(
    column_name DATATYPE(SIZE) NOT NULL,
    column_name DATATYPE(SIZE) NOT NULL,
    ...
)
```

**Example**

```sql
CREATE TABLE product
(
    name VARCHAR2(50) UNIQUE,
    price NUMBER(10,2),
    description VARCHAR2(150)
)
```

In above example for name we have applied UNIQUE constraint, which means we can't enter duplicate data into name attribute. 

If we also do not want to allow null value we can specify both NOT NULL and UNIQUE constraint as shown in below example.

**Example**

```sql
CREATE TABLE product
(
    name VARCHAR2(50) NOT NULL UNIQUE,
	price NUMBER(10,2),
	description VARCHAR2(150)
)
```

To apply UNIQUE constraint to group of column, below syntax is used. Below syntax also used to give a name to UNIQUE constraint which can be useful when removing the constraint.

**Syntax**

```sql
CREATE TABLE table_name
(
column_name DATATYPE(SIZE) NOT NULL,
column_name DATATYPE(SIZE) NOT NULL,
...
CONSTRAINT constraint_name UNIQUE (column_name),
CONSTRAINT constraint_name UNIQUe (column_name, column_name),
...
)
```

**Example**

```sql
CREATE TABLE product
(
    name VARCHAR2(50) NOT NULL,
	price NUMBER(10,2),
	description VARCHAR2(150),
	CONSTRAINT UC_NAME UNIQUE (name)
)
```

To apply UNIQUE constraint to group of column, below syntax is used. Below syntax also used to give a name to UNIQUE constraint which can be useful when removing the constraint.

## Apply UNIQUE constraint on already created table

If table is already created, we can add UNIQUE constraint to column or multiple columns using alter table command.

**Syntax**

```sql
ALTER TABLE table_name ADD UNIQUE (column_name)

-- to specify UNIQUE constraint on multiple column

ALTER TABLE table_name ADD UNIQUE (column_name, column_name, ...)
```

Below syntax can be used to give name to unique constraint in already created table.

**Syntax**

```sql
-- to specify UNIQUE constraint on single column
ALTER TABLE table_name ADD CONSTRAINT constraint_name UNIQUE (column_name)

-- to specify UNIQUE constraint on multiple column
ALTER TABLE table_name ADD CONSTRAINT constraint_name UNIQUE (column_name, column_name, ...)
```

**Example**

```sql
-- UNIQUE constraint to single column
ALTER TABLE product ADD UNIQUE (name)

-- UNIQUE constraint to multiple columns
ALTER TABLE product ADD UNIQUE (name, price)

-- Specifing constraint name with single column
ALTER TABLE product ADD CONSTRAINT UC_name (name)

-- specifing constraint name with multiple column
ALTER TABLE product ADD CONSTRAINT UC_name_price (name, price)
```

## Remove UNIQUE Constraint

We can remove UNIQUE constraint using below syntax

**Syntax**

```sql
ALTER TABLE tablename
DROP CONSTRAINT constraint_name
```

**Example**

```sql
ALTER TABLE product
DROP CONSTRAINT UC_name_price
```

Above example will remove UNIQUE constraint with name UC_name_price

# PRIMARY KEY Constraint

PRIMARY KEY is used to identify each records in a table uniquely. 

Table can have only one PRIMARY KEY. PRIMARY KEY can be made of single column or group of column. When PRIMARY KEY constraint is assigned to any column or group of column below rules are enforced. 

- PRIMARY KEY column (or group of column) can not be left blank and can not contain NULL value
- PRIMARY KEY column (or group of column) can not have duplicate value.

## Apply PRIMARY KEY Constraint when creating a new table

Below syntax can be used to apply PRIMARY KEY constraint when creating a new table.

**Syntax**

```SQL
-- Apply PRIMARY KEY to single column
CREATE TABLE table_name
(
    column_name DATATYPE(SIZE) PRIMARY KEY,
    column_name DATATYPE(SIZE),
...
)

-- Apply PRIMARY KEY to group of columns
-- Below syntax also can be used to give a name to PRIMARY KEY Constraint
CREATE TABLE table_name
(
    column_name DATATYPE(SIZE),
    column_name DATATYPE(SIZE),
    ...
    CONSTRAINT constraint_name PRIMARY KEY (column_name, column_name, ...)
)

```

**Example**

```sql
    CREATE TABLE product
    (
        product_id varchar2(5) PRIMARY KEY
        name VARCHAR2(50),
    	price NUMBER(10,2),
    	description VARCHAR2(150)
    )
```

## Apply PRIMARY KEY constraint on already created table

Below syntax can be used to apply PRIMARY KEY Constraint on already created table.

**Syntax**

```sql
-- Add PRIMARY KEY Without giving a constraint name
ALTER TABLE table_name
ADD PRIMARY KEY (column_name)

-- Add PRIMARY KEY and also to give constraint a name
ALTER TABLE table_name
ADD CONSTRAINT constraint_name PRIMARY_KEY (column_name)
```

**Example**

```sql
ALTER TABLE product
ADD PRIMARY KEY (product_id)

-- PRIMARY KEY with constraint name
ALTER TABLE product
ADD CONSTRAINT PK_Product_Id PRIMARY KEY (product_id)
```

## Remove PRIMARY KEY constraint

Below command can be used to drop PRIMARY KEY constraint

**Syntax**

```sql
ALTER TABLE table_name
DROP CONSTRAINT constraint_name
```

**Example**

```sql
ALTER TABLE product
DROP CONSTRAINT PK_Product_Id
```

