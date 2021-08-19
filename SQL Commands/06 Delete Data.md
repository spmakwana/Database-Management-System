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