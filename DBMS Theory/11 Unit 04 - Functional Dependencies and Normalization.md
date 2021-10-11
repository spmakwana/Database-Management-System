# Functional Dependencies

A functional dependency is a constraint that specifies the relationship between two sets of attributes where one set can accurately determine the value of other sets.

It is denoted as **X → Y**, where X is a set of attributes that is capable of determining the value of Y

The attribute set on the left side of the arrow, **X** is called **Determinant**, while on the right side, **Y** is called the **Dependent**.

**Example**

| Enrolment no | Name  | Mark | Pin code | City      |
| ------------ | ----- | ---- | -------- | --------- |
| 1            | Arjun | 30   | 361001   | Jamnagar  |
| 2            | Bhim  | 25   | 361002   | Rajkot    |
| 3            | Arjun | 35   | 361003   | Ahmedabad |
| 4            | Nakul | 25   | 361002   | Rajkot    |

From above we can conclude

Enrolment No. → Name

Enrolment No. → Mark

Enrolment No → City

Pin code → City



**Some Invalid Functional Dependencies**

Name → Mark

Name → Pin code

# Types of Functional Dependencies

## Trivial Functional Dependencies

In Trivial Functional Dependency, a dependent is always a subset of the determinant.
i.e. If **X → Y** and **Y is the subset of X**, then it is called trivial functional dependency

**Example**

{Enrolment No., Name} → Name

Name → Name

## Non-trivial Functional Dependency

In Non-trivial functional dependency, the dependent is strictly not a subset of the determinant.
i.e. If **X → Y** and **Y** **is not a subset of X**, then it is called Non-trivial functional dependency.

**Example**

Enrolment No. → Name

Enrolment No. → Mark

## Transitive Functional Dependency

n transitive functional dependency, dependent is indirectly dependent on determinant.
i.e. If a → b & b → c, then a → c. This is a transitive functional dependency  

**Example**

if **Enrolment No. → Pin code** & **Pin code → city** then **Enrolment No. → city**

# Normalization

**Normalization** is the process of minimizing **redundancy** from a relation or set of relations. Redundancy in relation may cause insertion, deletion and updation anomalies. So, it helps to minimize the redundancy in relations. **Normal forms** are used to eliminate or reduce redundancy in database tables.

## First Normal Form (1NF)

For a relation to be in first normal form, it must satisfy below conditions.

1. Must not contain any multivalued attribute.
2. Must not contain any composite attribute.

Relation is in first normal for if all of its attributes are single valued attribute.

**Example**

| Enrolment No | Name       | Subject                  |
| ------------ | ---------- | ------------------------ |
| 1001         | Yudhisthir | Sanskrit, Gujarati       |
| 1002         | Bhim       | Sanskrit, English        |
| 1003         | Arjun      | Gujarati, English, Hindi |

In above relation Subject is multivalued attribute, so this relation is not in first normal form. This can cause update anomalies. To make this relation in first normal form either we can write subject on different tuple or we can decompose (split) relation into two relations.

| Enrolment No | Name       | Subject   |
| ------------ | ---------- | --------- |
| 1001         | Yudhisthir | Sanskrit, |
| 1001         | Yudhisthir | Gujarati  |
| 1002         | Bhim       | Sanskrit  |
| 1002         | Bhim       | English   |
| 1003         | Arjun      | Gujarati  |
| 1003         | Arjun      | English   |
| 1003         | Arjun      | Hindi     |

Now above relation do not contain any multivalued attribute, so it is now in first normal form.

Another way is to decopose the table.

| Enrolment No | Name       |
| ------------ | ---------- |
| 1001         | Yudhisthir |
| 1002         | Bhim       |
| 1003         | Arjun      |

| Enrolment No | Subject   |
| ------------ | --------- |
| 1001         | Sanskrit, |
| 1001         | Gujarati  |
| 1002         | Sanskrit  |
| 1002         | English   |
| 1003         | Gujarati  |
| 1003         | English   |
| 1003         | Hindi     |

Now above relations do not contain any multivalued attribute, so it is now in first normal form.

## Second Normal Form (2NF)

For a relation to be in second normal form, it must satisfy below conditions.

- Relation must be in first normal form
- Must not contain any partial dependencies.

### Partial Dependencies

Partial Dependencies means any non prime attribute (attribute which not part of any candidate key) is dependent on any proper subset of any candidate key of a relation.

**Example**

| Enrolment No | Certification Course | Fee  |
| ------------ | -------------------- | ---- |
| 1001         | Java                 | 5000 |
| 1001         | .NET Programming     | 8000 |
| 1002         | PHP                  | 4000 |
| 1003         | Java                 | 5000 |
| 1003         | PHP                  | 4000 |
| 1003         | .NET Programming     | 8000 |

Here we can see that 

- (Enrolment No, Certification Course) is composite primary key.
- Fee can not determine Certification Course or Enrolment No so it is non prime attribute which is not part of any candidate key.

Here Fee can be determine by Certification Course (Certification Course → Fee)

Hence we can say that Fee is non prime attribute which can be determine by Certification Course which is subset of composite candidate key. So it is partial dependencies. Which can cause data redundancy.

To eliminate this we can discompose relation into two relations to make these relations into second normal form as follows.

| Enrolment No | Certification Course |
| ------------ | -------------------- |
| 1001         | Java                 |
| 1001         | .NET Programming     |
| 1002         | PHP                  |
| 1003         | Java                 |
| 1003         | PHP                  |
| 1003         | .NET Programming     |

| Certification Course | Fee  |
| -------------------- | ---- |
| Java                 | 5000 |
| .NET Programming     | 8000 |
| PHP                  | 4000 |

> Note: If table do not have any composite candidate / primary key then table is already in the second normal form.

## Third Normal Form (3NF)

For a relation to be in second normal form, it must satisfy below conditions.

- Relation must be in second normal form.
- There must not be any transitive dependencies for any non prime attribute.

**Example**

| ID   | Name       | State          | Country | Age  |
| ---- | ---------- | -------------- | ------- | ---- |
| 1001 | Yudhisthir | Gujarat        | India   | 55   |
| 1002 | Bhim       | Madhya Pradesh | India   | 54   |
| 1003 | Arjun      | Gujarat        | India   | 53   |

In above relation

ID → Name, ID → State, ID → Country, State → Country, ID → Age are various Functional dependencies and ID is candidate key.

For this relation ID → State and State → Country hold true. So ID → Country is transitive dependency. Country is non prime attribute so it violates the rule of third normal form.

To convert this relation into third normal form we can decompose this relation as below.

| ID   | Name       | State          | Age  |
| ---- | ---------- | -------------- | ---- |
| 1001 | Yudhisthir | Gujarat        | 55   |
| 1002 | Bhim       | Madhya Pradesh | 54   |
| 1003 | Arjun      | Gujarat        | 53   |

| State          | Country |
| -------------- | ------- |
| Gujarat        | India   |
| Madhya Pradesh | India   |

## Boyce-Codd Normal Form (BCNF)

Boyce-Codd Normal Form is a slightly stronger version of the third normal form (3NF). Sometimes also known as 3.5NF

For a relation to be in Boyce-Codd normal form, it must satisfy below conditions.

- Relation must be in third normal form.
- For every functional dependency, LHS must be super key. (i.e. for every functional dependency X → Y, X must be a super key)

Only in rare cases does a 3NF table not meet the requirements of BCNF. A 3NF table that does not have multiple overlapping candidate keys is guaranteed to be in BCNF.
