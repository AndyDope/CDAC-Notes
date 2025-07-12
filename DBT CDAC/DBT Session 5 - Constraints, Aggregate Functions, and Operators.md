## Constraints, Aggregate Functions, and Operators

Welcome to Session 5. Now that we know how to create tables and insert data, we need to learn how to enforce data integrity and how to perform calculations and retrieve specific data from our tables. This session covers **Constraints** (rules for our data), **Aggregate Functions** (for summarizing data), and various **Operators** used in the `WHERE` clause to filter data.

---

### MySQL Data Types
Before creating tables, you must choose a data type for each column. This tells the database what kind of data to expect and how to store it.

*   **Numeric Types:**
    *   `INT` or `INTEGER`: For whole numbers.
    *   `DECIMAL(p, s)`: For fixed-point numbers with exact precision, ideal for monetary values. `p` is the total number of digits, and `s` is the number of digits after the decimal point (e.g., `DECIMAL(10, 2)`).
    *   `FLOAT`, `DOUBLE`: For floating-point (approximate value) numbers.
*   **String Types:**
    *   `CHAR(size)`: Fixed-length string. If you store 'hi' in a `CHAR(10)`, it uses all 10 characters of space. Good for data of a known, fixed length like country codes ('US').
    *   `VARCHAR(size)`: Variable-length string. If you store 'hi' in a `VARCHAR(10)`, it only uses space for 'hi' plus a little overhead. This is the most common string type.
    *   `TEXT`: For long-form text data like articles or descriptions.
*   **Date and Time Types:**
    *   `DATE`: Stores a date (YYYY-MM-DD).
    *   `TIME`: Stores a time (HH:MM:SS).
    *   `DATETIME` or `TIMESTAMP`: Stores both date and time. `TIMESTAMP` is often used for tracking when a row was created or modified.

### Database Constraints
Constraints are rules enforced on data columns in a table. They are used to ensure the accuracy, reliability, and integrity of the data. They prevent invalid data from being entered.

*   **`NOT NULL`**: Ensures that a column cannot have a `NULL` (empty) value.
*   **`UNIQUE`**: Ensures that all values in a column are different.
*   **`PRIMARY KEY` (PK)**: A combination of `NOT NULL` and `UNIQUE`. It uniquely identifies each record in a table. A table can have only one Primary Key.
*   **`FOREIGN KEY` (FK)**: A key used to link two tables together. It is a field (or collection of fields) in one table that refers to the `PRIMARY KEY` in another table. This enforces **referential integrity**.
*   **`DEFAULT`**: Provides a default value for a column when no value is specified.
*   **`CHECK`**: Ensures that all values in a column satisfy a specific condition. (Note: MySQL historically parsed this but didn't enforce it until version 8.0.16).

**Visualizing Primary & Foreign Keys:**
This is the mechanism that builds relationships in an RDBMS.

```c
    Students Table                                 Courses Table
+-----------+--------+--------------+        +--------------+---------+
| Roll_No(PK)| Name   | CourseID(FK)|        | CourseID(PK) |  Title  |
+-----------+--------+--------------+        +--------------+---------+
| 101       | Ravi   |      C10     | -----> |     C10      |  Java   |
+-----------+--------+--------------+        +--------------+---------+
| 102       | Priya  |      C20     | --+--> |     C20      | Python  |
+-----------+--------+--------------+   |    +--------------+---------+
| 103       | Amit   |      C10     | --+
+-----------+--------+--------------+
```
Here, the `CourseID` in the `Students` table is a Foreign Key that references the `CourseID` Primary Key in the `Courses` table. This ensures you cannot enter a `CourseID` for a student that does not exist in the `Courses` table.

> **Quick Question:** You want to ensure that every employee in your `Employees` table has a unique `EmployeeID` and that this field can never be empty. Which single constraint achieves both of these goals?
> **Answer:** The `PRIMARY KEY` constraint.

---

### Aggregate Functions and Grouping (`GROUP BY`, `HAVING`)
Aggregate functions perform a calculation on a set of values and return a single summary value.

*   `COUNT()`: Counts the number of rows.
*   `SUM()`: Calculates the sum of a numeric column.
*   `AVG()`: Calculates the average of a numeric column.
*   `MAX()`: Returns the maximum value in a column.
*   `MIN()`: Returns the minimum value in a column.

#### GROUP BY
The `GROUP BY` clause is used with aggregate functions to group rows that have the same values in specified columns into summary rows.

**Example: Find the number of students in each city.**
Using the `Students` table from [[DBT Session 1 - Introduction to Database Technologies#Visualizing a Students Table|Session 1]]:
```sql
SELECT city, COUNT(roll_no)
FROM Students
GROUP BY city;
```
**Execution Flow & Visualization:**
1.  **FROM:** The query starts with the `Students` table.
2.  **GROUP BY:** It groups the rows based on the `city` column.
    *   Group 1: { (101, Ravi, Pune), (103, Amit, Pune) }
    *   Group 2: { (102, Priya, Mumbai) }
3.  **SELECT:** The aggregate function `COUNT()` is now applied to each group.
    *   For the 'Pune' group, `COUNT()` is 2.
    *   For the 'Mumbai' group, `COUNT()` is 1.

**Result:**

| city   | COUNT(roll_no) |
|:-------|:---------------|
| Pune   | 2              |
| Mumbai | 1              |

#### HAVING
The `HAVING` clause was added to SQL because the `WHERE` keyword cannot be used with aggregate functions. `HAVING` is used to filter the *results* of a `GROUP BY` clause.

*   `WHERE` filters rows *before* they are grouped.
*   `HAVING` filters groups *after* they have been created.

**Example: Find the cities that have more than one student.**
```sql
SELECT city, COUNT(roll_no)
FROM Students
GROUP BY city
HAVING COUNT(roll_no) > 1;
```
**Result:**

| city | COUNT(roll_no) |
| :--- | :------------- |
| Pune | 2              |

> **Quick Question:** You want to find the average salary of employees in each department, but only for departments where the maximum salary is over 90,000. Which clause would you use to filter by the maximum salary?
> **Answer:** The `HAVING` clause, because `MAX(salary)` is an aggregate function. The query would be `... GROUP BY department HAVING MAX(salary) > 90000;`.

---

### Other Important Operators & Clauses

*   **`ORDER BY`**: Sorts the result set in ascending (`ASC`) or descending (`DESC`) order.
    `SELECT name, city FROM Students ORDER BY name ASC;`

*   **`DISTINCT`**: Returns only distinct (different) values.
    `SELECT DISTINCT city FROM Students;`  -- Returns 'Pune', 'Mumbai'

*   **`LIKE` Operator**: Used in a `WHERE` clause to search for a specified pattern in a column.
    *   `%`: Represents zero, one, or multiple characters.
    *   `_`: Represents a single character.
    `SELECT name FROM Students WHERE name LIKE 'A%';` -- Finds names starting with 'A'.

*   **`BETWEEN...AND`**: Selects values within a given range. It is inclusive.
    `SELECT * FROM Products WHERE price BETWEEN 100 AND 500;`

*   **`IN / NOT IN`**: Specifies multiple possible values for a column.
    `SELECT * FROM Students WHERE city IN ('Pune', 'Delhi');`

*   **Comparing Nulls**: `NULL` represents a missing or unknown value. You cannot use standard comparison operators like `=` or `!=` with `NULL`. You must use `IS NULL` or `IS NOT NULL`.
    `SELECT name FROM Students WHERE email IS NULL;`

---

### Topic Summary & Revision

*   **Constraints:** Rules to ensure data integrity. Key constraints are `PRIMARY KEY` (unique, not null identifier) and `FOREIGN KEY` (links to another table's PK).
*   **Aggregate Functions:** `COUNT`, `SUM`, `AVG`, `MAX`, `MIN` summarize data.
*   **`GROUP BY`:** Groups rows to allow aggregate functions to operate on each group.
*   **`HAVING` vs. `WHERE`:** `WHERE` filters rows before grouping. `HAVING` filters groups after aggregation.
*   **Common Clauses:** `ORDER BY` (sorting), `DISTINCT` (unique values).
*   **Operators:** `LIKE` (pattern matching), `BETWEEN` (ranges), `IN` (multiple values), `IS NULL` (handling nulls).

---

### MCQs for Exam Preparation

1.  **Which constraint combines the properties of `UNIQUE` and `NOT NULL`?**
    - [ ] `FOREIGN KEY`
    - [ ] `CHECK`
    - [ ] `PRIMARY KEY`
    - [ ] `DEFAULT`
    <br>

2.  **To get a list of all unique cities where your customers live, which query would you use?**
    - [ ] `SELECT city FROM Customers GROUP BY city;`
    - [ ] `SELECT city FROM Customers;`
    - [ ] `SELECT UNIQUE city FROM Customers;`
    - [ ] `SELECT DISTINCT city FROM Customers;`
    <br>

3.  **A query needs to find all departments where the average salary is greater than 50,000. Which clause should be used for the condition `AVG(salary) > 50000`?**
    - [ ] `WHERE`
    - [ ] `HAVING`
    - [ ] `GROUP BY`
    - [ ] `LIKE`
    <br>

4.  **Which `LIKE` pattern would find all names that have 'a' as the second letter and are at least three letters long?**
    - [ ] `LIKE 'a_%'`
    - [ ] `LIKE '_a%'`
    - [ ] `LIKE '%a_'`
    - [ ] `LIKE '_a_'`
    <br>

5.  **What is the purpose of a `FOREIGN KEY`?**
    - [ ] To ensure every row in the table is unique.
    - [ ] To provide a default value for a column.
    - [ ] To enforce a link between data in two tables, ensuring referential integrity.
    - [ ] To speed up data retrieval.
    <br>

6.  **Which statement about `NULL` is true?**
    - [ ] `NULL` is the same as 0 for numeric types.
    - [ ] `NULL` is the same as an empty string ('') for string types.
    - [ ] To find rows where a column is `NULL`, you must use the `IS NULL` operator.
    - [ ] `NULL` values are included in the result of `COUNT(*)`, but not `COUNT(column_name)`.
    <br>

7.  **What is the correct order of clauses in a `SELECT` statement?**
    - [ ] `SELECT, GROUP BY, WHERE, HAVING, ORDER BY`
    - [ ] `SELECT, FROM, WHERE, GROUP BY, HAVING, ORDER BY`
    - [ ] `SELECT, FROM, HAVING, WHERE, GROUP BY, ORDER BY`
    - [ ] `SELECT, WHERE, FROM, GROUP BY, ORDER BY, HAVING`
    <br>

8.  **The `COUNT(column_name)` function, by default, counts:**
    - [ ] All rows in the table.
    - [ ] Only the rows where `column_name` has a non-`NULL` value.
    - [ ] Only the distinct values in `column_name`.
    - [ ] The number of characters in `column_name`.
    <br>

9.  **To sort the results of a query by `price` in descending order (highest to lowest), which clause would you use?**
    - [ ] `ORDER BY price ASC`
    - [ ] `GROUP BY price DESC`
    - [ ] `ORDER BY price DESC`
    - [ ] `SORT BY price DESC`
    <br>

10. **The `BETWEEN` operator, as in `WHERE price BETWEEN 10 AND 20`, is inclusive. This is equivalent to:**
    - [ ] `price > 10 AND price < 20`
    - [ ] `price >= 10 AND price <= 20`
    - [ ] `price > 10 OR price < 20`
    - [ ] `price = 10 OR price = 20`
    <br>

**Answer Key**
1.  **C**: ||A Primary Key enforces both uniqueness (no two rows can have the same key) and non-nullability (the key must have a value).||
2.  **D**: ||The DISTINCT keyword is specifically designed to remove duplicate rows from a result set, returning only the unique values. While GROUP BY would also produce unique city names, DISTINCT is the more direct and conventional tool for this specific task.||
3.  **B**: ||The WHERE clause filters rows before aggregation. Since the condition involves an aggregate function (AVG(salary)), you must use the HAVING clause to filter the groups after they have been aggregated.||
4.  **B**: ||The underscore _ is a wildcard for exactly one character. The percent sign % is a wildcard for zero or more characters. _a% means "any single character, followed by 'a', followed by anything else."||
5.  **C**: ||A Foreign Key constraint creates a relationship between a child table and a parent table. It ensures that a value entered in the foreign key column of the child table must already exist in the primary key column of the parent table.||
6.  **C**: ||NULL is a special marker for missing data and cannot be compared using standard operators like =. The correct syntax is WHERE my_column IS NULL or WHERE my_column IS NOT NULL. Note: D is also a true statement, but C addresses the comparison aspect directly.||
7.  **B**: ||The logical processing order of an SQL query is FROM -> WHERE -> GROUP BY -> HAVING -> SELECT -> ORDER BY. This is the correct syntactical order you must write them in.||
8.  **B**: ||COUNT(*) counts all rows. COUNT(column_name) specifically counts the number of rows where that particular column has a value that is not NULL. COUNT(DISTINCT column_name) counts the unique non-NULL values.||
9.  **C**: ||The ORDER BY clause is used for sorting. ASC is for ascending (the default), and DESC is for descending.||
10. **B**: ||The BETWEEN operator is inclusive of its start and end values. Therefore, price BETWEEN 10 AND 20 is equivalent to the condition price >= 10 AND price <= 20.||

---

### **Bonus Tips**

*   **Execution Order Matters:** Remember the logical execution order of a query (`FROM -> WHERE -> GROUP BY -> HAVING -> SELECT -> ORDER BY`). This explains *why* you can't use an alias from the `SELECT` clause in the `WHERE` clause (because `WHERE` is processed before `SELECT`), but you *can* use it in the `ORDER BY` clause.
*   **The Power of `GROUP BY`:** `GROUP BY` is one of the most powerful tools for data analysis. Practice using it with multiple columns (`GROUP BY city, status`) and with different aggregate functions (`COUNT`, `SUM`, `AVG`) to generate meaningful summary reports from raw data.
*   **Primary Key Choice:** When designing a table, always prefer a "natural" primary key if one exists (like a government-issued `ProductID` or `ISBN` for a book). If no good natural key exists, it is standard practice to create a "surrogate" key using an auto-incrementing integer (`INT AUTO_INCREMENT PRIMARY KEY`). This is often simpler and more efficient.
*   **Constraints are Your Friends:** Don't be lazy about adding constraints. Defining `NOT NULL`, `UNIQUE`, `FOREIGN KEY`, and `CHECK` constraints at the database level is your first and best line of defense against bad data entering your system. It's much better to have the database reject an invalid entry than to deal with corrupted data later.

**🔗Links:** [[DBT Session 6 - Relational Algebra and Joins]]