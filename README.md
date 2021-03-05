# Introduction to SQL
# What is a database?
- Any collection of related information
    - Phone book
    - shopping list
    - todo list
    - your 5 best friends
    - Faceboks user base

- Databases can be stored in diffeerent ways
    - On paper
    - In your mind
    - On computer
    - Powerpoint
    - Comments section

## Database management systems (DBMS)
- A special software program that helps users create and maintain a database
    - Makes ir easy to manage large amounts of information
    - Handles security
    - Backups
    - Importing/exporting data
    - Concurrency
    - Ineteracts with software applications
        - Programming languages
- CRUD: Create, read(retrieve), update, delete
## Two types of Databases

- Relational databases (SQL)
    - Organize data into one or more tables
        - Each table has columns and rows
        - A unique key identifies each row
- Non-relational  (noSQL/ not just SQL)
    - Organize data is anything but a traditional table
        - Key-value stores
        - Documents (JSON,XML)
        - Graphs
        - Flexible Tables

### Relational databases (SQL)
Student table

|ID# | Name |Major      |
|:--- |:----:|----------:|
|1   |Jack  |  Biology  |
|2   |Kate  |  Sociology|
|3   |Claire|  English  |
|4   |John  |  Chemistry|

Users table

|*Username | PAssword |Email      |
|:--- |:----:|----------:|
|jsmith22     |wordpass  |  ...  |
|catlover45   |apple223  |  ...|
|gamerkid     |...|  ...  |
|giraffe     |...  |  ...|

- Relational database management systems (RDBMS)
    - Help users create and maintain a relational database
        - MySQL, Oracle, postgreSQL, mariaDB
- Structued Query Language (SQL)
    - Standarized language for interacting with RDBMS
    - Used to perform CRUD operations, as well as other administrative tasks (user management, security, backup)
    - Used to define tables and structures
    - SQL code used on one RDBMS is not always portable to another without modification.

### Non-Relational Databases (noSQL / not just SQL)
- Document
    - JSON, BLOB, XML
- Graph
    - Relational nodes
- Key-value hash
    - Keys are mapped to values (strings, json,blob)

|Key | Value |
|:----------- |---------:|
|"XYZ"     |string  |
|"abc"   |JSON  |
|"pqr"     |BLOB       |
|"lmno"      |etc...      |

- Non-relational databases management systems (NRDBMS)
    - Help users create and maintain a non-relational database
        - mongoDB, dynamoDB, apache cassandra, firebase
- Implementation specific
    - Any nonrelational database falls under this categoy, so there's no set language standard
    - Most NRDBMS will implement their own language for performing CRUD and administrative operations on te database

## Database queries
Queries are requests made to the database management system for specific information.

As the databese's structure more and more complex, it becomes more difficult to get the specific pieces of information we wamnt.

A google search is a query

## Wrap up
- Database is any collection of related information
- Computers are great for sotring databases
- Database management systems DBMS make it easy to create, maintain and secure a database
- DBMS allow you to perform the CRUD operations and other administrative tasks
- Two types of Databases, Relational & Non-Relational
- Relational databases use SQL and store data in tables woth rows and columns- Non-relational data store data using other data structures

# Tables and keys

|*student_id* | Name |Major      |
|:---: |:----:|:----------:|
|1   |Jack  |  Biology  |
|2   |Kate  |  Sociology|
|3   |Claire|  English  |
|4   |Jack  |  Biology|
|5   |Mike  | Comp. Sci.|

- Columns define single attributes
- Rows represent entries
- Primary key (student_id) is unique for each row although the attributes are repeated

|*email* | password |date_created| Type|
|:---: |:----:|:----------:|:---:|
|fakemail@fake.co|shivers1|1999-05-11|Admin|
|fakemail112@fake.co|wordpass|2001-03-15|Free|
|rsmith@fake.co|redRoad23|2010-09-05|Free|
|jdoe@fake.co|passw0rd|2008-06-25|Premium|
|jhalpert@fake.co|557df32d|2003+07-22  |Free|

- Primary key (email)

## Types of primary keys

### Surrogate key(emp_id): no meaning in the real world

|*emp_id*|first_name|last_name|birth_date|sex|salary|
|:---:|:---:|:---:|:---:|:---:|:---:|
|100|Jan|Levinson|1961-05-11|F|110,000|
|101|Michael|Scott|1964-03-15|M|75,000|
|102|Josh|Porter|1969-09-05|M|78,000|
|103|Angela|Martin|1971-06-25|F|63,000|
|104|Andy|Bernard|1973-07-22|M|65,000|

### Natual key (emp_ssn):  has a mapping in the real world

|*emp_ssn*|first_name|last_name|birth_date|sex|salary|
|:---:|:---:|:---:|:---:|:---:|:---:|
|123456789|Jan|Levinson|1961-05-11|F|110,000|
|555667777|Michael|Scott|1964-03-15|M|75,000|
|8886665555|Josh|Porter|1969-09-05|M|78,000|
|111332467|Angela|Martin|1971-06-25|F|63,000|
|99857463|Andy|Bernard|1973-07-22|M|65,000|

### Foreign key (branch_id) : Stores the primary key of a row in another table 

|emp_id|first_name|last_name|birth_date|sex|salary|*branch_id*|
|:---:|:---:|:---:|:---:|:---:|:---:|:---:|
|100|Jan|Levinson|1961-05-11|F|110,000|1|
|101|Michael|Scott|1964-03-15|M|75,000|2|
|102|Josh|Porter|1969-09-05|M|78,000|3|
|103|Angela|Martin|1971-06-25|F|63,000|2|
|104|Andy|Bernard|1973-07-22|M|65,000|3|

Table below links the branch_id as well as the manager ID from the employees list

|*branch_id*|branch_name|mgr_id|
|:---:|:---:|:---:|
|2|Scranton|101|
|3|Stamford|102|
|1|Corporate|108|

Table below shows foreign id within same table linking each employee with their respective supervisor.

> Employee

|emp_id|first_name|last_name|birth_date|sex|salary|branch_id|*super_id*|
|:---:|:---:|:---:|:---:|:---:|:---:|:---:|:---:|
|100|Jan|Levinson|1961-05-11|F|110,000|1|NULL|
|101|Michael|Scott|1964-03-15|M|75,000|2|100|
|102|Josh|Porter|1969-09-05|M|78,000|3|100|
|103|Angela|Martin|1971-06-25|F|63,000|2|101|
|104|Andy|Bernard|1973-07-22|M|65,000|3|101|

###  Composite key (branch_id, supplier_name) : Key of two attributes, each row is uniquely identified by both attributes together
> Branch

|*branch_id*|*supplier_name*|supply_type|
|:---:|:---:|:---:|
|2|Hammer Mill|Paper|
|2|Uni-ball|Writing utensils|
|3|PAtriot Paper|Paper|
|2|J.T. Forms & Labels|Custom Forms|
|3|Uni-ball|Writing Utensils|
|3|Hammer Mill|Paper|
|3|Stamford Lables|Custom Forms|

> Client

|*client_id*|client_name|branch_id|
|:---:|:---:|:---:|
|400| Dunmore Highschool |2|
|401| Lackawaba Country |2|
|402| FedEx |3|
|403| John Daly Law, LLC |3|
|404| Scranton Whitepages |2|

> Works_with

|*emp_id*|*client_id*|total_sales|
|:---:|:---:|:---:|
|107 | 400 | 55,000|
|101| 401| 267,000|
|105| 402| 22,500|
|104| 403| 5,000|
|405| 403| 12,000|
|107| 404| 33,000|

# SQL Basics
## Structured Query Language (SQL)
- SQL is a language used for interacting with Relational Database Management Systems (RDBMD)
     - YOu can use SQL to get the RDBMS to do things for you
        - Create, retrieve, update & delete data
        - Create & manage databases
        - Design & create databse tables
        - Perform administration tasks (security, user management, import/export)
- SQL imlementations vary between systems
    - Not all RDBMS folow the SQL standard to a 'T'
    - The concepts are the same but the implementation may vary
- SQL is actually a hybrid language, it's basically 4 types of languages in one
    - Data Query Language (DQL)
        - Used to query the database for information
        - Get information that is already stored there
    - Data Definition Language (DDL)
        - Used for defining databases schemas
    - Data Control Language (DCL)
        - Used for controlling access to the data in the database
        - User & permissions management
    - Data Magipulation Language (DML)
        - Used for isnerting, updating and deleting data from the database

## Queries
- A query is a set of instructuons given to the RDBMS (written in SQL) that tell the RDBMS what information you want it to retrieve for you
    - TONS of data in a DB
    - Often hidden in a complex schema
    - Goal is to only get the data you need
    - Example:
``` sql
SELECT employee.name,employee.age
  FROM employee
  WHERE employee.salary > 30000;
```

>  Start mySQL

``` console
user@machine:~$ sudo mysql -u root -p
```
> Change the password
``` sql
mysql> ALTER USER 'root'@'localhost' IDENTIFIED BY 'password';
Query OK, 0 rows affected (0.01 sec)
mysql> exit
```
>  log in again and use 'password'

``` console
(base) user@machine:~$ sudo mysql -u root -p
mysql> 
```
> Create a database
``` sql
mysql> create database database_name;
```
> All commands can be submitted via command line but other programs can be used: PopSQL
``` sql
USE database_name
```
# Creating Tables
## Datatypes
``` sql
INT -- Whole Numbers
DECIMAL(M,N) -- Decimal numbers - Exact value
VARCHAR(1) -- String of text of length 1
BLOB -- Binary Large Object, Stores large data
DATE -- 'YYY-MM-DD'
TIMESTAMP -- 'YYYY-MM--DD HH:MM:SS' - used for recording

```

## Creating database tables
- The following table:

|*student_id* | Name |Major      |
|:---: |:----:|:----------:|
|1   |Jack  |  Biology  |
|2   |Kate  |  Sociology|
|3   |Claire|  English  |
|4   |Jack  |  Biology|
|5   |Mike  | Comp. Sci.|

reads:

``` sql
CREATE TABLE student (
    student_id INT PRIMARY KEY,
    name VARCHAR(20),
    major VARCHAR(20)
);
```
or:

``` sql
CREATE TABLE student (
    student_id INT,
    name VARCHAR(20),
    major VARCHAR(20),
    PRIMARY KEY(student_id)
);
```
- Verify table:

``` sql
DESCRIBE student;
```
- To delete:
``` sql
DROP TABLE student;
```
- To modify table:
``` sql
ALTER TABLE student ADD gpa DECIMAL(3,2); -- Three total digits, two decimals
ALTER TABLE student DROP COLUMN gpa; -- remove a column
```
# Inserting Data

- Table declaration
``` sql
CREATE TABLE student (
    student_id INT,
    name VARCHAR(20),
    major VARCHAR(20),
    PRIMARY KEY(student_id)
);
```
- Print current state of table
``` sql
SELECT * FROM student; -- print out actual table 
```
- Add more data
``` sql
INSERT INTO student VALUES(1, 'Jack', 'Biology');
INSERT INTO student VALUES(2, 'Kate', 'Sociology');
```
- If there is missing information we can skip columns:
``` sql
INSERT INTO student(student_id,name) VALUES(3, 'Claire');
```
- No duplicate entries can be entered, running above command again will give error

# Constraints

``` sql
CREATE TABLE student (
    student_id INT,
--  student_id INT AUTO_INCREMENT, -- automatic label to primary key
    name VARCHAR(20) NOT NULL, -- no null values allowed in name
--  major VARCHAR(20) DEFAULT 'undecided', -- default value instead of null if not specified
    major VARCHAR(20) UNIQUE, -- this field should be unique for each row
    PRIMARY KEY(student_id)
);
SELECT * FROM student;

INSERT INTO student VALUES(1, 'Jack', 'Biology');
INSERT INTO student VALUES(2, 'Kate', 'Sociology');
INSERT INTO student VALUES(3, NULL, 'Chemistry'); -- NULL error
INSERT INTO student VALUES(4, 'Jack', 'Biology'); -- UNIQUE error
INSERT INTO student VALUES(5, 'Mike', 'Computer Science');

```
*do: `DROP TABLE student;` before applying changes*

# Update & Delete

change the name of the majors
``` sql
UPDATE student
SET major = 'Bio'
WHERE major = 'Biology'; -- =, <>, >, <, >=, <=
```

``` sql
UPDATE student
SET major = 'Comp Sci'
WHERE major = 'Computer Science';
```

``` sql
UPDATE student
SET major = 'Comp Sci'
WHERE student_id = 4;
```

- Any student from either biology or chemistry into biochemistry

``` sql
UPDATE student
SET major = 'Biochemistry'
WHERE major = 'Bio' OR major = 'Chemistry';
```

``` sql
UPDATE student
SET name = 'Tom'
WHERE student_id = 1;
```

``` sql
UPDATE student
SET major = 'undecided'; -- applies to all
```
- Delete data
``` sql
DELETE FROM student; -- delete all rows
```

``` sql
DELETE FROM student
WHERE student_id = 5;
```

``` sql
DELETE FROM student
WHERE name = 'Tom' AND major = 'undecided';
```

# Basic queries

``` sql
-- SELECT * -- all columns
-- SELECT name
-- SELECT name, major
SELECT student.name, student.major
FROM student
WHERE major = 'Biology' OR major = 'Chemistry'
-- WHERE name IN ('Claire', 'Kate', 'Mike')
LIMIT 2
ORDER BY name DESC -- ASC
-- ORDER BY major, student_id DESC
;
```

# Create a company database

- Create database
``` sql
mysql> CREATE DATABASE company;
```
- List databases
``` sql
mysql> SHOW DATABASES;
```
- Use database
``` sql
mysql> USE company;
```

- Load tables from script
Atable can be loaded from script `company-database.sql` as:

``` sql
mysql> SOURCE /PATH/TO/company-database.sql;
```
- List tables from database
``` sql 
mysql> SHOW TABLES from company;
```
# More basic queries

-- Find all employees
``` sql
SELECT *
FROM employee;
```
- Find all clients
``` sql
SELECT *
FROM employee;
```
- Find all employees sorted by salary
``` sql
SELECT *
FROM employee
ORDER BY salary DESC;
```
- Find all employees ordered by sex then name
``` sql
SELECT *
FROM employee
ORDER BY sex, first_name, last_name;
```
- Find the first five employees in the table
``` sql
SELECT *
FROM employee
LIMIT 5;
```
- Find the firs and last names of all employees
``` sql
SELECT first_name, last_name
FROM employee;
```
- Find the forename and surnames names of all employees
``` sql
SELECT first_name AS forename, last_name AS surname
FROM employee;
```
- Find out all the different genders
``` sql
SELECT DISTINCT sex
FROM employee;
```

# Functions

- Find the number of employees
``` sql 
SELECT COUNT(emp_id)
FROM employee;
```
- Find the number of female employees orn after 1970
``` sql
SELECT COUNT(emp_id)
FROM employee
WHERE sex = 'F' AND birth_date = > '1970-12-31';
```
- Find the average of all male employees salaries
``` sql
SELECT AVG(salary)
FROM employee
WHERE sex = 'M';
```
- Find the sum of all employee's salaries
``` sql
SELECT SUM(salary)
FROM employee;
```
- FInd out how many males and how many males there out
``` sql
SELECT COUNT(sex), sex
FROM employee
GROUP BY sex;
```
- Find the total sales of every salesman 
``` sql
SELECT SUM(total_sales), emp_id
FROM works_with
ORDER BY emp_id;
``` 

# Wildcards

``` sql
-- % = any characters, _ = one character
```
- Find any client's who are an LLC
``` sql
SELECT *
FROM client
WHERE client_name LIKE '%LLC'; -- Any number of characters ending in LLC
```
- Find any employee born in october
``` sql
SELECT *
FROM employee
WHERE birth_date LIKE '____-10%';
```
- Find any clients who are schools
``` sql
SELECT *
FROM client
WHERE client_name LIKE '%school%';
```
# Union

Operator used to combine multiple select statements into one
- Find a list of employee and branch name
``` sql
SELECT first_name AS Company_names
FROM employee
UNION
SELECT *
FROM branch_name
UNION
SELECT client_name
FROM client;
```
Rules:
- There must be the same number of columns
- Similar data type
- Output named after first element
``` sql
SELECT client_name, client.branch_id
FROM client
UNION
SELECT supplier_name, branch_supplier.branch_id
FROM branch_supplier;
```
- Find a list of all money spent or earned by the company 
``` sql
SELECT *salary
FROM employee
UNION
SELECT total_sales
FROM works_with;
```

# Joins

- Combine rows from two or more tables into a single result
``` sql
INSERT INTO branch VALUES(4, 'Buffalo', NULL, NULL);
```
- Find all branches and the names of their managers
``` sql
SElECT employee.emp_id, employee.first_name, branch.branch_name
FROM employee
JOIN branch 
-- LEFT JOIN includes all from left table (employee)
-- RIGHT JOIN -- includes all from right table (branch)
ON employee.emp_id = branch.mgr_id;
```

# Nested queries

- Used to select specific information
    - Find names of all employees who have sold over 30,000 to a single client
``` sql
SELECT employee.first_name, employee.last_name
FROM employee
WHERE employee.emp_id IN (
    SELECT works_with.emp_id
    FROM works_with
    WHERE works_with.total_sales > 30000
);
```
- Find all clients who are handled by the branch that Michael Scott manages Assume you know Michael's ID
``` sql
SELECT client.client_name
FROM client
WHERE client.branch_id = (
    SELECT branch.branch_id
    FROM branc h 
    WHERE branch.branch.mgr_id = 102
    LIMIT 1;
);
```

# On delete

- In entry gets deleted replace value with NULL
``` sql
CREATE TABLE branch (
    banch_id INT PRIMARY KEY,
    branch_name VARCHAR(40),
    mgr_id INT,
    mgr_start_date DATE,
    FOREIGN KEY(mgr_id) REFERENCES employee(emp_id) ON DELETE SET NULL
);

DELETE FROM employee
WHERE emp_id = 102;
```
- If the entry gets deleted, delete entire row. Primary keys can't be NULL, must be deleted completely
``` sql
CREATE TABLE branch_supplier ( 
    branch_id INT,
    supplier_name VARCHAR(40),
    supply_type VARCHAR(40),
    PRIMARY KEY(branch_id, supplier_name),
    FOREIGH KEY(branch_id) REFERENCES branch_id(branch_id) ON DELETE CASCADE
);

DELETE FROM branch
WHERE branch_id = 2;
```

# Triggers

A block of code that defines an action to happen when an operation is performed
``` sql
CREATE TABLE trigger_test(
    message VARCHAR(100)
)
```
On console:
``` console
sudo mysql -u root -p
```
``` sql
use database_name
DELIMITER $$
       CREATE
            TRIGGER my_trigger BEFORE INSERT
            ON employee
            FOR EACH ROW BEGIN
                INSERT INTO trigger_test VALUES('added new employee')
            END $$
DELIMITER;

INSERT INTO employee 
VALUE(109,'Oscar', 'Martinez', '1968-02-19','M',69000,106,3);
```
- Print Name when add entry
``` sql
use database_name
DELIMITER $$
       CREATE
            TRIGGER my_trigger BEFORE INSERT
            ON employee
            FOR EACH ROW BEGIN
                INSERT INTO trigger_test VALUES(NEW.first_name)
            END $$
DELIMITER;

INSERT INTO employee 
VALUE(110,'Kevin', 'Malone', '1978-02-19','M',69000,106,3);
```
- Trigger custom mesages depending on cases
``` sql
use database_name
DELIMITER $$
    CREATE
    TRIGGER my_trigger BEFORE INSERT -- INSERT, UPDATE or DELETE
    ON employee
    FOR EACH ROW BEGIN
        IF NEW.sex = 'M' THEN
            INSERT INTO trigger_test VALUES('added male employee');
        ELSEIF NEW.sex = 'F' THEN
            INSERT INTO trigger_test VALUES('added female');
        ELSE
            INSERT INTO trigger_test VALUES('added other employee');
        ENDIF
    END $$
DELIMITER ;

INSERT INTO employee 
VALUE(111,'Pam', 'Beesly', '1988-02-19','F',69000,106,3);
```
- Drop trigger
``` sql
DROP TRIGGER my_trigger;
```

# Entity Relationship (ER) Diagrams Intro
One of the most important things in database design is the databse schema.
- **Entity**: An object we want to model  store information about (STUDENT)
    - **Attributes**: Specific pieces of information about an entity (name, grade, gpa)
        - **Primary key**: An attribute that uniquely identifies an entry in the database table (student_id)
    - **Composite Attributes**: Can be broken up into sub-attributes (name:fname, lname) 
    - **Multi-valued attribute**: An attribute that can have more than one value (clubs)
    - **Derived attributes**:An attribute that can be derived from the other attributes (has honors: derived from gpa)
- **Multiple Entities**: You can define more than one entity in the diagram (Class:class_id)
- **Relationships**: Defines a relationship between two identities (student "takes" class)
    - **Partial participation**: Some members participate in the relationship (Some students take a class)
    - **Total participation**: All members must participate in the relationship (All students take a class)
    - **Relationship Attribute**: An attribute about the relationship (grade after taking class)
    - **Relationship cardinality**: Number of instances of an entity froma relation that can be associated with the relation( a student can take any number of classes)
- **Weak entity**: Cannot be uniquely identified by its attributes alone (Exam depends on class)
    - **Identifying relationship**: A relationship that serves to uniquely identify the weak entity, always has total participation in the identifying relationship (Class "has" exam)

# Exercise: Designing an ER diagram

## Company data requirements
- The company is organized into granches. Each branch has a unique number, a name, and a particular employee who panages it.
- The company makes it's money by selling to clients. Each client has a name and a unique number to identify
- The foundation of the company i it's employees. Each employee has a name, birthday, sex, salary and a unique number.
- An employee can work for one branch at a time, and each branch will be managed by one of the employees that work there. We'll also want to keep track of when the current manager started as manager.
- An employee can act as a supervisor for another employees at the branch, an employee may also act as the supervisor for employees at other branches. An employee can have at most one supervisor.
- A branch may handle a number if clients, with each having a name and a unique number to identify it. A single client may only be handled by one branch at a time.
- Employees can work with clients controlled by their branch to sell them stuff. If necessary multiple employees can work with the same client. We'll want to keep track of how many dollars worth of stuff each employee sells to each client they work with.
- Many branches will need to work with suppliers to buy inventory. For each supplier we'll keep track of their name and the type of product they're selling the branch. A single supplier may supply products to multiple branches.

# Converting ER diagram to schema
1. Mapping of regular entity types: For each regular entity type create a relation (table) that includes all the simple attribtes of that entity
2. Mapping of weak entity types: For each weak entity type create a relation (table) that includes all simple attributes of the weak entity.
3. Mapping of binary 1:1 relationship types: Include one side of the relationship as a foreign key in the other Favor total participation.
4. Mapping of binary 1:N relationship types: Include the 1 side's primary key as a foreign key on the N side relation (table)
5. Mappping of M:N relationship types: Create a new relation table who's primary key is a combination of both entities' primary keys. Also include any relationship attributes.

---
> From https://www.mikedane.com/
