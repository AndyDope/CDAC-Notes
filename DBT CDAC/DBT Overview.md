## Database Technologies Overview

This page provides a high-level summary of the essential concepts covered in the PG-DAC Database Technologies module. Use it as a quick-recall cheat sheet before exams.

---

### [[DBT Session 1 - Introduction to Database Technologies|Session 1: Introduction to Database Technologies]]
*   [[DBT Session 1 - Introduction to Database Technologies#Introduction to DBMS & Basic Database Terminology|DBMS]]: Software for creating, maintaining, and controlling access to a database.
*   [[DBT Session 1 - Introduction to Database Technologies#Basic Terminology|Schema]]: The logical blueprint or structure of a database.
*   [[DBT Session 1 - Introduction to Database Technologies#Types of DBMS|RDBMS vs. NoSQL]]: **RDBMS** uses structured tables (schema-on-write). **NoSQL** uses flexible models like documents (schema-on-read) for scalability.
*   [[DBT Session 1 - Introduction to Database Technologies#Introduction to MySQL & Clients|MySQL Clients]]: Tools like the command-line **Monitor/Shell** and the visual **Workbench** used to interact with the MySQL server.

---

### [[DBT Session 2 - Database Design and DDL|Session 2: Database Design and DDL]]
*   [[DBT Session 2 - Database Design and DDL#Data Models|Data Models]]: The design process flows from **Conceptual** (ideas) -> **Logical** (technical blueprint) -> **Physical** (DBMS-specific implementation).
*   [[DBT Session 2 - Database Design and DDL#Database Design and Entity-Relationship Diagram (ERD)|ERD]]: A visual diagram of entities, attributes, and relationships used in database design.
*   [[DBT Session 2 - Database Design and DDL#Categories of SQL Commands|SQL Categories]]: **DDL** (structure), **DML** (data), **DCL** (permissions), **TCL** (transactions).
*   [[DBT Session 2 - Database Design and DDL#DDL (CREATE/ALTER/DROP/TRUNCATE) in Detail|DDL Commands]]: `CREATE` (build), `ALTER` (modify), `DROP` (delete object), `TRUNCATE` (delete all data).

---

### [[DBT Sessions 3 & 4 - Normalization and DML|Sessions 3 & 4: Normalization and DML]]
*   [[DBT Sessions 3 & 4 - Normalization and DML#Data Redundancy and Data Anomalies|Data Anomalies]]: Issues like Insertion, Deletion, and Update anomalies caused by data redundancy.
*   [[DBT Sessions 3 & 4 - Normalization and DML#Normalization and Normal Forms|Normalization]]: The process of organizing tables to reduce redundancy.
    *   [[DBT Sessions 3 & 4 - Normalization and DML#First Normal Form (1NF)|1NF]]: All column values are atomic (indivisible).
    *   [[DBT Sessions 3 & 4 - Normalization and DML#Second Normal Form (2NF)|2NF]]: In 1NF + no partial dependencies.
    *   [[DBT Sessions 3 & 4 - Normalization and DML#Third Normal Form (3NF)|3NF]]: In 2NF + no transitive dependencies.
*   [[DBT Sessions 3 & 4 - Normalization and DML#DML (INSERT/UPDATE/DELETE)|DML Commands]]: `INSERT` (add rows), `UPDATE` (modify rows), `DELETE` (remove rows). Always use a `WHERE` clause with `UPDATE` and `DELETE`.

---

### [[DBT Session 5 - Constraints, Aggregate Functions, and Operators|Session 5: Constraints, Aggregate Functions, and Operators]]
*   [[DBT Session 5 - Constraints, Aggregate Functions, and Operators#Database Constraints|Constraints]]: Rules to ensure data integrity. `PRIMARY KEY` (unique identifier) and `FOREIGN KEY` (links tables) are crucial.
*   [[DBT Session 5 - Constraints, Aggregate Functions, and Operators#Aggregate Functions and Grouping (`GROUP BY`, `HAVING`)|Aggregate Functions]]: `COUNT`, `SUM`, `AVG`, `MAX`, `MIN` are used to summarize data.
*   [[DBT Session 5 - Constraints, Aggregate Functions, and Operators#GROUP BY|`GROUP BY`]]: Groups rows to apply aggregate functions to each group.
*   [[DBT Session 5 - Constraints, Aggregate Functions, and Operators#HAVING|`HAVING` vs. `WHERE`]]: `WHERE` filters rows before grouping; `HAVING` filters groups after aggregation.

---

### [[DBT Session 6 - Relational Algebra and Joins|Session 6: Relational Algebra and Joins]]
*   [[DBT Session 6 - Relational Algebra and Joins#Relational Algebra Operations|Relational Algebra]]: The theoretical foundation for SQL queries, including Selection (σ) and Projection (π).
*   [[DBT Session 6 - Relational Algebra and Joins#Joins|Joins]]: Combine rows from multiple tables based on a related column.
    *   [[DBT Session 6 - Relational Algebra and Joins#Inner Join|`INNER JOIN`]]: Returns only matching rows from both tables.
    *   [[DBT Session 6 - Relational Algebra and Joins#Outer Joins|`LEFT JOIN`]]: Returns all rows from the left table, and matched rows from the right.
    *   [[DBT Session 6 - Relational Algebra and Joins#Outer Joins|`RIGHT JOIN`]]: Returns all rows from the right table, and matched rows from the left.
*   [[DBT Session 6 - Relational Algebra and Joins#Other Useful Concepts|`AUTO_INCREMENT`]]: Automatically generates unique integer values for a column, typically a primary key.

---

### [[DBT Session 7 - Subqueries, Views, and Transaction Control|Session 7: Subqueries, Views, and Transaction Control]]
*   [[DBT Session 7 - Subqueries, Views, and Transaction Control#Subqueries (Nested or Inner Queries)|Subquery]]: A query nested inside another query.
*   [[DBT Session 7 - Subqueries, Views, and Transaction Control#Correlated Subqueries|Correlated Subquery]]: An inner query that depends on the current row of the outer query.
*   [[DBT Session 7 - Subqueries, Views, and Transaction Control#Views|View]]: A stored query that acts as a secure, simplified virtual table.
*   [[DBT Session 7 - Subqueries, Views, and Transaction Control#TCL (Transaction Control Language)|TCL]]: `COMMIT` saves a transaction; `ROLLBACK` undoes it.
*   [[DBT Session 7 - Subqueries, Views, and Transaction Control#DCL (Data Control Language)|DCL]]: `GRANT` gives permissions; `REVOKE` removes them.

---

### [[DBT Session 8 - Indexes, ACID Properties, and Storage Engines|Session 8: Indexes, ACID Properties, and Storage Engines]]
*   [[DBT Session 8 - Indexes, ACID Properties, and Storage Engines#Indexes|Index]]: A data structure that speeds up `SELECT` queries but slows down `INSERT`/`UPDATE`/`DELETE` operations.
*   [[DBT Session 8 - Indexes, ACID Properties, and Storage Engines#ACID Properties|ACID Properties]]: Guarantees for reliable transactions: **A**tomicity, **C**onsistency, **I**solation, **D**urability.
*   [[DBT Session 8 - Indexes, ACID Properties, and Storage Engines#MySQL Storage Engines|Storage Engines]]: The backend component that handles data storage.
    *   [[DBT Session 8 - Indexes, ACID Properties, and Storage Engines#InnoDB|`InnoDB`]]: Default, transactional (ACID), row-level locking, supports foreign keys.
    *   [[DBT Session 8 - Indexes, ACID Properties, and Storage Engines#MyISAM|`MyISAM`]]: Older, non-transactional, table-level locking.

---

### [[DBT Session 9 - MySQL Programming and Stored Procedures|Session 9: MySQL Programming and Stored Procedures]]
*   [[DBT Session 9 - MySQL Programming and Stored Procedures#Introduction to Stored Procedures|Stored Procedure]]: A reusable block of pre-compiled SQL statements stored in the database, executed with `CALL`.
*   [[DBT Session 9 - MySQL Programming and Stored Procedures#Procedure Parameters|Parameters]]:
    *   `IN`: Passes a value into the procedure.
    *   `OUT`: Returns a value from the procedure.
    *   `INOUT`: Passes a value in, which can be modified and returned.

---

### [[DBT Session 10 - Flow Control in Stored Procedures|Session 10: Flow Control in Stored Procedures]]
*   [[DBT Session 10 - Flow Control in Stored Procedures#Conditional Statements|Conditionals]]: Use `IF-THEN-ELSEIF-ELSE-END IF` for branching logic. `CASE` is a cleaner alternative for checking a variable against multiple values.
*   [[DBT Session 10 - Flow Control in Stored Procedures#Flow Control Statements (Loops)|Loops]]: `LOOP`, `WHILE`, and `REPEAT` are used for iteration.

---

### [[DBT Session 11 - Functions and Loop Constructs|Session 11: Functions and Loop Constructs]]
*   [[DBT Session 11 - Functions and Loop Constructs#Advanced Loop Constructs (`ITERATE`, `LEAVE`)|`LEAVE` & `ITERATE`]]: `LEAVE` is like `break` (exits a loop). `ITERATE` is like `continue` (skips to the next iteration).
*   [[DBT Session 11 - Functions and Loop Constructs#Stored Functions|Stored Function]]: A stored program that **must return a single value** and can be used directly in SQL queries.
*   [[DBT Session 11 - Functions and Loop Constructs#MySQL Built-in Functions|Built-in Functions]]: Pre-defined functions for `string`, `numeric`, and `date` manipulations.

---

### [[DBT Session 12 - Cursors|Session 12: Cursors]]
*   [[DBT Session 12 - Cursors#What is a Cursor and Why Use It?|Cursor]]: A database object for row-by-row processing of a result set. Generally inefficient and should be a last resort.
*   [[DBT Session 12 - Cursors#The Lifecycle of a Cursor|Cursor Lifecycle]]: A four-step process: **`DECLARE`** the cursor, **`OPEN`** it, **`FETCH`** from it in a loop, and **`CLOSE`** it.
*   [[DBT Session 12 - Cursors#Using Cursors in a Stored Procedure|Handler]]: A `DECLARE HANDLER FOR NOT FOUND` is essential to gracefully exit the fetch loop.

---

### [[DBT Session 13 - Triggers|Session 13: Triggers]]
*   [[DBT Session 13 - Triggers#Introduction to Triggers|Trigger]]: A stored program that executes **automatically** in response to an `INSERT`, `UPDATE`, or `DELETE` event.
*   [[DBT Session 13 - Triggers#Introduction to Triggers|`BEFORE` vs. `AFTER`]]: `BEFORE` triggers are for validation and modifying incoming data. `AFTER` triggers are for logging and auditing.
*   [[DBT Session 13 - Triggers#`NEW` and `OLD` Trigger Variables|`NEW` & `OLD`]]: Pseudo-rows to access the data being changed. `NEW` is available for `INSERT`/`UPDATE`. `OLD` is available for `UPDATE`/`DELETE`.

---

### [[DBT Session 14 - Error Handling in Stored Procedures|Session 14: Error Handling in Stored Procedures]]
*   [[DBT Session 14 - Error Handling in Stored Procedures#How to Write a Handler|`DECLARE HANDLER`]]: Defines a block of code to execute when a specific error (like `SQLEXCEPTION`) or condition (like `NOT FOUND`) occurs.
*   [[DBT Session 14 - Error Handling in Stored Procedures#Types of Handler Actions|Handler Actions]]: **`CONTINUE`** resumes execution after the error line. **`EXIT`** terminates the `BEGIN...END` block.

---

### [[DBT Session 15 - NoSQL Database|Session 15: NoSQL Database]]
*   [[DBT Session 15 - NoSQL Database#What is NoSQL?|NoSQL]]: "Not Only SQL". A category of databases designed for scalability and flexibility, often using a flexible schema.
*   [[DBT Session 15 - NoSQL Database#The CAP Theorem|CAP Theorem]]: A distributed system must choose between **Consistency** and **Availability** when faced with a network **Partition**.
*   [[DBT Session 15 - NoSQL Database#The BASE Model|BASE]]: **B**asically **A**vailable, **S**oft State, **E**ventual Consistency. An alternative to ACID favored by many NoSQL systems.
*   [[DBT Session 15 - NoSQL Database#Categories of NoSQL Databases|NoSQL Types]]: Key-Value, Document, Column-Oriented, Graph.

---

### [[DBT Sessions 16, 17, 18 - MongoDB|Sessions 16-18: MongoDB]]
*   [[DBT Sessions 16, 17, 18 - MongoDB#Introduction to MongoDB|MongoDB]]: A leading document-oriented database that stores data in flexible, JSON-like **BSON** documents.
*   [[DBT Sessions 16, 17, 18 - MongoDB#RDBMS & MongoDB Analogies|Terminology]]: Database -> Database, Table -> **Collection**, Row -> **Document**, Column -> **Field**, Primary Key -> **_id**.
*   [[DBT Sessions 16, 17, 18 - MongoDB#Performing CRUD Operations|CRUD Operations]]:
    *   Create: `insertOne()`, `insertMany()`
    *   Read: `find()`, `findOne()`
    *   Update: `updateOne()`, `updateMany()` (using operators like `$set`, `$inc`)
    *   Delete: `deleteOne()`, `deleteMany()`
*   [[DBT Sessions 16, 17, 18 - MongoDB#UPSERT|Upsert]]: An update option (`{ upsert: true }`) that inserts a new document if no match is found for the update filter.

---

🔗 **[[DBT MCQs|All MCQs]]**