# Table of contents

- [Create Tables](#create-tables)
- [Modify Table Structure](#modify-table-structure)
  - [Add Column to Table](#add-column-to-table)
  - [Remove Column from Table](#remove-column-from-table)
  - [Modify Column Datatype](#modify-column-datatype)
  - [Rename Column](#rename-column)
  - [Rename Table](#rename-table)

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