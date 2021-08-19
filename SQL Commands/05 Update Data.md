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