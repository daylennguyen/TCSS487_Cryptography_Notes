Day 3 Database Model, Reasoning
======


### Components of a Database system
>	Users > Database application > DBMS > Database


#### Database
> Actual structure containing data

#### DBMS (Database Management System)
> Accepts SQL
> Program that reads/writes directly to database(s)
> 	Create, Process, Administer

### Application
> Computer program that end users work with
> Program used by users to work with database
> Interface used by users

What is a **Database Model** ?
------  


### Model
>	- Entities ()
>	  - ex. Course: Has a course number, location, time
>	  - Teams, Games, Students, Courses
>	- Relationships 
>	  - (e.g., The Patriots are playing the Seahawks)
>	- Even active components
>	  - A student may not register for more than 5 courses
>	  - An employee may not get paid more than their manager  

## Why use a database?

### **Problem 1:** Data **redundancy** and inconsistency (Data stored as txt, xls, rtf?)
 > 	- Duplication of information in different files
 > 	    - Update John Smith inn one file, not the other -> inconsistency
 > 	      - Storing data in a system more than once, there are two problems
 > 	        - You must update it multiple times at multiple locations
 > 	          - Information is inconsistent 
 > 	        - Wasting Space/Money, it takes more data to store values multiple times

### **Problem 3:** Data integrity

> - Concurrency: Prevent simultaneous modifications
> - Resiliency: Coping for system crashes
> - Checks Preventing data entry errors
> - Security problems (Authentication)
___
#### The Key Characteristic of databases: Related Tables

> Each relationship is going to become a table
>
> Tables will contain multiple entities that may contain their own tables

### Schemas

> Relation schema = relation (table) name and attribute list
>
> Schema is the description of the table (The Table name)
>
> - The Table name
> - The Col names
> - ​



## Naming Conventions in the textbook

------

###### Table names: all capital letters:

- >  STUDENT, CLASS, GRADE

###### Column names: CamelCase

- > Term, Section, ClassNumber, StudetName

----------



## Database Applications: Forms

______

> - Allows for the naive use to enter data to the database

##  Database: Reports

------



> ### Insert data into the tables through queries
>
> - We are going to convert the ER model into tables
> - Then, we are going to write queries to enter data into the tables

## Database applications: Queries

______

~~~sql

~~~

​	SELECT 		LastName, FirstName, EmailAddress

​	FROM		STUDENT

​	WHERE		StudentNumber > 2

##Microsoft Access:

______

######  *Microsoft Access*

> - Low-end product intended for individual users / small workgroups
> - Attempts to hide underlying database tech from the user

### The Relational Database model

______

> - Dominant database model: **relational** database model
>   - All major DBMS products are based on it



