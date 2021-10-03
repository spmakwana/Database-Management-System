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

