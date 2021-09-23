# Aggregate Function

Aggregate functions takes multiple values of a column and returns a single value. For example it can return sum of all values, find minimum value, find maximum values etc.

Below are some of the aggregate functions.

# Min

It is used to find the minimum value of a selected column.

**Syntax**

```sql
SELECT MIN(column_name) FROM table_name WHERE condition
```

Example

```SQL
SELECT MIN(mark) FROM result
```

Above query will select minimum value of mark column from result table.

# Max

It is used to find the maximum value of a selected column.

**Syntax**

```sql
SELECT MAX(column_name) FROM table_name WHERE condition
```

Example

```SQL
SELECT MAX(mark) FROM result
```

Above query will select maximum value of mark column from result table.

# Sum

It is used to find the total of values of a selected column.

**Syntax**

```sql
SELECT SUM(column_name) FROM table_name WHERE condition
```

Example

```SQL
SELECT SUM(mark) FROM result
```

Above query will select sum of all the marks of mark column of result table.

# Avg

It is used to find the average of values of a selected column.

**Syntax**

```sql
SELECT AVG(column_name) FROM table_name WHERE condition
```

Example

```SQL
SELECT AVG(mark) FROM result
```

Above query will select average of all the marks of mark column of result table.

# Count

Count function can be used to count total number of rows of a table and also can be used to count number of rows that match the specified criteria of where condition.

**Syntax**

```sql
SELECT COUNT(column_name) FROM table_name WHERE condition
```

Example

```SQL
SELECT COUNT(mark) FROM result
```

Above query will count the rows of result table.