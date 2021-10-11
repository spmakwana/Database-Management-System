# Table of Content

- [Integrity Constraint](#integrity-constraint)
- [Check](#check)
- [Not NULL](#not-null)
- [Unique Key](#unique-key)
- [Primary Key](#primary-key)
- [Foreign Key](#foreign-key)

# Integrity Constraint

- Integrity constraints are the set of rules imposed on database to maintain quality of data.
- Integrity constraints ensures that any manipulation on data does not affect the data integrity.
- It secures the data management.
- Various Integrity Constraints are:
  - Check
  - Not null
  - Unique Key
  - Primary key
  - Foreign key

# Check

- This constraint is defined on a column of the table. 
- The constraint can be applied for a single column or a group of columns.
- Limits the data values of column to a specific set of values based on condition. 
- E.g. Amount must be greater than 500. 
- E.g. Marks must be between 0 and 100
- E.g. Gender must be Male, Female or Transgender.

# Not NULL

- This constraint is applied on a column of a table.
- It ensure that NULL value can not be assigned in a column.
- NULL value means empty value or no value.
- Hence every row must have some value in column where Not NULL constraint is assigned.

# Unique Key

- Unique key constraint can be assigned to column or group of column.
- It ensure that the data in column or group of column is unique (distinct).
- Unique key column(s) can not have duplicate value.
- But Unique key column(s) can have NULL values. 
- E.g. Roll Number of a student is Unique.
- E.g. Transaction Id should be Unique in banking system.

# Primary Key

- Primary key constraint can be assigned to column or group of column.
- It ensure that
  - The data in column or group of column is unique (distinct).
  - The data in column or group of column can not have duplicate value.
  - The data in column or group of column can not have NULL value.
- There can be only one primary key constraint in a table.
- E.g. Enrollment no of student can be defined as primary key.
- E.g. Transaction Id can be defined as a primary key in banking transaction.

# Foreign Key

- Foreign key is a column or group of column in one table, that refers to the primary key column(s) in another table.
- Foreign key is generally used to establish a relationship between two tables.
- Table with foreign key is known as child table and table with primary key is known as parent table.
- Foreign key is used so it can prevent invalid data in child table which can destroy the link between two tables.
- Foreign key ensures that we can not enter a value in foreign key column which is not available in primary key column of another table which foreign key column points to.
- For E.g. 
  - Student (enrolment_no, sname, branch, semester) [here enrolment_no is primary key in student table]
  - Result (enrolment_no, subject, mark) [here enrolment_no is foreign key which points to enrolment_no column of student table]

