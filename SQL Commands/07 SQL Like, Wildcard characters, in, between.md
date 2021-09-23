# Like and Wildcard Characters

Like is used to in select query to search specific patterns. When we used = sign in condition, it search for the exact match, to search partially or pattern search we can use like operators

We have to use wild card characters when we want to search for specific patterns. Wild card characters are some special characters which is used to build patterns.

Below are some most used wild card characters.

| Wildcard Character   | Description                                                  |
| -------------------- | ------------------------------------------------------------ |
| % (Percentage Sign)  | Represents zero, one or any number of characters (characters include alphabets, numbers, special characters etc.) |
| _ (Underscore Sign)  | Represents one  (only single) character (characters include alphabets, numbers, special characters etc.) |
| [] (Square brackets) | Represent one (only single) characters specified between the brackets. |





**Syntax for Like operator**

```sql
SELECT */column_list FROM table_name WHERE column_name LIKE pattern_to_search
```

| Example                    | Description                                                  |
| -------------------------- | ------------------------------------------------------------ |
| Where name like '%laptop%' | Find records where there is laptop word in name column       |
| Where name like '%laptop'  | Find records where value of name column ends with laptop word. There can or be anything before the laptop. |
| Where name like 'laptop%'  | Find records where value of name column starts with laptop word. There can be anything after the laptop word. |
| Where name like '_a'       | Find records where value of name column ends with a and there is exactly one character before a. |
| Where name like 'c_t'      | Find records where first letter is c and last letter is t and there is exactly one character between c and t. |

# In Operator

In operator is used in select query and is used to specify multiple values in where condition. It is generally used to shorten multiple conditions combined with OR logical operator.

**Syntax**

```sql
SELECT */column_list FROM table_name WHERE column_name in (value1, value2, value3, ...)
```

**Example**

```sql
SELECT * FROM students WHERE city in ('Ahmedabad', 'Delhi', 'Mumbai')
```

Above query will fetch the records of student table whose city are either Ahmedabad, Delhi or Mumbai.

# Not In Operator

Not in operator is used in select query and used to specify multiple values in where condition. It is opposite of in operator. It fetch all records whose value does not match with the values specified in the where condition.

**Syntax**

```sql
SELECT */column_list FROM table_name WHERE column_name not in (value1, value2, value3, ...)
```

**Example**

```sql
SELECT * FROM students WHERE city not in ('Ahmedabad', 'Delhi', 'Mumbai')
```

Above query will fetch the records of student table whose city is not Ahmedabad, Delhi and Mumbai. It will display all records except student with city value Ahmedabad, Delhi and Mumbai.

# Between Operator

Between operator is used to select the data between specified range. It can be used on numbers, date and also text data.

**Syntax**

```sql
SELECT */column_list FROM table_name WHERE column_name between value1 and value2
```

**Example**

```sql
SELECT * FROM product WHERE price between 1000 and 5000
```

Above query will fetch all the data from product table where the value of price column is between 1000 and 5000 rupees.

# Not Between Operator

Not between operator is reverse of between operator. It is used to select the data which is outside of specified range. It can be used on numbers, date and also text data.

**Syntax**

```sql
SELECT */column_list FROM table_name WHERE column_name not between value1 and value2
```

**Example**

```sql
SELECT * FROM product WHERE not price between 1000 and 5000
```

Above query will fetch all the data from product table where the value of price column is outside 1000 and 5000 range.
