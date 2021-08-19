# Table of contents

- [Select Data](#select-data)
  - [Select all attributes (columns) and records (rows)](#select-all-attributes-columns-and-records-rows)
  - [Select selective attributes (columns)](#select-selective-attributes-columns)
  - [Select selective records (rows)](#select-selective-records-rows)
  - [Select selective attributes (columns) and selective records (rows)](#select-selective-attributes-columns-and-selective-records-rows)

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