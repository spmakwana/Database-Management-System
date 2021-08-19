# Practical 1

**Create a table ACCOUNT**

![image-20210819144321164](images/image-20210819144321164.png)

**Solution**

```sql
create table account
(
    acc_no varchar2(5),
    name varchar2(30),
    city varchar2(20),
    balance number (10,2),
    loan_taken varchar2(5)
)
```

**Insert the following records into table account**

![image-20210819144517402](images/image-20210819144517402.png)

```sql
insert into account (acc_no, name, city, balance, loan_taken) values ('A001', 'Patel Jigar', 'Mehsana', '50000', 'YES')
insert into account (acc_no, name, city, balance, loan_taken) values ('A002', 'Patel Ramesh', 'Mehsana', '50000', 'YES')
insert into account (acc_no, name, city, balance, loan_taken) values ('A003', 'Dave Hardik', 'Ahmedabad', '50000', 'NO')
insert into account (acc_no, name, city, balance, loan_taken) values ('A004', 'Soni Hetal', 'Ahmedabad', '50000', 'NO')
insert into account (acc_no, name, city, balance, loan_taken) values ('A005', 'Sony Atul', 'Vadodara', '50000', 'YES')
```

