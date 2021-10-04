1. Display the sum of balance of account holders who’s live in same city ‘Mehsana’ using group by clause.
```sql
select sum(balance) from account group by city having city='Mehsana'
```
2. Display the information about account where balance is less than total balance of all account holders.
```sql
select *from account where balance<(select sum (balance) from account)
```
3. Displays the information of account holders whose loan amount and balance both are same.
```sql
select * from account inner join loan on account.acc_no=loan.acc_no where account.balance=loan.loan_amt
```
4. Display the name of city, remaining loan amount, account, date of loan and loan number of account holders.
```sql
select account.city, loan.remaining_loan, account.acc_no, loan.loan_date, loan.loan_no from account inner join loan on account.acc_no=loan.acc_no
```
5. Display name of account holder, installment number and installment amount Whose loan number is ‘L001’.
```sql
select loan.acc_no, name, inst_no, amount from account inner join loan on account.acc_no=loan.acc_no inner join installment on loan.loan_no=installment.loan_no where loan.loan_no='L001'
```
6. Display name of account holder, city, loan amount and installment amount.
```sql
select name, city, loan_amt, amount from account inner join loan on account.acc_no=loan.acc_no inner join installment on loan.loan_no=installment.loan_no
```
7. Display the balance of account holders whose balance and remaining loan both are same.
```sql
select balance from account inner join loan on account.acc_no = loan.acc_no where account.balance=loan.remaining_loan 
```
8. List of all account holders’ information whose balance is same as loan amount.
```sql
select account.acc_no,name,city,balance,loan_taken from account inner join loan on account.acc_no = loan.acc_no where account.balance=loan.loan_amt
```
9. Display the amount of transaction, name of account holders, account number and mode of payment whose mode of payment is ‘CHEQUE’.
```sql
select amt, name, account.acc_no, mode_of_pay from account inner join transaction on account.acc_no=transaction.acc_no where mode_of_pay='Cheque'
```
10. Display account no, loan amount, amount of transaction.
```sql
select account.acc_no, loan_amt, amt from account inner join loan on account.acc_no=loan.acc_no inner join transaction on transaction.acc_no=loan.acc_no
```
11. List of installment information whose amount is less than average amount of transaction.
```sql
select * from installment where amount < (select avg(amt) from transaction)
```
12. Display the sum of installment amount and transaction amount.
```sql
select sum (amount) from installment
union
select sum(amt) from transaction
```
13. Display the balance and amount of transaction group by amount and balance.
```sql
select amt, balance from transaction inner join account on account.acc_no=transaction.acc_no group by amt, balance;
```
14. List of installment number and account number of account holders.
```sql
select account.acc_no, inst_no from account inner join loan on account.acc_no = loan.acc_no inner join installment on loan.loan_no = installment.loan_no
```
15. Display loan amount, transaction amount and mode of payment where transaction date and loan taken date both are done in month of ‘MAY’.
```sql
select * from account full join loan on account.acc_no = loan.acc_no full join transaction on account.acc_no = transaction.acc_no where to_char(loan.loan_date,'mon')='May' and to_char(transaction.tr_date,'mon')='May';
```
16. Display all the information of installment and transaction where installment date and transaction date both are done in month of ‘JULY’.
```sql
select * from installment,transaction where to_char(inst_date,'mon')='July' and to_char(tr_date,'mon')='July';
```
17. Display the last three row of account table.
```sql
select * from account
intersect
select * from account where acc_no >= 'A003'
```
18. Display the balance, mode of payment, loan taken status whose mode of payment is ‘CHEQUE’ and loan taken is ‘YES’.
```sql
select account.balance,transaction.mode_of_pay,account.loan_taken from account full join loan on account.acc_no=loan.loan_no full join transaction on account.acc_no=transaction.acc_no where transaction.mode_of_pay='Cheque' and account.loan_taken='YES';
```
19. Retrieve only rows 2 to 5 from account table.
```sql
select * from account where rownum <= 5 
minus
select *from account where rownum < 2;
```