# Table of contents

- [Relational Algebra](#relational-algebra)
  - [Operations in Relational Algebra](#operations-in-relational-algebra)
- [SELECT Operation](#select-operation)
- [PROJECT Operation](#project-operation)
- [Combination of SELECT and PROJECT Operation](#combination-of-select-and-project-operation)
- [UNION Operation](#union-operation)
- [INTERSECTION Operation](#intersection-operation)
- [SET DIFFERENCE Operation](#set-difference-Operation)

# Relational Algebra

- Relational Algebra is procedural query language, which takes Relation as input and generate relation as output.
- Relational algebra mainly provides theoretical foundation for relational databases and SQL.
- In relational algebra input is a relation (table) and output is also a relation (table) (temporary table holding the data asked by the user)

## Operations in Relational Algebra

- Unary Relational Operation
  - SELECT (Symbol σ) (Sigma)
  - PROJECT (Symbol ∏) (Pi)
  
- Binary Relational Operation

  - Operations from set theory
    - UNION (Symbol ∪)
    - INTERSECTION (Symbol ∩)
    - DIFFERENCE (Symbol −)
    - CARTESIAN PRODUCT (Symbol Χ)

  - JOIN 
    - Inner JOIN
    - Left Outer JOIN
    - Right Outer JOIN
    - Full Outer JOIN
  - DIVISION

# SELECT Operation

- **Symbol** : σ (SIGMA)

![image-20210819101109443](images/image-20210819101109443.png)

- **Operation:** Display particular tuples from a relation that satisfy a given condition (predicate) 
- **Operators:** =, <>, <, >, <=, >=, ^ (AND), v (OR)

**Example 1:**

- Select all account whose balance is greater then 100000 from relation SavingAaccount

![image-20210819100921515](images/image-20210819100921515.png)

**Example 2**

Below is the relation named 'r'. From relation r select the records where a = b and d > 5. When we use the below Select operation to find the below output relation is generated.

![Select Operation Example](images/image-20210818104933407.png)

**Exercise**

![Student Table for select operation](images/image-20210818105029020.png)

Above is the relation Student. Find below using Select operation

**Questions**

1. Display the detail of students belongs to “Rajkot” city.
2. Display the details students whose name is Karan
3. Display the details of students who is studying in EC branch
4. Display the details of students who are living in Mumbai and studying in CE branch
5. Display the details of students who are living in Delhi and Patna
6. Display the details of students whose enrolment no is S3 and S5

**Answers**

![image-20210819101549503](images/image-20210819101549503.png)

# PROJECT Operation

- **Symbol:** Π (Pi)

![image-20210819101720989](images/image-20210819101720989.png)

- **Operation:** Selects specified attributes of a relation.
- Project operation selects certain columns from a table while discarding others.
- It removes any duplicate tuples (records) from the result.
- The result of the project operation has only the attributes specified in the attribute list and in the same order as they appear in list.

**Example 1**

List out all account number and name from SavingAccount relation

![image-20210819101815804](images/image-20210819101815804.png)

**Example 2**

![image-20210818111826469](images/image-20210818111826469.png)

**Exercise**

![Student table for project operation](images/image-20210818114247849.png)

Above is the relation Student. Find below using Project operation

**Questions**

1. Display the Enrollno, Name and city of all students.
2. Display Enrollno, branch, name of students
3. Display branch, name, city of students
4. Display name, Enrollno, branch of students

**Answers**

![image-20210819102105782](images/image-20210819102105782.png)

# Combination of SELECT and PROJECT Operation

We can also combine Select and Project operation as seen in below example.

![Student table for Select and Project operation](images/image-20210818114924295.png)

Display the Enrollno,Name and city of “IT” branch students.

![image-20210819102204016](images/image-20210819102204016.png)

**Output Relation**

![image-20210818115155944](images/image-20210818115155944.png)

# UNION Operation

![image-20210819121453948](images/image-20210819121453948.png)

- **Operation:** Operation of Union in relational algebra is same as set theory union operation. It combines the tuples (records) of the both input relation. 
- **Requirement:** Union must be taken between compatible relations
- Relation R and S are compatible, if
  - Both have same number of attributes
  - Domain of the attribute of R and S are similar

**Example 1**

![image-20210819122159546](images/image-20210819122159546.png)

In above example we have two relation named 'r' and 's'. Output of R ∪ S will display all the records of relation r and relation after combining them. If there are some duplicate records it will remove the duplicate records

**Example 2**

![image-20210819122842881](images/image-20210819122842881.png)

Above are two relation employee and relation that stores the detail of employee and student respectively.

List all the students and faculties with their department.

Here Employee relation and Student relation are not compatible relations. But the resultant relation of projection operator contains similar attribute with similar domain. So it is possible to apply union operation after applying such project operation even though the original relations are not compatible.

![image-20210819123002173](images/image-20210819123002173.png)

![image-20210819123032077](images/image-20210819123032077.png)

# INTERSECTION Operation

![image-20210819132042329](images/image-20210819132042329.png)

- **Operation:** Selects the tuples (records) which are common in both the input relations.
- **Requirement:** Union must be taken between compatible relations
- Relation R and S are compatible, if
  - Both have same number of attributes
  - Domain of the attribute of R and S are similar

**Example 1**

![image-20210819132523637](images/image-20210819132523637.png)

In above example we have two relation named 'r' and 's'. Output of R ∩ S will display only those records which are common in both the relation.

**Example 2**

![image-20210819132837311](images/image-20210819132837311.png)

Above are two relation employee and relation that stores the detail of employee and student respectively.

List all the employee who are also students.

Here Employee relation and Student relation are not compatible relations. But the resultant relation of projection operator contains similar attribute with similar domain. So it is possible to apply intersection operation after applying such project operation even though the original relations are not compatible.

![image-20210819133057271](images/image-20210819133057271.png)

![image-20210819133119603](images/image-20210819133119603.png)

# SET DIFFERENCE Operation

- **Symbol:** - (minus sign)
- **Notation:** Relation1_name - Relation2_name
- **Operation: ** Returns all the records from relation1 (left relation) after removing the common records of relation1 and relation2.

**Example**

![image-20210819133925721](images/image-20210819133925721.png)

Above are two relation employee and relation that stores the detail of employee and student respectively.

List all the employee who are not students.

Here Employee relation and Student relation are not compatible relations. But the resultant relation of projection operator contains similar attribute with similar domain. So it is possible to apply set difference operation after applying such project operation even though the original relations are not compatible.

![image-20210819134127657](images/image-20210819134127657.png)

![image-20210819134205969](images/image-20210819134205969.png)

