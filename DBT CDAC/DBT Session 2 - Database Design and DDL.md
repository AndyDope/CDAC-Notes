## Database Design and DDL

Welcome to Session 2. Now that we understand what a database is, we need to learn how to design one. A well-designed database is efficient, reliable, and easy to maintain. A poorly designed one leads to data redundancy, inconsistency, and performance problems. This session focuses on the design process and the SQL commands used to create the database structure.

---

### Data Models
A **data model** is a high-level design that describes the structure of a database, including its entities, attributes, and the relationships between them. It acts as a blueprint before we start building. We typically progress through three stages of data modeling.

#### Conceptual Data Model
*   **What it is:** The highest-level, most abstract view. It focuses on identifying the main entities (the "things" we want to store data about) and the relationships between them.
*   **Purpose:** To understand the business requirements and communicate the design to non-technical stakeholders. It answers the question, "What data does the system need?"
*   **How it's represented:** Often as a simple sketch or a high-level **Entity-Relationship Diagram (ERD)**. Details like data types and keys are omitted.

#### Logical Data Model
*   **What it is:** A more detailed model that translates the conceptual model into a formal structure, usually the relational model. It defines the tables, columns (with their data types), and the relationships using primary and foreign keys.
*   **Purpose:** To provide a detailed technical blueprint for developers and DBAs. It is independent of any specific DBMS (e.g., MySQL, Oracle). It answers the question, "How will the data be structured?"
*   **How it's represented:** A detailed ERD with attributes, data types, and key specifications.

#### Physical Data Model
*   **What it is:** The most detailed model, specifying how the logical model will be physically implemented in a specific DBMS.
*   **Purpose:** To define the actual database implementation. It includes DBMS-specific details like storage engines, indexing strategies, and data type names (e.g., `VARCHAR` in MySQL vs. `NVARCHAR2` in Oracle).
*   **How it's represented:** The final database schema and the `CREATE TABLE` scripts.

**Visualizing the Modeling Process:**

```c
+-----------------+      +-----------------+      +-----------------+
| Conceptual Model| ---> |  Logical Model  | ---> | Physical Model  |
| (What we need)  |      | (How to struct) |      | (How to build)  |
|-----------------|      |-----------------|      |-----------------|
| - Entities      |      | - Tables        |      | - Table Scripts |
| - Relationships |      | - Columns/Types |      | - Indexes       |
|                 |      | - Keys (PK/FK)  |      | - Storage Engine|
+-----------------+      +-----------------+      +-----------------+
```

> **Quick Question:** At which stage of data modeling would you decide on using `INT` for a student's roll number and `VARCHAR(50)` for their name?
> **Answer:** The Logical Data Model, as this is where specific attributes and their data types are defined.

---

### Database Design and Entity-Relationship Diagram (ERD)
Database design is often done using an **Entity-Relationship Diagram (ERD)**. An ERD is a visual representation of the entities in our system and the relationships between them.

*   **Entity:** A real-world object or concept about which we want to store data (e.g., `Student`, `Course`). Represented by a **rectangle**.
*   **Attribute:** A property of an entity (e.g., `student_name`, `course_title`). Represented by an **oval**.
*   **Relationship:** An association between two or more entities (e.g., a `Student` *enrolls in* a `Course`). Represented by a **diamond**.

**Visualizing a Simple ERD:**

```c
+-----------+        +----------+        +----------+
|  Student  |--(N)---| Enrolls  |---(M)--|  Course  |
+-----------+        +----------+        +----------+
     |                    |                    |
  (Attributes)         (Relationship)       (Attributes)
  - RollNo (PK)                            - CourseID (PK)
  - Name                                   - Title
```
This diagram shows a "Many-to-Many" relationship: one student can enroll in many courses, and one course can have many students.

---

### Codd's 12 Rules for RDBMS
Dr. E.F. Codd, the father of the relational model, proposed a set of 12 rules (numbered 0 to 12) that a DBMS must adhere to in order to be considered truly "relational." We don't need to memorize all of them, but understanding the core idea is important.

**Core Idea:** The rules enforce that the entire database should be manageable purely through its relational capabilities. All data must be represented as values in tables, and the system must support a powerful language (like SQL) to manipulate this data in a consistent way, independent of its physical storage. A key rule is that `NULL` values must be handled consistently as "missing information," not as zero or an empty string.

---

### Introduction to SQL
**SQL (Structured Query Language)** is the standard language used to communicate with a relational database. It's a declarative language—you describe *what* you want, and the DBMS figures out *how* to get it.

#### Categories of SQL Commands

SQL commands are grouped into categories based on their function.

*   **DDL (Data Definition Language):** Defines or modifies the database structure.
    *   **Keywords:** `CREATE`, `ALTER`, `DROP`, `TRUNCATE`.

*   **DML (Data Manipulation Language):** Manipulates the data within the tables.
    *   **Keywords:** `INSERT`, `UPDATE`, `DELETE`.

*   **DCL (Data Control Language):** Manages user access and permissions.
    *   **Keywords:** `GRANT`, `REVOKE`.

*   **TCL (Transaction Control Language) / DTL:** Manages transactions to ensure data integrity.
    *   **Keywords:** `COMMIT`, `ROLLBACK`, `SAVEPOINT`.

> **Quick Question:** You need to add a new column named `email` to an existing `Students` table. Which category of SQL command would you use?
> **Answer:** DDL (Data Definition Language), specifically the `ALTER` command.

---

### DDL (CREATE/ALTER/DROP/TRUNCATE) in Detail

#### CREATE
Used to create new database objects like databases and tables.

**Syntax (Create Table):**
```sql
CREATE TABLE table_name (
    column1_name data_type [constraints],
    column2_name data_type [constraints],
    ...
);
```
**Example:**
```sql
CREATE TABLE Students (
    roll_no INT PRIMARY KEY,
    name VARCHAR(100) NOT NULL,
    city VARCHAR(50)
);
```

#### ALTER
Used to modify the structure of an existing database object. You can add, delete, or modify columns in a table.

**Example (Add a column):**
`ALTER TABLE Students ADD COLUMN email VARCHAR(100);`

**Example (Modify a column):**
`ALTER TABLE Students MODIFY COLUMN city VARCHAR(75);`

**Example (Drop a column):**
`ALTER TABLE Students DROP COLUMN city;`

#### DROP
Used to permanently delete an entire database object (like a table or a database). This is irreversible.
`DROP TABLE Students;`

#### TRUNCATE
Used to quickly delete all rows from a table, but the table structure itself remains. It is much faster than `DELETE` for emptying a large table because it deallocates the data pages without logging each row deletion.
`TRUNCATE TABLE Students;`

**`DROP` vs. `TRUNCATE` vs. `DELETE` (Important Distinction)**
*   **`DROP TABLE`**: Deletes the table structure and all its data. The table no longer exists.
*   **`TRUNCATE TABLE`**: Deletes all data from the table but keeps the empty table structure. It is a DDL command and cannot be rolled back easily.
*   **`DELETE FROM table`**: Deletes rows from a table (can be all or specific rows using a `WHERE` clause). It is a DML command, is slower, and can be rolled back as part of a transaction.

---

## Topic Summary & Revision

*   **Data Models:** The design process moves from **Conceptual** (high-level ideas) -> **Logical** (technical blueprint with tables/keys) -> **Physical** (DBMS-specific implementation).
*   **ERD:** A visual tool using **Entities** (rectangles), **Attributes** (ovals), and **Relationships** (diamonds) to design a database.
*   **SQL Categories:** **DDL** (structure), **DML** (data), **DCL** (permissions), **TCL** (transactions).
*   **DDL Commands:**
    *   `CREATE`: To build new objects.
    *   `ALTER`: To modify the structure of existing objects.
    *   `DROP`: To permanently delete an object (structure and data).
    *   `TRUNCATE`: To quickly delete all data from a table (structure remains).

---

## MCQs for Exam Preparation

1.  **Which SQL command category is used to manage user permissions to a database?**
    - [ ] DDL
    - [ ] DML
    - [ ] DCL
    - [ ] TCL
    <br>

2.  **Which statement best describes a Conceptual Data Model?**
    - [ ] It details the specific data types and indexes to be used in MySQL.
    - [ ] It provides the `CREATE TABLE` scripts for the database.
    - [ ] It is a high-level view focusing on the main entities and their relationships, intended for stakeholders.
    - [ ] It defines the primary and foreign keys for all tables.
    <br>

3.  **What is the primary difference between the `DROP TABLE` and `TRUNCATE TABLE` commands?**
    - [ ] `DROP` removes all data, while `TRUNCATE` only removes some data.
    - [ ] `TRUNCATE` is a DML command, while `DROP` is a DDL command.
    - [ ] `DROP` deletes the table structure itself, while `TRUNCATE` leaves the empty table structure intact.
    - [ ] `TRUNCATE` can be easily rolled back, while `DROP` cannot.
    <br>

4.  **In an Entity-Relationship Diagram (ERD), what shape is typically used to represent an entity?**
    - [ ] Diamond
    - [ ] Oval
    - [ ] Circle
    - [ ] Rectangle
    <br>

5.  **A developer needs to change the data type of an existing `price` column in a `Products` table from `INT` to `DECIMAL(10, 2)`. Which command should be used?**
    - [ ] `CREATE TABLE Products ...`
    - [ ] `UPDATE Products SET price ...`
    - [ ] `ALTER TABLE Products MODIFY COLUMN ...`
    - [ ] `TRUNCATE TABLE Products ...`
    <br>

6.  **The commands `COMMIT` and `ROLLBACK` belong to which category of SQL?**
    - [ ] DDL
    - [ ] DML
    - [ ] DCL
    - [ ] TCL
    <br>

7.  **Which of the following is NOT a DDL command?**
    - [ ] `CREATE`
    - [ ] `ALTER`
    - [ ] `UPDATE`
    - [ ] `DROP`
    <br>

8.  **During which phase of data modeling do you consider DBMS-specific features like `InnoDB` or `MyISAM` storage engines?**
    - [ ] Conceptual Model
    - [ ] Logical Model
    - [ ] Physical Model
    - [ ] All of the above
    <br>

9.  **According to Codd's rules, a key goal of a relational database is to ensure that data is accessed and manipulated by what means?**
    - [ ] Through direct physical file access.
    - [ ] Based on its values in tables, not by its physical location or pointers.
    - [ ] Only through a graphical user interface.
    - [ ] Using object-oriented programming methods.
    <br>

10. **What is the result of the `TRUNCATE TABLE Employees;` command?**
    - [ ] The `Employees` table is deleted from the database.
    - [ ] All data is removed from the `Employees` table, and the operation is logged for rollback.
    - [ ] All data is quickly removed from the `Employees` table, but the table definition remains.
    - [ ] Only the first row of the `Employees` table is removed.
    <br>

**Answer Key**
1.  **C**: ||DCL (Data Control Language) includes GRANT and REVOKE, which are used to manage user privileges.||
2.  **C**: ||The Conceptual model is the initial, big-picture view that captures business requirements without getting into technical details like data types or keys.||
3.  **C**: ||DROP removes the entire object, including its definition. TRUNCATE only empties the object, leaving the structure for future use.||
4.  **D**: ||In standard ERD notation, rectangles represent entities (like Student, Product), ovals represent their attributes (like name, price), and diamonds represent the relationship between entities (like "buys" or "enrolls in").||
5.  **C**: ||ALTER TABLE is the DDL command used to modify the structure of an existing table. The MODIFY COLUMN clause is used to change a column's definition. UPDATE is a DML command used to change data, not structure.||
6.  **D**: ||TCL (Transaction Control Language) commands are used to manage transactions. COMMIT saves a transaction, and ROLLBACK undoes it.||
7.  **C**: ||UPDATE is a DML (Data Manipulation Language) command used to change existing data within rows. The others are DDL commands used to define or destroy the data structure.||
8.  **C**: ||The Physical Model is where the abstract logical design is translated into a concrete implementation for a specific DBMS, including choices like storage engines and indexing strategies.||
9.  **B**: ||A core tenet of the relational model is data independence. Users should interact with data based on its logical value (e.g., "find the student where roll_no = 101"), not by its physical position on a disk.||
10. **C**: ||TRUNCATE is a high-performance DDL operation for deleting all records from a table. The table itself is not deleted, but the data is gone and the operation is typically not transaction-safe in the same way DELETE is.||

---

## **Bonus Tips**

*   **Design First, Code Later:** Just like with [[DS Session 1 - Problem Solving & Computational Thinking|software development]], the most critical work in database management happens at the design stage. A good ERD and logical model will save you from immense pain and restructuring later. Never start by just writing `CREATE TABLE` statements without a plan.
*   **Choosing Data Types:** When in the logical/physical design phase, choose the most appropriate and smallest data type that can hold your data. Don't use a `BIGINT` for a person's age or a `VARCHAR(255)` for a 2-letter country code. This saves space and improves performance.
*   **`TRUNCATE` is Powerful but Dangerous:** Because `TRUNCATE` is a DDL command and often minimally logged, it's incredibly fast for clearing out large tables (e.g., temporary log tables). However, it cannot be easily undone within a transaction like a `DELETE` command can. Use it with caution.
*   **The Power of Declarative Language:** SQL is declarative. You specify *what* data you want, not *how* to get it. `SELECT name FROM Students WHERE city = 'Pune';` doesn't tell the database to loop through every student. It describes the desired result set, and the DBMS's query optimizer finds the most efficient physical plan to retrieve that data (e.g., by using an index on the `city` column).

**🔗Links:** [[DBT Sessions 3 & 4 - Normalization and DML]]