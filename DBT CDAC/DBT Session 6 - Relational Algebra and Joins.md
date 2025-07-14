## Relational Algebra and Joins

Welcome to Session 6. In a well-normalized database, data is split across multiple tables to reduce redundancy. But how do we combine this data back together to get meaningful information? This session covers **Relational Algebra**, the theoretical foundation for querying relational data, and **SQL Joins**, the practical implementation used to combine rows from two or more tables based on a related column between them.

---

### Relational Algebra Operations
Relational Algebra is a formal, procedural query language. It takes relations (tables) as input and produces relations as output. Understanding these core operations helps you think more clearly about what your SQL queries are actually doing.

*   **Selection (σ):** Selects a subset of **rows (tuples)** from a relation that satisfy a given condition. This is the conceptual basis for the SQL `WHERE` clause.
    *   `σ_{city='Pune'}(Students)` -> Returns all rows from the `Students` table where the city is 'Pune'.

*   **Projection (π):** Selects a subset of **columns (attributes)** from a relation. This is the conceptual basis for the `SELECT column1, column2` part of an SQL query. It also eliminates duplicate rows in the result.
    *   `π_{name, city}(Students)` -> Returns only the `name` and `city` columns for all students.

*   **Union (∪):** Combines the rows of two relations. The two relations must be **union-compatible** (have the same number of columns, and corresponding columns must have compatible data types). It automatically removes duplicate rows. This corresponds to `UNION` in SQL.

*   **Set Difference (Minus, -):** Returns rows that are in the first relation but not in the second. The relations must be union-compatible. Corresponds to `MINUS` or `EXCEPT` in some SQL dialects.

*   **Cartesian Product (Cross Product, ×):** Combines every row of the first relation with every row of the second relation. If table A has `m` rows and table B has `n` rows, the result has `m × n` rows. This is the foundation from which joins are built. Corresponds to `CROSS JOIN` in SQL.

*   **Intersection (∩)\*:** Returns rows that are present in both relations. The relations must be union-compatible. Corresponds to `INTERSECT` in SQL.
    _(\*Not all DBMS directly support Intersect/Minus, but the same result can be achieved with other operations like joins or subqueries)._

> **Quick Question:** If you want to get a list of just the names of all employees from the `Employees` table, which two relational algebra operations would you conceptually use?
> **Answer:** You would use **Selection** to get all rows (`σ_{true}(Employees)`) and then **Projection** to select only the `name` column (`π_{name}(...)`). This is equivalent to `SELECT name FROM Employees;`.

---

### Joins
A **Join** is an operation that combines rows from two or more tables based on a related column. It is essentially a **Cartesian Product followed by a Selection** based on the join condition.

Let's use these two tables for our examples:
**`Employees`**

| EmpID(PK) | Name  | DeptID(FK) |
| --------- | ----- | ---------- |
| 101       | Ravi  | 10         |
| 102       | Priya | 20         |
| 103       | Amit  | 10         |
| 104       | Sumit | NULL       |

**`Departments`**

| DeptID(PK) | DeptName   |
| :--------- | :--------- |
| 10         | Technology |
| 20         | HR         |
| 30         | Marketing  |

#### Inner Join
An **Inner Join** returns only the rows that have matching values in both tables. It is the most common type of join.

**SQL Syntax (Standard):**
```sql
SELECT E.Name, D.DeptName
FROM Employees E
INNER JOIN Departments D ON E.DeptID = D.DeptID;
```
**Execution Flow & Visualization:**
1.  Conceptually, a cross product is formed.
2.  The `ON` clause then filters this result, keeping only the rows where `Employees.DeptID` equals `Departments.DeptID`.
3.  The `SELECT` clause then projects the required columns.

**Result:**

| Name  | DeptName   |
|:------|:-----------|
| Ravi  | Technology |
| Priya | HR         |
| Amit  | Technology |
*(Note: Sumit (no department) and Marketing (no employees) are excluded).*

#### Outer Joins
Outer joins are used when you want to keep all rows from one table, even if there are no matching rows in the other table.

*   **`LEFT OUTER JOIN` (or `LEFT JOIN`)**: Returns **all rows from the left table** and the matched rows from the right table. If there is no match, the columns from the right table will contain `NULL`.

    **Example:** Find all employees and their department names.
```sql
SELECT E.Name, D.DeptName
FROM Employees E
LEFT JOIN Departments D ON E.DeptID = D.DeptID;
```
**Result:**

| Name  | DeptName   |
|:------|:-----------|
| Ravi  | Technology |
| Priya | HR         |
| Amit  | Technology |
| Sumit | NULL       |
*(Sumit is included because `Employees` is the left table).*

*   **`RIGHT OUTER JOIN` (or `RIGHT JOIN`)**: Returns **all rows from the right table** and the matched rows from the left table. If there is no match, the columns from the left table will contain `NULL`.

    **Example:** Find all departments and the employees in them.
```sql
SELECT E.Name, D.DeptName
FROM Employees E
RIGHT JOIN Departments D ON E.DeptID = D.DeptID;
```
**Result:**

| Name  | DeptName   |
|:------|:-----------|
| Ravi  | Technology |
| Amit  | Technology |
| Priya | HR         |
| NULL  | Marketing  |
*(Marketing is included because `Departments` is the right table).*

*   **`FULL OUTER JOIN`**: Returns all rows when there is a match in either the left or the right table. It's a combination of `LEFT` and `RIGHT JOIN`. (MySQL does not directly support `FULL OUTER JOIN`, but it can be simulated using a `UNION` of a `LEFT JOIN` and a `RIGHT JOIN`).

#### Other Join Types
*   **`CROSS JOIN`**: Produces the Cartesian product of the two tables. It has no `ON` clause.
*   **`NATURAL JOIN`**: A special type of join that automatically joins tables based on columns that have the **same name and data type**. It can be dangerous because it might join on unintended columns if schemas change. It's generally better to be explicit with an `ON` clause.

> **Quick Question:** You need a list of all departments, and for each department, you want to show the employees who work there. If a department has no employees, it should still appear in the list. Which type of join would you use?
> **Answer:** A `RIGHT JOIN` with `Departments` as the right table, or more conventionally, a `LEFT JOIN` with `Departments` as the left table (`FROM Departments LEFT JOIN Employees ...`).

---

### Other Useful Concepts

*   **Sequences (`AUTO_INCREMENT`)**: A feature that automatically generates a unique number when a new record is inserted into a table. It is commonly used for primary key columns.
```mysql
CREATE TABLE Users (id INT AUTO_INCREMENT PRIMARY KEY, ...);
```

*   **Copying Table Structure/Data**:
    *   To create an empty table with the same structure as another:
        `CREATE TABLE NewTable LIKE OldTable;`
    *   To create a table and populate it with data from another:
        `CREATE TABLE NewTable AS SELECT * FROM OldTable;`

---

### Topic Summary & Revision

*   **Relational Algebra:** The theoretical foundation of SQL. Key operations are **Selection (σ)** for rows (`WHERE`), **Projection (π)** for columns (`SELECT`), and Cartesian Product.
*   **Joins:** Used to combine data from multiple tables.
    *   **`INNER JOIN`**: Returns only matching rows from both tables.
    *   **`LEFT JOIN`**: Returns all rows from the left table, plus matches from the right.
    *   **`RIGHT JOIN`**: Returns all rows from the right table, plus matches from the left.
*   **Join Condition:** The `ON` clause specifies how the tables are related (e.g., `ON table1.pk = table2.fk`).
*   **`AUTO_INCREMENT`:** A useful constraint for automatically generating unique primary key values.

---

### MCQs for Exam Preparation

1.  **Which relational algebra operation is conceptually equivalent to the `WHERE` clause in SQL?**
    - [ ] Projection (π)
    - [ ] Selection (σ)
    - [ ] Union (∪)
    - [ ] Cartesian Product (×)
    <br>

2.  **You want to get a list of all customers and any orders they have placed. Every customer should appear in the result, even if they have placed no orders. Which join should you use?**
    - [ ] `SELECT * FROM Customers INNER JOIN Orders ON ...`
    - [ ] `SELECT * FROM Customers LEFT JOIN Orders ON ...`
    - [ ] `SELECT * FROM Customers RIGHT JOIN Orders ON ...`
    - [ ] `SELECT * FROM Customers CROSS JOIN Orders`
    <br>

3.  **If `TableA` has 5 rows and `TableB` has 4 rows, how many rows will `TableA CROSS JOIN TableB` produce?**
    - [ ] 4
    - [ ] 5
    - [ ] 9
    - [ ] 20
    <br>

4.  **The `ON` clause in a `JOIN` statement is used to:**
    - [ ] Specify which columns to display in the final result.
    - [ ] Filter the final result set based on a condition.
    - [ ] Define the condition for matching rows between the tables.
    - [ ] Sort the results of the join.
    <br>

5.  **Which statement is true about `UNION` and `UNION ALL`?**
    - [ ] `UNION` is faster because it does not check for duplicates.
    - [ ] `UNION ALL` includes duplicate rows from the results, while `UNION` removes them.
    - [ ] They are identical commands.
    - [ ] `UNION` works on tables with different numbers of columns, while `UNION ALL` does not.
    <br>

6.  **A `NATURAL JOIN` between `TableA` and `TableB` will join them based on:**
    - [ ] The primary key of `TableA` and the foreign key of `TableB`.
    - [ ] The first column of each table.
    - [ ] All columns that have the same name and compatible data types in both tables.
    - [ ] A condition explicitly provided in a `WHERE` clause.
    <br>

7.  **If a `LEFT JOIN` is performed (`TableA LEFT JOIN TableB`), and a row in `TableA` has no matching row in `TableB`, what will be the values of the columns from `TableB` in the result row?**
    - [ ] 0
    - [ ] An empty string
    - [ ] The row from `TableA` will be excluded.
    - [ ] `NULL`
    <br>

8.  **The query `SELECT * FROM Employees, Departments;` (without a `WHERE` clause) is equivalent to:**
    - [ ] `Employees INNER JOIN Departments`
    - [ ] `Employees LEFT JOIN Departments`
    - [ ] `Employees CROSS JOIN Departments`
    - [ ] `Employees NATURAL JOIN Departments`
    <br>

9.  **Which operation forms the theoretical basis of all join operations?**
    - [ ] Union
    - [ ] Projection
    - [ ] Cartesian Product
    - [ ] Set Difference
    <br>

10. **To create a new table `OldEmployees` and copy all records of employees hired before the year 2010 from the `Employees` table, which query is most suitable?**
    - [ ] `CREATE TABLE OldEmployees LIKE Employees;`
    - [ ] `INSERT INTO OldEmployees SELECT * FROM Employees;`
    - [ ] `CREATE TABLE OldEmployees (SELECT * FROM Employees WHERE hire_year < 2010);`
    - [ ] `CREATE TABLE OldEmployees AS SELECT * FROM Employees WHERE hire_year < 2010;`
    <br>

**Answer Key**
1. B: ||Selection (σ) is the formal operation for filtering rows based on a predicate, which is exactly what the WHERE clause does in SQL.||
2. B: ||A LEFT JOIN with Customers as the left table will ensure that every row from Customers is included in the result. If an order exists, its details will be shown; otherwise, the order-related columns will be NULL.||
3. D: ||A CROSS JOIN or Cartesian product creates every possible combination of rows from the two tables. The resulting number of rows is the product of the number of rows in each table (5 \* 4 = 20).||
4. C: ||The ON clause specifies the join-condition, which tells the DBMS how to match rows. This is typically done by equating the primary key of one table with the foreign key of another.||
5. B: ||Both UNION and UNION ALL combine the results of two queries. However, UNION performs the extra step of filtering out duplicate rows from the final result, while UNION ALL simply appends the results, making it faster.||
6. C: ||A NATURAL JOIN implicitly looks for all columns that share the same name in both tables and creates the join condition based on them. This can be convenient but is often discouraged in production code because it's not explicit and can break if column names are changed.||
7. D: ||For rows in the "all" table (the left table in a LEFT JOIN) that do not have a match in the other table, the columns selected from the other table are filled with NULL values.||
8. C: ||The comma-separated syntax in the FROM clause is the older, implicit syntax for a CROSS JOIN. It is functionally equivalent to the modern, explicit CROSS JOIN keyword.||
9. C: ||A join is conceptually a Cartesian Product that produces all possible row combinations, followed by a Selection that filters out only the rows that meet the join condition.||
10. D: ||The CREATE TABLE ... AS SELECT ... syntax is the standard way to create a new table and immediately populate it with the results of a query in a single command.||

---

### **Bonus Tips**

*   **`INNER JOIN` is the Default:** If you just write `JOIN` without specifying `LEFT`, `RIGHT`, or `CROSS`, the DBMS will interpret it as an `INNER JOIN`.
*   **Always Use Standard `JOIN` Syntax:** Avoid the old comma-separated join syntax (`FROM table1, table2 WHERE table1.id = table2.id`). The modern, explicit `JOIN ... ON` syntax is clearer, less error-prone (you can't accidentally forget the join condition and create a massive cross join), and is necessary for performing `OUTER JOIN`s.
*   **Table Aliases are Your Friend:** When writing joins, give your tables short, meaningful aliases (e.g., `FROM Employees e JOIN Departments d`). This makes your query much shorter and more readable, especially when you have to reference columns like `e.name` and `d.dept_name`.
*   **Think About the Question:** Before writing a join, ask yourself: "Do I need only the records that match in both tables (INNER JOIN)? Or do I need all records from one of the tables, even if they don't have a match (LEFT/RIGHT JOIN)?" This will guide you to the correct join type.

**🔗Links:** [[DBT Session 7 - Subqueries, Views, and Transaction Control]]