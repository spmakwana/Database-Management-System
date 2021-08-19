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