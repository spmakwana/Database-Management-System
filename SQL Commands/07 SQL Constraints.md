# Table of contents

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
- [FOREIGN KEY Constraint](#foreign-key-constraint)
  - [Apply FOREIGN KEY Constraint when creating a new table](#apply-foreign-key-constraint-when-creating-a-new-table)
  - [Apply FOREIGN KEY constraint on already created table](#apply-foreign-key-constraint-on-already-created-table)
  - [Remove FOREIGN KEY constraint](#remove-foreign-key-constraint)
- [CHECK Constraint](#check-constraint)
  - [Apply CHECK Constraint when creating a new table](#apply-check-constraint-when-creating-a-new-table)
  - [Apply CHECK constraint on already created table](#apply-check-constraint-on-already-created-table)
  - [Remove CHECK constraint](#remove-check-constraint)
- [DEFAULT Constraint](#default-constraint)
  - [Apply DEFAULT Constraint when creating a new table](#apply-default-constraint-when-creating-a-new-table)
  - [Apply DEFAULT constraint on already created table](#apply-default-constraint-on-already-created-table)
  - [Remove CHECK constraint](#remove-check-constraint)

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
    column_name DATATYPE(SIZE) UNIQUE,
    column_name DATATYPE(SIZE) UNIQUE,
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
    product_id varchar2(5) PRIMARY KEY,
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
-- PRIMARY KEY without constraint name
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

# FOREIGN KEY Constraint

- Foreign key is a column or group of column in one table, that refers to the primary key column(s) in another table.
- Foreign key is generally used to establish a relationship between two tables.
- Table with foreign key is known as child table and table with primary key is known as parent table.
- Foreign key is used so it can prevent invalid data in child table which can destroy the link between two tables.
- Foreign key ensures that we can not enter a value in foreign key column which is not available in primary key column of another table which foreign key column points to.

## Apply FOREIGN KEY Constraint when creating a new table

Below syntax can be used to apply FOREIGN KEY constraint when creating a new table.

**Syntax**

```SQL
-- Apply FOREIGN KEY to single column
CREATE TABLE table_name
(
    column_name DATATYPE(SIZE),
    column_name DATATYPE(SIZE),
	...
    FOREIGN KEY (column_name) REFERENCES table_name(column_name)
)

```

**Example**

```sql
CREATE TABLE product
(
    product_id varchar2(5) PRIMARY KEY,
    name VARCHAR2(50),
    price NUMBER(10,2),
    description VARCHAR2(150)
)

CREATE TABLE order
(
    order_no NUMBER(5) PRIMARY KEY,
    order_date DATE,
    product_id VARCHAR2(5),
    quantity number(2),
    FOREIGN KEY (product_id) REFERENCES product(product_id)
)
    
```

## Apply FOREIGN KEY constraint on already created table

Below syntax can be used to apply FOREIGN KEY Constraint on already created table.

**Syntax**

```sql
-- Add FOREIGN  KEY Without giving a constraint name
ALTER TABLE table_name
ADD FOREIGN KEY (column_name) REFERENCES table_name(column_name)

-- Add FOREIGN  KEY and also to give constraint a name
ALTER TABLE table_name
ADD CONSTRAINT constraint_name
FOREIGN KEY (column_name) REFERENCES table_name(column_name)
```

**Example**

```sql
-- FOREIGN KEY without constraint name
ALTER TABLE order
ADD FOREIGN KEY (product_id) REFERENCES product(product_id)

-- FOREIGN KEY with constraint name
ALTER TABLE order
ADD CONSTRAINT FK_Product_Id 
FOREIGN KEY (product_id) REFERENCES product(product_id)
```

## Remove FOREIGN KEY constraint

Below command can be used to drop FOREIGN KEY constraint

**Syntax**

```sql
ALTER TABLE table_name
DROP CONSTRAINT constraint_name
```

**Example**

```sql
ALTER TABLE product
DROP CONSTRAINT FK_Product_Id
```

# CHECK Constraint

- This constraint is defined on a column of the table. 
- The constraint can be applied for a single column or a group of columns.
- It Limits the data values of column to a specific set of values based on condition. 
- It is applied for data validation, so only data which satisfy the given condition can be inserted. If the data does not meet the criteria the operation is aborted and the data will not be inserted into the table.
- Example
  - E.g. Amount must be greater than 500. 
  - E.g. Marks must be between 0 and 100
  - E.g. Gender must be Male, Female or Transgender.

## Apply CHECK Constraint when creating a new table

Below syntax can be used to apply CHECK constraint when creating a new table.

**Syntax**

```SQL
-- Apply CHECK constraint without giving a constraint name
CREATE TABLE table_name
(
    column_name DATATYPE(SIZE) CHECK (CONDITION),
    column_name DATATYPE(SIZE) CHECK (CONDITION),
	...
)

-- Apply CHECK constriant and difine a constraint name
CREATE TABLE table_name
(
    column_name DATATYPE(SIZE),
    column_name DATATYPE(SIZE),
	...
    CONSTRAINT constraint_name CHECK (CONDITION)
)
```

**Example**

```sql
-- Apply CHECK constraint without giving a constraint name
CREATE TABLE product
(
    product_id varchar2(5) PRIMARY KEY,
    name VARCHAR2(50),
    price NUMBER(10,2) CHECK (price >= 0),
    description VARCHAR2(150)
)

-- Apply CHECK constriant and also give constraint a name
CREATE TABLE product
(
    product_id varchar2(5) PRIMARY KEY,
    name VARCHAR2(50),
    price NUMBER(10,2),
    description VARCHAR2(150)
    CONSTRAINT Price_Check CHECK(price >= 0)
)
```

## Apply CHECK constraint on already created table

Below syntax can be used to apply CHECK Constraint on already created table.

**Syntax**

```sql
-- Add CHECK Without giving a constraint name
ALTER TABLE table_name
ADD CHECK (condition)

-- Add CHECK and also to give constraint a name
ALTER TABLE table_name
ADD CONSTRAINT constraint_name
CHECK (condition)
```

**Example**

```sql
-- Add CHECK Without giving a constraint name
ALTER TABLE product
ADD CHECK (price >= 0)

-- Add CHECK and also to give constraint a name
ALTER TABLE product
ADD CONSTRAINT Price_Check
CHECK (price >= 0)
```

## Remove CHECK constraint

Below command can be used to drop CHECK constraint

**Syntax**

```sql
ALTER TABLE table_name
DROP CONSTRAINT constraint_name
```

**Example**

```sql
ALTER TABLE product
DROP CONSTRAINT Price_Check
```

# DEFAULT Constraint

DEFAULT Constraint is used to set a default value of a column. If value is not specified when inserting the record then default value is inserted in the specified column.

## Apply DEFAULT Constraint when creating a new table

Below syntax can be used to apply DEFAULT constraint when creating a new table.

**Syntax**

```SQL
CREATE TABLE table_name
(
    column_name DATATYPE(SIZE) DEFAULT 'value',
    column_name DATATYPE(SIZE) DEFAULT 'value',
	...
)
```

**Example**

```sql
CREATE TABLE product
(
    product_id varchar2(5) PRIMARY KEY,
    name VARCHAR2(50),
    price NUMBER(10,2) DEFAULT 0,
    description VARCHAR2(150) DEFAULT 'No description is available'
)
```

## Apply DEFAULT constraint on already created table

Below syntax can be used to apply DEFAULT Constraint on already created table.

**Syntax**

```sql
ALTER TABLE table_name
MODIFY column_name DEFAULT 'value'
```

**Example**

```sql
ALTER TABLE product
MODIFY price DEFAULT 0
```

## Remove CHECK constraint

Below command can be used to drop CHECK constraint

**Syntax**

```sql
ALTER TABLE table_name
ALTER COLUMN column_name DROP DEFAULT
```

**Example**

```sql
ALTER TABLE product
ALTER COLUMN price DROP DEFAULT
```
