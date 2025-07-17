### **Comprehensive MCQ Review: Database Technologies (Hard)**
Practice these questions to challenge your in-depth understanding of database concepts. For best results, attempt to answer them before checking the key.

---
### **Topic 1: Database Design & Normalization (Sessions 1-4)**

1.  **A table of `Orders` contains `OrderID` (PK), `OrderDate`, `CustomerID`, `CustomerName`, and `CustomerAddress`. Assuming `CustomerID` functionally determines `CustomerName` and `CustomerAddress`, this design violates which normal form?**
- [ ] First Normal Form (1NF)
- [ ] Second Normal Form (2NF)
- [ ] Third Normal Form (3NF)
- [ ] The design is already in 3NF.
<br>

2.  **Which of the following scenarios describes a "Deletion Anomaly"?**
- [ ] Being unable to add a new professor until they are assigned to teach a course.
- [ ] Having to update a professor's phone number in multiple rows if they teach multiple courses.
- [ ] Deleting the record of the only student enrolled in a particular course, which results in the loss of all information about that course.
- [ ] Storing a professor's multiple phone numbers in a single comma-separated string field.
<br>

3.  **A table has a composite primary key consisting of `(StudentID, CourseID)`. An attribute in the table is `CourseProfessor`. If `CourseProfessor` depends only on `CourseID`, this is a violation of:**
- [ ] 1NF
- [ ] 2NF
- [ ] 3NF
- [ ] BCNF
<br>

4.  **What is a key difference in how `DELETE FROM table;` and `TRUNCATE TABLE table;` are handled by a transactional database system?**
- [ ] `TRUNCATE` is a DML command, while `DELETE` is DDL.
- [ ] `DELETE` fires `DELETE` triggers for each row, while `TRUNCATE` typically does not.
- [ ] `DELETE` resets the `AUTO_INCREMENT` counter, while `TRUNCATE` does not.
- [ ] `TRUNCATE` can be used with a `WHERE` clause, while `DELETE` cannot.
<br>

5.  **Boyce-Codd Normal Form (BCNF) is stricter than 3NF. A table is in 3NF but not in BCNF if:**
- [ ] It contains a transitive dependency.
- [ ] A non-key attribute determines a part of the primary key.
- [ ] A part of a candidate key determines a non-key attribute.
- [ ] A non-key attribute determines a part of a candidate key.
<br>

6.  **During which phase of data modeling would you make DBMS-specific decisions like choosing the `InnoDB` storage engine or defining a `TIMESTAMP` data type?**
- [ ] Conceptual Data Model
- [ ] Logical Data Model
- [ ] Physical Data Model
- [ ] All of the above
<br>

7.  **If `A -> B` and `B -> C` both hold in a relation, what is the term for the dependency `A -> C`?**
- [ ] Partial dependency
- [ ] Join dependency
- [ ] Transitive dependency
- [ ] Multi-valued dependency
<br>

8.  **The primary purpose of database normalization is to:**
- [ ] Improve query performance by adding redundancy.
- [ ] Reduce the number of tables in the database.
- [ ] Minimize data redundancy and prevent data anomalies.
- [ ] Enforce security constraints on data access.
<br>

9.  **A table `(StudentID, CourseID, ProfessorID)` has a composite primary key `(StudentID, CourseID)`. It also has the dependency `ProfessorID -> CourseID`. This design is problematic because:**
- [ ] It violates 1NF.
- [ ] It has a partial dependency.
- [ ] It has a transitive dependency.
- [ ] The determinant `ProfessorID` is not a candidate key, violating BCNF.
<br>

10. **The `CREATE TABLE ... LIKE` statement in MySQL copies:**
- [ ] The table structure and all the data from the original table.
- [ ] Only the primary key and foreign key constraints.
- [ ] The table structure including columns, data types, and indexes, but none of the data.
- [ ] Only the column names and not the data types.
<br>

**Answer Key (1-10)**
1.  **Answer:** ||(C) This is a classic transitive dependency. OrderID -> CustomerID, and CustomerID -> CustomerName. A non-key attribute (CustomerID) determines another non-key attribute (CustomerName). CustomerName and CustomerAddress should be in a separate Customers table.||
2.  **Answer:** ||(C) A deletion anomaly occurs when the deletion of one set of facts inadvertently causes the deletion of a completely different set of facts. In this case, removing the last student enrollment also removes the course's existence from the database.||
3.  **Answer:** ||(B) This is the definition of a partial dependency. The non-key attribute CourseProfessor depends on only a part of the composite primary key (CourseID), not the whole key. This violates Second Normal Form.||
4.  **Answer:** ||(B) Because DELETE is a DML operation that removes rows one by one, it will fire any ON DELETE triggers for each affected row. TRUNCATE is a DDL operation that deallocates the data pages and typically bypasses these individual row triggers.||
5.  **Answer:** ||(D) This is a complex but key distinction. A table can be in 3NF but not BCNF when a non-key attribute determines part of a composite candidate key. Essentially, BCNF is stricter by requiring that every determinant in a functional dependency must be a superkey.||
6.  **Answer:** ||(C) The Physical Data Model is where the abstract logical design is translated into a concrete implementation for a specific DBMS, including choices like storage engines, indexing strategies, and vendor-specific data types.||
7.  **Answer:** ||(C) This is the definition of a transitive dependency, where an indirect relationship causes a functional dependency between two non-key attributes.||
8.  **Answer:** ||(C) The entire process of normalization is designed to reduce or eliminate data redundancy, which in turn prevents insertion, update, and deletion anomalies.||
9.  **Answer:** ||(D) In this case, ProfessorID determines CourseID. However, ProfessorID itself is not a candidate key (it doesn't uniquely identify a row). For a table to be in BCNF, every determinant must be a superkey. This design violates BCNF.||
10. **Answer:** ||(C) CREATE TABLE ... LIKE is a DDL statement that creates an empty table with the exact same structure, including all column definitions, indexes, and constraints, as the original table.||
<br>

### **Topic 2: SQL Queries, Joins & Subqueries (Sessions 5-7)**

11. **To find all departments that currently have no employees, which query is most appropriate?**
- [ ] `SELECT d.DeptName FROM Departments d INNER JOIN Employees e ON d.DeptID = e.DeptID;`
- [ ] `SELECT d.DeptName FROM Departments d LEFT JOIN Employees e ON d.DeptID = e.DeptID WHERE e.EmpID IS NULL;`
- [ ] `SELECT d.DeptName FROM Departments d RIGHT JOIN Employees e ON d.DeptID = e.DeptID WHERE d.DeptID IS NULL;`
- [ ] `SELECT d.DeptName FROM Departments d WHERE e.EmpID IS NULL;`
<br>

12. **What is the functional difference between `COUNT(*)` and `COUNT(DISTINCT column_name)`?**
- [ ] There is no difference.
- [ ] `COUNT(*)` counts all rows, while `COUNT(DISTINCT column_name)` counts the number of unique non-NULL values in that column.
- [ ] `COUNT(*)` is faster because it does not need to check for uniqueness.
- [ ] Both B and C are correct.
<br>

13. **Which statement correctly describes the logical processing order of SQL clauses?**
- [ ] `SELECT -> FROM -> WHERE -> GROUP BY -> HAVING -> ORDER BY`
- [ ] `FROM -> WHERE -> GROUP BY -> HAVING -> SELECT -> ORDER BY`
- [ ] `FROM -> JOIN -> SELECT -> WHERE -> GROUP BY -> HAVING -> ORDER BY`
- [ ] `SELECT -> WHERE -> HAVING -> GROUP BY -> FROM -> ORDER BY`
<br>

14. **A query to find employees whose salary is greater than the average salary of their respective departments requires what kind of subquery?**
- [ ] A scalar subquery
- [ ] An inline view
- [ ] A multi-row subquery using `IN`
- [ ] A correlated subquery
<br>

15. **Why might a query using `NOT EXISTS` be more performant than one using `NOT IN`?**
- [ ] `NOT EXISTS` can use indexes more efficiently.
- [ ] `NOT EXISTS` stops processing the subquery as soon as it finds a single match, whereas `NOT IN` must build the entire list of values.
- [ ] `NOT IN` handles `NULL` values from the subquery in an unexpected way, often returning no rows, while `NOT EXISTS` handles them correctly.
- [ ] Both B and C are significant reasons.
<br>

16. **You want a list of all employees and all departments. If an employee has no department, or a department has no employees, they should still appear in the list. Which operation is needed?**
- [ ] `INNER JOIN`
- [ ] `LEFT JOIN`
- [ ] `CROSS JOIN`
- [ ] `FULL OUTER JOIN`
<br>

17. **What is a "scalar subquery"?**
- [ ] A subquery that returns multiple rows and multiple columns.
- [ ] A subquery that is guaranteed to return exactly one row and one column.
- [ ] A subquery used only in the `FROM` clause.
- [ ] A subquery that is correlated with the outer query.
<br>

18. **The SQL query `SELECT name FROM Employees UNION SELECT name FROM Customers;` will return:**
- [ ] A combined list of all employee and customer names, including duplicates.
- [ ] A combined list of all employee and customer names, with duplicate names removed.
- [ ] An error, because the tables are different.
- [ ] A list of names that appear in both the `Employees` and `Customers` tables.
<br>

19. **What is the result of a `LEFT JOIN` from `TableA` to `TableB` where the `ON` condition is always false (e.g., `ON 1=0`)?**
- [ ] An empty result set.
- [ ] A `CROSS JOIN` of the two tables.
- [ ] All rows from `TableA`, with columns from `TableB` being `NULL`.
- [ ] A syntax error.
<br>

20. **To find the second highest salary in a table, the query `SELECT salary FROM Employees ORDER BY salary DESC LIMIT 1, 1;` is used. What does `LIMIT 1, 1` mean?**
- [ ] Select 1 row starting from the 1st row.
- [ ] Select 1 row after skipping the first row.
- [ ] Select 2 rows starting from the 1st row.
- [ ] Select 1 column and 1 row.
<br>

**Answer Key (11-20)**
11. **Answer:** ||(B) A LEFT JOIN from Departments to Employees will include all departments. For those departments with no matching employee, the columns from the Employees table (like e.EmpID) will be NULL. The WHERE clause then filters to find only these rows.||
12. **Answer:** ||(B) COUNT(*) counts all rows returned by the query. COUNT(DISTINCT column_name) first finds all the unique values in that column (ignoring NULLs) and then counts them. C is also true, but B is the primary functional difference.||
13. **Answer:** ||(B) This is the correct logical processing order. It explains why a column alias defined in the SELECT clause cannot be used in the WHERE or GROUP BY clause of the same query level.||
14. **Answer:** ||(D) This requires a correlated subquery because the average salary needs to be recalculated for each employee's specific department. The subquery must be linked to the outer query's current row (e.g., WHERE E2.DeptID = E1.DeptID).||
15. **Answer:** ||(D) The NOT IN operator fails if the subquery result set contains even a single NULL value, because value NOT IN (..., NULL, ...) evaluates to unknown, not true. NOT EXISTS does not have this problem. Additionally, EXISTS can stop early, improving performance.||
16. **Answer:** ||(D) A FULL OUTER JOIN combines the results of both a LEFT JOIN and a RIGHT JOIN, ensuring all rows from both tables are included, with NULLs filling in where there are no matches.||
17. **Answer:** ||(B) A scalar subquery returns a single value (a scalar). It can be used anywhere a single literal value is expected, such as in a SELECT list or in a comparison in the WHERE clause.||
18. **Answer:** ||(B) UNION combines the result sets of two queries and removes any duplicate rows from the final combined set. UNION ALL would include the duplicates.||
19. **Answer:** ||(C) The LEFT JOIN guarantees that every row from TableA will be in the result set. Since the ON condition can never be true, there will be no matching rows from TableB, so all columns from TableB will be NULL.||
20. **Answer:** ||(B) The LIMIT clause syntax is LIMIT [offset,] row_count. So LIMIT 1, 1 means skip 1 row, then fetch 1 row. This effectively selects the second row from the result set.||
<br>

### **Topic 3: Advanced SQL & MySQL Internals (Sessions 8-12)**

21. **What is a key difference in locking mechanisms between `InnoDB` and `MyISAM`?**
- [ ] `InnoDB` uses optimistic locking, while `MyISAM` uses pessimistic locking.
- [ ] `InnoDB` uses row-level locking, while `MyISAM` uses table-level locking.
- [ ] `InnoDB` does not use locks, while `MyISAM` does.
- [ ] `InnoDB` locks the entire database for writes, while `MyISAM` locks only the table.
<br>

22. **What is the effect of the `ISOLATION` property in an ACID-compliant system?**
- [ ] It ensures that each transaction is executed in a separate memory space.
- [ ] It prevents transactions from interfering with each other's intermediate and uncommitted results.
- [ ] It isolates the database from network failures.
- [ ] It guarantees that the database can be restored after a crash.
<br>

23. **Why would a developer choose to use a Stored Function over a Stored Procedure?**
- [ ] The logic involves multiple DML statements and transaction control.
- [ ] The logic needs to return multiple values back to the caller.
- [ ] The logic needs to be embedded directly within a `SELECT` or `WHERE` clause of a standard SQL query.
- [ ] The logic requires complex error handling.
<br>

24. **Inside a stored procedure loop, you have `DECLARE CONTINUE HANDLER FOR SQLEXCEPTION SET has_error = 1;`. What happens when an SQL error occurs inside the loop?**
- [ ] The `has_error` flag is set to 1, the loop terminates, and the procedure exits.
- [ ] The procedure crashes with an unhandled exception.
- [ ] The `has_error` flag is set to 1, and execution resumes at the statement immediately following the one that caused the error.
- [ ] The `has_error` flag is set to 1, and the current iteration of the loop is skipped.
<br>

25. **What is a major downside of using cursors for data processing?**
- [ ] They can only be used on indexed columns.
- [ ] They are generally much less performant than set-based SQL operations.
- [ ] They do not support transaction control.
- [ ] They can only be used in triggers, not in stored procedures.
<br>

26. **What is the purpose of the `DETERMINISTIC` keyword when creating a function?**
- [ ] It indicates that the function will always complete within a determined amount of time.
- [ ] It is a hint to the optimizer that the function will always return the same output for the same input parameters.
- [ ] It means the function can only be called from a stored procedure.
- [ ] It forces the function to be re-evaluated every time it is called, even with the same arguments.
<br>

27. **A composite index is created on `(LastName, FirstName)`. Which `WHERE` clause can most efficiently use this index?**
- [ ] `WHERE FirstName = 'John'`
- [ ] `WHERE LastName = 'Smith'`
- [ ] `WHERE FirstName = 'John' OR LastName = 'Smith'`
- [ ] `WHERE LastName > 'Smith'`
<br>

28. **In a stored procedure, what is the key difference between an `OUT` parameter and a function's `RETURN` value?**
- [ ] A procedure can have multiple `OUT` parameters, while a function can only return a single value.
- [ ] An `OUT` parameter can be of any data type, while a `RETURN` value must be an integer.
- [ ] An `OUT` parameter is faster.
- [ ] There is no difference.
<br>

29. **You have a procedure with a cursor loop. You must ensure a resource is freed up, regardless of whether the loop completes successfully or an error occurs. Where should the resource-freeing code be placed?**
- [ ] Inside the loop.
- [ ] Immediately after the `CLOSE CURSOR` statement.
- [ ] Inside an `EXIT` handler for `SQLEXCEPTION`.
- [ ] It's not possible to guarantee this.
<br>

30. **Which statement is true regarding the MySQL `MEMORY` storage engine?**
- [ ] It is ACID compliant.
- [ ] Data persists after a server restart.
- [ ] All data is stored in RAM, making it extremely fast but volatile.
- [ ] It supports foreign key constraints.
<br>

**Answer Key (21-30)**
21. **Answer:** ||(B) This is a fundamental architectural difference. InnoDB's row-level locking provides much higher concurrency, as a write on one row does not block a write on a different row. MyISAM's table-level locking is a major bottleneck in write-heavy applications.||
22. **Answer:** ||(B) Isolation prevents concurrency-related data anomalies like dirty reads, non-repeatable reads, and phantom reads by making transactions appear to run sequentially, even when they are executing concurrently.||
23. **Answer:** ||(C) The unique ability of a function to be called within a SELECT, WHERE, GROUP BY, etc., is its primary advantage. If you need to perform a calculation on a per-row basis within a query, a function is the tool to use.||
24. **Answer:** ||(C) The CONTINUE action specifically means the handler's code executes, and then control flow resumes at the very next statement after the one that failed, allowing the procedure block to continue running.||
25. **Answer:** ||(B) Cursors force a row-by-row (RBAR - "row by agonizing row") processing model, which defeats the purpose of a set-based language like SQL. The overhead of fetching each row individually is immense compared to a single set-based UPDATE or SELECT.||
26. **Answer:** ||(B) This hint allows the query optimizer to make better decisions. If a function is deterministic, the optimizer knows it can cache the result and reuse it if the function is called again with the same inputs within the same query.||
27. **Answer:** ||(B) A composite index works like a phone book sorted by Last Name, then First Name. You can efficiently look up by "Smith" (the first part of the index) or by "Smith, John". You cannot efficiently look up by just "John" because you'd have to scan all entries for every last name.||
28. **Answer:** ||(A) This is the key difference. A function is limited to a single return value. A procedure can have no output or can return many different values through multiple OUT or INOUT parameters.||
29. **Answer:** ||(C) An EXIT handler for a general SQLEXCEPTION provides a guaranteed "catch-all" block. Placing the resource-freeing logic here ensures it will run before the procedure block terminates, even if an unexpected error occurs.||
30. **Answer:** ||(C) The MEMORY (or HEAP) storage engine stores all its data in memory. This makes it incredibly fast for lookup tables or temporary data, but all data is lost if the MySQL server restarts.||
<br>

### **Topic 4: Triggers & NoSQL Concepts (Sessions 13-15)**

31. **Which of the following is an invalid `CREATE TRIGGER` statement in MySQL?**
- [ ] `CREATE TRIGGER my_trigger BEFORE INSERT ON my_table ...`
- [ ] `CREATE TRIGGER my_trigger AFTER DELETE ON my_table ...`
- [ ] `CREATE TRIGGER my_trigger BEFORE SELECT ON my_table ...`
- [ ] `CREATE TRIGGER my_trigger AFTER UPDATE ON my_table ...`
<br>

32. **Inside a `BEFORE UPDATE` trigger, what does the statement `SET NEW.last_modified = NOW();` accomplish?**
- [ ] It modifies the existing row on disk before the update is applied.
- [ ] It modifies the incoming data value for the `last_modified` column before the update operation proceeds.
- [ ] It will cause an error because `NEW` is read-only.
- [ ] It logs the update time to a separate table.
<br>

33. **A system needs to choose between Consistency and Availability during a network partition. This trade-off is described by:**
- [ ] The ACID properties
- [ ] The BASE principles
- [ ] The CAP Theorem
- [ ] Codd's 12 Rules
<br>

34. **The principle of "Eventual Consistency" means that:**
- [ ] The system is not consistent and should not be used.
- [ ] All reads are guaranteed to see the result of the most recent write.
- [ ] All nodes in a distributed system are updated simultaneously.
- [ ] If no new updates are made, all replicas will gradually converge to the same state over time.
<br>

35. **Which NoSQL data model is represented by the following structure: `{ "_id": 1, "name": "Laptop", "specs": { "cpu": "i7", "ram": 16 }, "tags": ["pc", "work"] }`?**
- [ ] Key-Value
- [ ] Graph
- [ ] Column-Oriented
- [ ] Document
<br>

36. **When would a `BEFORE DELETE` trigger be most useful?**
- [ ] To log the deleted data to an archive table.
- [ ] To prevent the deletion of a row if a certain business rule is not met.
- [ ] To update a summary table after the deletion is complete.
- [ ] To send an email notification about the deletion.
<br>

37. **What is a key motivation for using a "schema-on-read" approach as seen in document databases?**
- [ ] It guarantees stronger data integrity than a fixed schema.
- [ ] It simplifies database administration.
- [ ] It provides greater flexibility and allows for easier application evolution without costly schema migrations.
- [ ] It improves query performance.
<br>

38. **Which of the following is NOT a category of NoSQL database?**
- [ ] Document Store
- [ ] Graph Store
- [ ] Relational Store
- [ ] Key-Value Store
<br>

39. **Inside an `AFTER UPDATE` trigger, you try to `SIGNAL` an error to cancel the operation. What happens?**
- [ ] The original `UPDATE` is rolled back.
- [ ] The trigger fails, but the `UPDATE` operation remains committed.
- [ ] It is not possible to use `SIGNAL` in an `AFTER` trigger.
- [ ] The error is logged, but the operation succeeds.
<br>

40. **The BASE acronym stands for:**
- [ ] Binary, Available, Scalable, Efficient
- [ ] Basically Available, Soft State, Eventual Consistency
- [ ] Before ACID, Start Early
- [ ] Basically ACID, Stronger Eventually
<br>

**Answer Key (31-40)**
31. **Answer:** ||(C) Triggers in MySQL are DML triggers. They can only be fired by data modification events (INSERT, UPDATE, DELETE). They cannot be fired by SELECT statements.||
32. **Answer:** ||(B) The BEFORE trigger intercepts the data before the write operation. The NEW pseudo-row represents this incoming data, and it is mutable. This allows you to clean, validate, or enrich the data before it's saved.||
33. **Answer:** ||(C) The CAP Theorem, formulated by Eric Brewer, states that a distributed data store can only provide two of the three guarantees: Consistency, Availability, and Partition Tolerance.||
34. **Answer:** ||(D) Eventual consistency is a core principle of many distributed NoSQL systems. It prioritizes availability, accepting that there may be a short lag before a write propagates to all replicas and becomes visible in all reads.||
35. **Answer:** ||(D) This structure, with nested objects and arrays, is a classic example of a JSON/BSON document, which is the model used by document databases like MongoDB.||
36. **Answer:** ||(B) A BEFORE trigger is for validation. It can check a condition (e.g., IF OLD.status = 'active' THEN...) and use SIGNAL to raise an error, which cancels the DELETE statement before it executes. Logging is better done in an AFTER trigger.||
37. **Answer:** ||(C) In agile development environments, application requirements change frequently. A flexible schema-on-read model allows developers to add new fields to their data without needing to perform a rigid ALTER TABLE schema migration on the entire database.||
38. **Answer:** ||(C) Relational stores (RDBMS) are the category of databases that NoSQL is defined in contrast to.||
39. **Answer:** ||(B) An AFTER trigger executes after the DML operation has already completed. At this point, it is too late to cancel the operation. Attempting to use SIGNAL in an AFTER trigger will cause the trigger itself to fail, but the original data change will likely have already been committed (if autocommit is on).||
40. **Answer:** ||(B) BASE is the set of principles often used to describe the properties of NoSQL databases, contrasting with the traditional ACID guarantees of RDBMSs.||
<br>

### **Topic 5: MongoDB (Sessions 16-18)**

41. **What is the purpose of the `$lookup` stage in a MongoDB aggregation pipeline?**
- [ ] To find documents based on a text search index.
- [ ] To perform a left outer join to another collection in the same database.
- [ ] To look up the data type of a specific field.
- [ ] To create a new view from the aggregation results.
<br>

42. **A MongoDB query is `db.inventory.find({ qty: { $in: [5, 15] } })`. What does it select?**
- [ ] Documents where `qty` is between 5 and 15.
- [ ] Documents where `qty` is an array containing both 5 and 15.
- [ ] Documents where the `qty` field's value is either 5 OR 15.
- [ ] Documents where `qty` is not equal to 5 or 15.
<br>

43. **What is a "replica set" in MongoDB?**
- [ ] A method for splitting data across multiple servers for scalability.
- [ ] A group of MongoDB servers that maintain the same data set, providing redundancy and high availability.
- [ ] A read-only copy of a collection.
- [ ] A set of rules for data validation.
<br>

44. **Which update operator is used to add an element to an array field within a document?**
- [ ] `$set`
- [ ] `$inc`
- [ ] `$addToSet`
- [ ] `$push`
<br>

45. **What happens if you attempt to insert a document into a collection without an `_id` field?**
- [ ] The operation fails with an error.
- [ ] The document is inserted, but it cannot be queried.
- [ ] The MongoDB driver or server automatically generates a unique `ObjectId` for the `_id` field.
- [ ] The value of the first field in the document is used as the `_id`.
<br>

46. **How do you create a compound index on the `city` (ascending) and `age` (descending) fields in a `users` collection?**
- [ ] `db.users.createIndex({ city: 1, age: -1 })`
- [ ] `db.users.createIndex("city ASC, age DESC")`
- [ ] `db.users.createIndex({ city, age }, { order: "ASC, DESC" })`
- [ ] `db.users.addIndex({ city: 1, age: -1 })`
<br>

47. **What does the term "sharding" refer to in the context of MongoDB?**
- [ ] The process of encrypting data at rest.
- [ ] The process of creating a backup of the database.
- [ ] The process of keeping identical copies of data on multiple servers for high availability.
- [ ] The process of horizontally partitioning data across multiple servers for scalability.
<br>

48. **Which command would you use to remove all documents from a `logs` collection?**
- [ ] `db.logs.truncate()`
- [ ] `db.logs.drop()`
- [ ] `db.logs.deleteMany({})`
- [ ] `db.logs.removeAll()`
<br>

49. **In a MongoDB query, how do you specify that you only want the `name` and `email` fields to be returned (and also the mandatory `_id`)?**
- [ ] `db.users.find({}, { fields: ["name", "email"] })`
- [ ] `db.users.find({ name: 1, email: 1 })`
- [ ] `db.users.find({}, { name: 1, email: 1 })`
- [ ] `db.users.select("name, email")`
<br>

50. **What is a key difference between BSON and JSON?**
- [ ] BSON is human-readable text, while JSON is binary.
- [ ] BSON supports additional data types like `Date` and `ObjectId` that are not native to JSON.
- [ ] BSON does not support nested documents.
- [ ] JSON is used for storage, while BSON is used for network transfer.
<br>

**Answer Key (41-50)**
41. **Answer:** ||(B) \$lookup is MongoDB's aggregation pipeline stage for performing a left outer join from one collection to another, allowing you to de-normalize data for queries.||
42. **Answer:** ||(C) The \$in operator takes an array of values and matches any document where the specified field's value is one of the elements in that array.||
43. **Answer:** ||(B) A replica set is MongoDB's mechanism for high availability and redundancy. If the primary node fails, an automatic failover process elects a new primary from the secondary nodes.||
44. **Answer:** ||(D) The $push operator is specifically designed to append a value to an array field. $addToSet is similar but only adds the value if it's not already present.||
45. **Answer:** ||(C) Every document must have a unique _id. If the client does not provide one, a unique 12-byte ObjectId composed of a timestamp, machine ID, process ID, and a counter is generated.||
46. **Answer:** ||(A) Indexes are created by passing a document to createIndex. The keys of the document are the fields to be indexed, and the values are 1 for an ascending index or -1 for a descending index.||
47. **Answer:** ||(D) Sharding is MongoDB's solution for horizontal scaling (scale-out). It distributes data across a cluster of servers, allowing the database to handle datasets and load far beyond the capabilities of a single server.||
48. **Answer:** ||(C) deleteMany({}) with an empty filter document {} will match and delete all documents in the collection. db.collection.drop() would remove the entire collection, including its indexes.||
49. **Answer:** ||(C) The second argument to the find() method is the "projection" document. You specify the fields to include with a 1. The \_id field is returned by default unless you explicitly exclude it with _id: 0.||
50. **Answer:** ||(B) BSON (Binary JSON) is a binary-encoded serialization format. It is more compact and faster for machines to parse than text-based JSON and extends the JSON specification with more data types.||