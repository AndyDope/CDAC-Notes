## Normalization and DML

Welcome. In our last session, we learned how to design and create the basic structure of a database. Now, we address a critical aspect of design: **Normalization**. This is the process of organizing the columns and tables in a relational database to minimize data redundancy and prevent data anomalies. We will also dive into the most common SQL commands you will ever use: the **DML** commands for manipulating data.

---

### Data Redundancy and Data Anomalies
A poorly designed database often suffers from two major problems:

*   **Data Redundancy:** The same piece of information is stored multiple times. For example, storing a professor's name and department in every single course record they teach.
*   **Data Anomalies:** These are data integrity problems that occur due to redundancy.
    1.  **Insertion Anomaly:** You cannot add a new piece of data without adding some other unrelated data. For example, you can't add a new professor who hasn't been assigned a course yet if the professor's details are stored in the course table.
    2.  **Deletion Anomaly:** Deleting one piece of data unintentionally deletes another. For example, if you delete the last course taught by a professor, you might lose all information about that professor.
    3.  **Update Anomaly:** To update a single piece of information, you have to change it in multiple places. For example, if a professor changes their name, you would have to update it in every course record they teach.

**Normalization is the cure for these problems.**

### Functional Dependency
The concept of normalization is built on **functional dependency**.

A column `B` has a functional dependency on column `A` if, for each value of `A`, there is at most one value of `B`. We write this as `A -> B` ("A determines B").

*   **Example:** In a `Students` table, `Roll_No -> Student_Name`. For any given Roll Number, there is exactly one student name. The Roll Number determines the name.
*   **Non-example:** `Student_Name -> Roll_No`. This is not a functional dependency, as two students could have the same name ("John Smith").

### Normalization and Normal Forms
**Normalization** is the process of decomposing large, problematic tables into smaller, well-structured tables to reduce redundancy and eliminate anomalies. This is achieved by following a set of rules called **Normal Forms**.

#### First Normal Form (1NF)
*   **Rule:** Every column in a table must hold **atomic** (indivisible) values, and each row must be unique. A table must not have repeating groups or multi-valued columns.

**Example (Un-normalized):**

| Roll_No | Name | Phone_Numbers      |
| :------ | :--- | :----------------- |
| 101     | Ravi | "98...01, 99...02" |


This violates 1NF because `Phone_Numbers` is not atomic.

**Example (1NF Compliant):**
We create separate rows for each phone number.

| Roll_No | Name  | Phone_Number |
|:--------|:------|:-------------|
| 101     | Ravi  | "98...01"    |
| 101     | Ravi  | "99...02"    |

*This table is now in 1NF, but it has redundancy (Ravi's name is repeated) and can cause update anomalies.*

#### Second Normal Form (2NF)
*   **Prerequisite:** The table must be in 1NF.
*   **Rule:** There must be no **partial dependencies**. This means that every non-key attribute must be fully functionally dependent on the **entire primary key**.
*   This rule only applies to tables with a **composite primary key** (a primary key made of two or more columns).

**Example (Violates 2NF):**
Consider a table with a composite key `(StudentID, CourseID)`:
`{StudentID, CourseID} -> Grade` (Grade depends on both student and course)
`{StudentID} -> StudentName` (StudentName only depends on StudentID, a part of the key)

This is a partial dependency. `StudentName` should not be in this table.

**Example (2NF Compliant):**
Decompose into two tables:
1.  `Enrollments` Table: `(StudentID, CourseID, Grade)`
2.  `Students` Table: `(StudentID, StudentName)`

#### Third Normal Form (3NF)
*   **Prerequisite:** The table must be in 2NF.
*   **Rule:** There must be no **transitive dependencies**. A transitive dependency exists when a non-key attribute determines another non-key attribute. `A -> B` and `B -> C`, so transitively `A -> C`.

**Example (Violates 3NF):**
```c
+-----------+-------------+------+---------+
| StudentID | StudentName | City | Pincode |
+-----------+-------------+------+---------+
```
*   Here `StudentID` is the key. `StudentID -> Pincode`.
*   But `Pincode` also depends on `City` (`City -> Pincode`). `City` is not a key.
*   This is a transitive dependency: `StudentID -> City -> Pincode`.

**Example (3NF Compliant):**
Decompose into two tables:
1.  `Students` Table: `(StudentID, StudentName, City)`
2.  `Locations` Table: `(City, Pincode)`

#### Boyce-Codd Normal Form (BCNF)
*   BCNF is a stricter version of 3NF.
*   **Rule:** For every non-trivial functional dependency `X -> Y`, `X` must be a **superkey** (a set of attributes that uniquely identifies a row, which contains a candidate key).
*   *In simple terms:* Every determinant must be a candidate key. Most tables that are in 3NF are also in BCNF.

> **Quick Question:** You have a table `(OrderID, OrderDate, CustomerID, CustomerName)`. `OrderID` is the primary key. Which normal form is this table likely violating?
> **Answer:** 3NF. There is a transitive dependency: `OrderID -> CustomerID -> CustomerName`. `CustomerName` should be in a separate `Customers` table.

---

### DML (INSERT/UPDATE/DELETE)
[[DBT Session 2 - Database Design and DDL#Categories of SQL Commands|DML (Data Manipulation Language)]] commands are used to manage the data within the tables created by DDL.

#### INSERT
Used to add new rows (records) to a table.

**Syntax:**
```sql
INSERT INTO table_name (column1, column2, ...) VALUES (value1, value2, ...);
```

**Example:**
```sql
INSERT INTO Students (roll_no, name, city) VALUES (104, 'Sita', 'Delhi');
```
#### UPDATE
Used to modify existing records in a table. The `WHERE` clause is critical to specify *which* rows to update. **Forgetting the `WHERE` clause will update all rows in the table!**

**Syntax:**
```sql
UPDATE table_name SET column1 = value1, column2 = value2, ... WHERE condition;
```

**Example:**
```sql
UPDATE Students SET city = 'Chennai' WHERE roll_no = 104;
```
#### DELETE
Used to remove existing records from a table. The `WHERE` clause is critical here too. **Forgetting the `WHERE` clause will delete all rows in the table!**

**Syntax:**
```sql
DELETE FROM table_name WHERE condition;
```
**Example:**
```sql
DELETE FROM Students WHERE roll_no = 104;
```

> **Quick Question:** What is the critical difference between `DELETE FROM Students;` and `TRUNCATE TABLE Students;`?
> **Answer:** `DELETE` is a DML command that removes rows one by one and can be rolled back. `TRUNCATE` is a DDL command that deallocates the data pages, is much faster for large tables, and generally cannot be rolled back.

---

### Topic Summary & Revision

*   **Anomalies:** Poor database design leads to Insertion, Deletion, and Update anomalies caused by **data redundancy**.
*   **Normalization:** The process of organizing tables to reduce redundancy and improve data integrity by following Normal Forms.
*   **1NF:** All column values must be atomic (indivisible).
*   **2NF:** Must be in 1NF + No partial dependencies (all non-key attributes depend on the *whole* composite key).
*   **3NF:** Must be in 2NF + No transitive dependencies (a non-key attribute cannot determine another non-key attribute).
*   **DML Commands:**
    *   `INSERT`: Adds new rows.
    *   `UPDATE`: Modifies existing rows. **Always use `WHERE`!**
    *   `DELETE`: Removes existing rows. **Always use `WHERE`!**

---

### MCQs for Exam Preparation

1.  **If you cannot add a new course to a database until at least one student enrolls in it, this is an example of what?**
    - [ ] Update Anomaly
    - [ ] Deletion Anomaly
    - [ ] Insertion Anomaly
    - [ ] Data Redundancy
    <br>

2.  **A table is in 2NF. Which of the following must be true?**
    - [ ] All its attributes are atomic.
    - [ ] It has no transitive dependencies.
    - [ ] All non-key attributes are fully dependent on the primary key.
    - [ ] Both A and C.
    <br>

3.  **Which SQL statement is used to add a new employee record to the 'Employees' table?**
    - [ ] `UPDATE Employees ...`
    - [ ] `ADD Employees ...`
    - [ ] `CREATE Employees ...`
    - [ ] `INSERT INTO Employees ...`
    <br>

4.  **Consider the functional dependency `ISBN -> Title`. This means:**
    - [ ] For every book title, there is exactly one ISBN.
    - [ ] The ISBN and Title are interchangeable.
    - [ ] For every ISBN, there is exactly one book title.
    - [ ] The ISBN is determined by the title.
    <br>

5.  **A table `(BookID, AuthorID, AuthorNationality)` has `BookID` as the primary key. We know that `AuthorID -> AuthorNationality`. This table violates which normal form?**
    - [ ] 1NF
    - [ ] 2NF
    - [ ] 3NF
    - [ ] BCNF
    <br>

6.  **What is the likely outcome of running the command `UPDATE Employees SET salary = salary * 1.1;` without a `WHERE` clause?**
    - [ ] It will produce a syntax error.
    - [ ] It will give a 10% salary raise to the first employee in the table.
    - [ ] It will give a 10% salary raise to all employees in the table.
    - [ ] It will update the salary of the most recently added employee.
    - <br>

7.  **The primary motivation for normalizing a database is to:**
    - [ ] Increase query speed.
    - [ ] Minimize data redundancy.
    - [ ] Make the database schema simpler.
    - [ ] Reduce the number of tables.
    <br>

8.  **A table with a single-column primary key is already in 1NF. Which other normal form is it guaranteed to be in?**
    - [ ] 2NF
    - [ ] 3NF
    - [ ] BCNF
    - [ ] 4NF
    <br>

9.  **The `DELETE` command belongs to which category of SQL?**
    - [ ] DDL
    - [ ] DML
    - [ ] DCL
    - [ ] TCL
    <br>

10. **To achieve 1NF, a column containing a comma-separated list of phone numbers for a user should be:**
    - [ ] Converted to a `TEXT` data type.
    - [ ] Stored as is, since it's just a string.
    - [ ] Split into multiple columns like `phone1`, `phone2`.
    - [ ] Restructured into a separate `PhoneNumbers` table linked by `UserID`.
    <br>

**Answer Key**
1.  **C**: ||This is a classic insertion anomaly. The table structure improperly ties the existence of a course to the existence of an enrollment, preventing you from adding a course independently.||
2.  **D**: ||To be in 2NF, a table must first be in 1NF (atomic attributes). The rule for 2NF itself is that there are no partial dependencies, meaning all non-key attributes are dependent on the entire primary key.||
3.  **D**: ||The INSERT INTO command is the standard SQL statement for adding new rows of data to a table.||
4.  **C**: ||The arrow -> denotes "determines". ISBN -> Title means that if you know the ISBN, you can uniquely determine the book's title.||
5.  **C**: ||This is a transitive dependency. BookID -> AuthorID (a non-key attribute) and AuthorID -> AuthorNationality (another non-key attribute). A non-key attribute should not determine another non-key attribute. This data should be split into a Books table and an Authors table.||
6.  **C**: ||An UPDATE statement without a WHERE clause applies its action to every single row in the specified table. This is a very dangerous command if used unintentionally.||
7.  **B**: ||The entire process of normalization is designed to reduce or eliminate data redundancy, which in turn prevents insertion, update, and deletion anomalies. While it can sometimes impact query speed, that is not its primary goal.||
8.  **A**: ||The rules for 2NF relate to partial dependencies on composite primary keys. If a table's primary key is a single column, it cannot have any partial dependencies, so if it's in 1NF, it is automatically in 2NF.||
9.  **B**: ||DELETE is a Data Manipulation Language command because it manipulates (removes) data within the tables, rather than changing the table structure itself.||
10. **D**: ||While splitting into multiple columns (C) achieves atomicity, it's not scalable. The best relational design is to create a separate table for phone numbers where each phone number gets its own row, linked back to the user via a foreign key. This properly represents the one-to-many relationship.||

---

### **Bonus Tips**

*   **Normalization is a Trade-off:** While 3NF/BCNF is the ideal for data integrity, sometimes designers will **de-normalize** a database for performance. For example, in a reporting database, it might be faster to have a table with some redundant data than to perform complex joins across many normalized tables for every query. This is a deliberate design choice.
*   **Think in Keys:** The essence of normalization is identifying what determines what. Ask yourself, "What is the primary key of this table?" Then, for every other column, ask, "Does this column depend on the whole key (good), just a part of the key (bad, violates 2NF), or some other non-key column (bad, violates 3NF)?"
*   **The `WHERE` Clause is Your Safety Net:** In your lab work and professional career, develop a habit of writing the `WHERE` clause *first* for any `UPDATE` or `DELETE` statement. `UPDATE Employees WHERE emp_id = 101 SET ...`. This prevents you from accidentally running the statement without the condition and modifying your entire table.
*   **DML vs. DDL Logging:** A key difference is how the database logs these operations. DML operations like `DELETE` are logged row by row, which allows them to be part of a transaction and rolled back. DDL operations like `TRUNCATE` are often minimally logged (they just log that the data pages were deallocated), which is why they are faster but harder to undo.

**🔗Links:** [[DBT Session 5 - Constraints, Aggregate Functions, and Operators]]