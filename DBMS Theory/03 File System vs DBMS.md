# Database vs File System
## Table of Contents

- [What is DBMS?](#what-is-dbms-)
- [Where to Store Data & Information](#where-to-store-data---information)
- [File System](#file-system)
  * [File System (Advantages)](#file-system--advantages-)
  * [File System (Disadvantages)](#file-system--disadvantages-)
- [DBMS](#dbms)
  * [DBMS (Advantages)](#dbms--advantages-)
  * [DBMS (Advantages)](#dbms--advantages--1)
- [Popular DBMS](#popular-dbms)


# What is DBMS?
* A general purpose software system enabling:
* Creation of large disk-resident databases.
* Posing of data retrieval queries in a standard manner.
* Retrieval of query results efficiently.
* Concurrent use of the system by a large number of users in a consistent manner.
* Guaranteed availability of data irrespective of system failures

# Where to Store Data & Information
* Data can be stored Operating System based File System by writing custom programs in different programming language.
* Or database management system software can be used to store the data.

# File System
* We can store data & information into various files
* E.g. text file, doc file, spreadsheet etc.
* We can organize this files in our hard drive using file system.

![file system](images/file%20system.png)

> File System Diagram. All files have to be managed by user.

## File System (Advantages)
* Easily create text files, doc files, spreadsheet etc. to store the various types of data.
* Easy to manage by using Interface (File explorer) provided by Operating System. 
* Only good for small amount of data.

## File System (Disadvantages)
* When data size is large, difficult to use files and data in file system.
* Probability of data inconsistency and data redundancy data.
* Data become unstructured and non validated.
* File System (Disadvantages) (Cont.)
* Difficult to search or query the data and get useful information.
* Data is less secure
* Issues with concurrent access of data.
* Have to write programs for each data operation. Can’t anticipate all kind of queries/request.

# DBMS
* We can also store the data into Database Management System.
* Here also files of Database is stored in the Hard disk

![file system dbms](images/file%20system%20dbms.png)

> Database file management Diagrams. All database files are managed by DBMS software itself, no user involvement is necessory.

## DBMS (Advantages)
* Easy to handle large amount of data.
* Less probability of data inconsistency.
* Data redundancy is reduced.
* Structured data management.
* Possible to validate data.
* Easy to query the data.
* More secure compared to file system.
* No need to write separate program for data management and data retrieval.

* Data Access Language
* Standardized Language (SQL - Structured Query Language)
* Hence querying the data is easier.
* System development takes less efforts.
* Concentration of logical design is enough
* Provides easy way to backup facility.
* Provides way to deal with hardware failure.
* Provides way to deal with multiple concurrent users.
* Provides transaction management.

# Popular DBMS
* MySQL
* Microsoft SQL Server
* Oracle
* Microsoft Access
* MongoDB
* SQLite
