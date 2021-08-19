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

