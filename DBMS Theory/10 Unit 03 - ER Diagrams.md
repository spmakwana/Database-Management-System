# Table of contents

- [Entity Relationship Diagram](#entity-relationship-diagram)
- [Entity and Attributes](#entity-and-attributes)
  - [Types of Attributes](#types-of-attributes)
- [Relationship between entities](#relationship-between-entities)
- [Mapping Cardinalities](#mapping-cardinalities)
  - [One to One](#one-to-one)
  - [One to Many](#one-to-many)
  - [Many to One](#many-to-one)
  - [Many to Many](#many-to-many)
- [Participation Constraints](#participation-constraints)
  - [Total Participation](#total-participation)
  - [Partial Participation](#partial-participation)
- [Extended E-R Diagram](#extended-e-r-diagram)
  - [Specialization](#specialization)
  - [Generalization](#generalization)
- [ER Diagram Cheatsheet](#er-diagram-cheatsheet)

# Entity Relationship Diagram

- Stands for Entity-Relationship diagram.
- It is a graphical or a pictorial representation of a database.
- It uses different types of symbols to represent various instances of database

# Entity and Attributes

- An entity is generally a “thing” or “object” of real world which is present in the context.
- For example, each Employee in a firm is an entity.
- Each entity has various attributes.
- Attributes is used to define the different type of data of the particular entity. (in short attributes defines the detail of entity)
- For example, employee entity can have attributes like name, salary, organization, department etc.
- Each entity in ER Diagram is represented using rectangle shape with name of entity written on the rectangle.

![image-20210923150709295](images/image-20210923150709295.png)

- Attributes of entity are represented using oval/ellipse symbol.
- Attributes are connected with entity using a line.

![image-20210923150611968](images/image-20210923150611968.png)

## Types of Attributes

Attributes of entity can be categorized into several types.

### Simple - Single Value Attribute

All simple attribute which contains a single value is known as a simple or single value attribute.

e.g. Enrolment no, gender etc.

### Composite Attribute

Attribute which can be further divided into sub attribute are known as composite attribute.

e.g. name attribute can be divided into sub attribute like first name, middle name, last name.

e.g. Address attribute can be divided into sub attribute like apartment name, street address, city, pin code

Hence this type of attributes are known as composite attribute. Sub attributes of composite attribute are connected with attribute using a line.

![image-20210923153133370](images/image-20210923153133370.png)

### Multivalued Attribute

Attribute which may have more than one value are known as multivalued attribute. 

E.g. Mobile No, Phone No can have multiple value, as person can have more than one mobile or phone number.

Multivalued attribute are represented using double line oval.

![image-20210923153238025](images/image-20210923153238025.png)

### Derived Attribute

Attribute whose value can be derived from another attributes are known as derived attribute.

E.g. Value of Age attribute can be derived from Date of Birth attribute, so age is known as derived attribute.

Derived attributes are represented using dotted line oval.

![image-20210923153414726](images/image-20210923153414726.png)

### Primary Key Attribute

Attribute which will be used to uniquely identify data (records) of an entity is known as primary key attribute. 

Primary key attribute is represented as underline under the attribute name.

![image-20210924082055256](images/image-20210924082055256.png)

### Example of Entity and its attributes.

![image-20210923153839576](images/image-20210923153839576.png)

Above example demonstrate the entity employee which have five attributes named employee code, mobile no, name, date of birth and age.

Here employee code is used for uniquely identify the records of employee so it is written with underline to indicate it is a primary key attribute.

Mobile no is multivalued attribute.

Name is composite attribute containing sub attributed named first name, middle name and last name.

Date of birth is simple / single attribute.

Age is derived attribute, because it can be derived from date of birth attribute.

# Relationship between entities

- Relationship is link between several entities.
- It must be placed between two entities and a line linking it to an entity.
- A relationship is represented by a diamond containing relationship details.
- A Relationship between 2 Entities is called Binary Relationship and A Relationship between 3 Entities is called Ternary Relationship.
- Relationship are represented using Dimond symbol.

**Example**

![image-20210923155040384](images/image-20210923155040384.png)

# Mapping Cardinalities

- It defined number of entities of one entity set connected to number of entities of another entity set using a relationship set.

- Mapping cardinalities are most useful in describing binary relationship sets.
- There are four types of cardinalities.
  - One to One
  - One to Many
  - Many to One
  - Many to Many

## One to One

In one to one mapping, each data of entity A can be associated with at most one data of entity B. And each data of entity B can be associated with at most one data of entity A.

![image-20210923155923644](images/image-20210923155923644.png)

**Example**

![image-20210923160307819](images/image-20210923160307819.png)

Here each student data only can be associated with one data in result entity, and also each result data can be associated with only one data in student entity as each student can only have one result, and each result can be of only one student.

One to one mapping is represented with arrow on both side when representing relationship.

## One to Many

In one to many mapping, each data of entity A can be associated with zero, one or more data of entity B. And each data of entity B can be associated with at most one data of entity A.

![image-20210923160536466](images/image-20210923160536466.png)

**Example**

![image-20210923160640970](images/image-20210923160640970.png)

Hear each customer can take multiple loans, so each customer data can be associated with multiple loan data in the loan entity. But each loan can be only taken by one customer only. So each data on loan entity can be only associated with only one customer data in the customer entity.

One to many mapping is represented with arrow on one side and simple line on many side when representing relationship.

## Many to One

It is reverse of one to many cardinality. In many to one mapping, each data of entity A can be associated with at most one data of entity B. And each data of entity B can be associated with zero, one or more data of entity A.

![image-20210923161045088](images/image-20210923161045088.png)

**Example**

![image-20210923161133744](images/image-20210923161133744.png)

Here each loan can only be taken by one customer only, so each data of loan entity can only be associated with at most one data of customer entity. But each customer can take multiple loans, so each customer data can be associated with multiple loan data in the loan entity.

Many to one mapping is represented with simple line on many side and arrow symbol on one side when representing relationship.

## Many to Many

In many to many cardinality, each data of entity A can be associated with zero, one or more data on the entity B, and also each data of entity B can be associated with zero, one or more data on entity A.

![image-20210923161426106](images/image-20210923161426106.png)

**Example**

![image-20210923161717308](images/image-20210923161717308.png)

Here each student can studies in multiple classroom, so each data of student can be mapped to multiple data on classroom entity. And also each classroom can be allocated to different students, so each data of classroom also can be associated with multiple student data of student entity.

Many to many mapping is represented with simple lines on both side when representing relationship.

# Participation Constraints

- It specifies the participation of an entity set in a relationship set.
- There are two types participation constraints:
  - Total Participation
  - Partial Participation

## Total Participation

In total participation each data (records) of entity must be compulsory associated with at least one data (records) of other entity  participating in the relationship.

Total participation is denoted by double line between entity and relationship.

## Partial Participation

In partial participation for each data (records) of entity is not compulsory to be associated with data (records) of other entity participating in the relationship. In other words, some data of and entity many not be associated with any data of other entity.

Partial participation is denoted by single line between entity and relationship.

**Example**

![image-20210924083158159](images/image-20210924083158159.png)

Here in above example, each loan data must be associated with customer, because all the loan is taken by some customer, so it is total participation and is denoted using double lines. On the other side, It is possible that some customer may not have taken the loan, so some data of customer entity may not be associated with loan entity. So it is partial participation and is denoted using single line.

# Extended E-R Diagram

## Specialization

- The process of creating sub-groups within an entity is called specialization.

- Top-Down design process; designate subgroupings within an entity set that are distinctive from other entities in the set.

- The process of taking a subset of higher level entity set to form a lower level entity set.

- Uses a triangle component labeled as “ISA”

**Example**

![image-20210924084656391](images/image-20210924084656391.png)

## Generalization

- The process of creating a main group from different entities is called generalization.

- Bottom-Up design process; combine a number of entity sets that share the same features into a higher-level entity set.

- The process of combining two or more low level entity sets to generate high level entity set.

- Uses a triangle component labeled as “ISA”

**Example**

![image-20210924084656391](images/image-20210924084656391.png)

# ER Diagram Cheatsheet

![E R Diagram CheatSheet](images/E%20R%20Diagram%20CheatSheet.jpg)