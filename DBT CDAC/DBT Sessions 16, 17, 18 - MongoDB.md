## MongoDB

Welcome to your final sessions on Database Technologies. Having understood the [[DBT Session 15 - NoSQL Database|theory behind NoSQL]], we will now do a deep dive into **MongoDB**, one of the most popular and widely used NoSQL databases in the world. MongoDB is a **Document-Oriented Database** that provides high performance, high availability, and easy scalability.

---

### Introduction to MongoDB
MongoDB stores data in flexible, JSON-like documents. This means fields can vary from document to document, and data structures can be nested. This model maps very naturally to objects in application code.

#### Features of MongoDB
*   **Document-Oriented:** Data is stored in **BSON** (Binary JSON) documents, which are a binary-encoded serialization of JSON-like documents. BSON supports more data types than JSON.
*   **Schema-less (Flexible Schema):** A collection does not enforce a document structure. This allows for easy evolution of the database schema as application requirements change.
*   **High Performance:** Performance is high due to features like in-memory computing, indexing, and its ability to scale horizontally.
*   **High Availability:** Achieved through a feature called a **Replica Set**, where copies of the data are kept on multiple servers. If the primary server fails, a secondary server is automatically elected to take its place.
*   **Scalability:** Achieved through **Sharding**, where data is distributed across multiple servers (a cluster). This allows the database to handle massive amounts of data and high throughput.

### RDBMS & MongoDB Analogies
To make the transition from SQL easier, it helps to map RDBMS concepts to MongoDB terminology.

| RDBMS (MySQL) | MongoDB | Description |
|:---|:---|:---|
| Database | Database | A container for collections/tables. |
| Table | **Collection** | A grouping of documents. |
| Row / Record | **Document** | A single record, stored in BSON format. |
| Column | **Field** | A key-value pair within a document. |
| Primary Key | **_id** (Field) | A unique identifier for a document. Automatically generated if not provided. |
| Index | Index | Data structure to improve query speed. |
| Join | **$lookup** (Aggregation)| An operation to combine data from multiple collections (less common than in SQL). |

**Visualizing the Analogy:**

`MySQL Table: Students`

| roll_no(PK)| name | city |
|:---|:---|:---|
| 101 | Ravi | Pune |

`MongoDB Collection: students`
```mongodb
{
  "_id": 101,
  "name": "Ravi",
  "city": "Pune"
}
```
This is a single **document**.

### JSON and BSON Documents
*   **JSON (JavaScript Object Notation):** A human-readable text format for representing structured data. It consists of key-value pairs.
    *   `{ "name": "John", "age": 30, "isStudent": true }`
*   **BSON (Binary JSON):** A binary-encoded serialization of JSON. This is what MongoDB uses to store data internally.
    *   **Advantages over JSON:** It is more space-efficient, faster to traverse, and supports additional data types like `Date`, `ObjectID`, and binary data.

---

### MongoDB Command Interface and Compass
*   **MongoDB Shell (`mongosh`):** A powerful command-line interface for interacting with MongoDB instances. You can run queries, perform administrative tasks, and write scripts. It uses a JavaScript-based API.
*   **MongoDB Compass:** A graphical user interface (GUI) that provides a visual way to explore your data, run queries, view query performance, and manage your database. It is the equivalent of [[DBT Session 1 - Introduction to Database Technologies#Common MySQL Clients|MySQL Workbench]].

---

### Performing CRUD Operations
CRUD stands for Create, Read, Update, and Delete. These are the four basic functions of persistent storage.

Let's assume we are working with a `products` collection.

#### **C**reate: `insertOne()` and `insertMany()`
To insert documents into a collection.

*   **Insert a single document:**
    ```javascript
    db.products.insertOne({
      name: "Laptop",
      price: 1200,
      tags: ["electronics", "pc"]
    })
    ```
*   **Insert multiple documents:**
    ```javascript
    db.products.insertMany([
      { name: "Mouse", price: 25, in_stock: true },
      { name: "Keyboard", price: 75, brand: "Logi" }
    ])
    ```

#### **R**ead: `find()` and `findOne()`
To query or retrieve documents from a collection.

*   **The Query Document:** You pass a "query document" to `find()` to filter the results. `{}` matches everything.
*   **Find all documents:**
    `db.products.find({})`
*   **Find documents with specific criteria:**
    `db.products.find({ price: { $lt: 100 } })`  // Find products where price is less than 100
*   **Find one specific document:**
    `db.products.findOne({ name: "Laptop" })`

#### **U**pdate: `updateOne()`, `updateMany()`, `replaceOne()`
To modify existing documents. Update operations take two arguments: a **filter document** to select which documents to update, and an **update document** to specify the modifications.

*   **The `$set` Operator:** This is the most common update operator. It modifies the value of a field without replacing the entire document.

*   **Update a single document:**
    ```javascript
    db.products.updateOne(
      { name: "Mouse" },                        // Filter: find the document with name "Mouse"
      { $set: { price: 28, in_stock: false } }   // Update: set the price and in_stock fields
    )
    ```
*   **Update all documents that match a filter:**
    `db.products.updateMany({ brand: "Logi" }, { $inc: { price: 5 } })` // Increase price by 5 for all Logi products

#### **D**elete: `deleteOne()` and `deleteMany()`
To remove documents from a collection.

*   **Delete a single document:**
    `db.products.deleteOne({ name: "Keyboard" })`
*   **Delete all documents that match a filter:**
    `db.products.deleteMany({ in_stock: false })`

#### UPSERT
An "update or insert" operation. If a document matching the filter is found, it is updated. If **no document** is found, a new document is **inserted**. This is achieved by adding `{ upsert: true }` as an option to an update operation.

**Example:**
```javascript
db.products.updateOne(
  { name: "Monitor" },
  { $set: { price: 250, brand: "Dell" } },
  { upsert: true } // Option
)
```
If a "Monitor" exists, its price and brand will be updated. If not, a new document `{ name: "Monitor", price: 250, brand: "Dell" }` will be created.

---

### MongoDB - Operators, Sorting, Indexing

#### Query Operators
MongoDB has a rich set of query operators (which start with `$`) to build complex queries.
*   **Comparison Operators:**
    *   `$eq` (equal), `$ne` (not equal)
    *   `$gt` (greater than), `$gte` (greater than or equal)
    *   `$lt` (less than), `$lte` (less than or equal)
    *   `$in`: Matches any of the values specified in an array. ` { status: { $in: ["A", "D"] } }`
*   **Logical Operators:**
    *   `$and`, `$or`, `$not`, `$nor`: Combine query clauses.
    *   `{ $or: [ { price: { $lt: 20 } }, { brand: "Logi" } ] }`

#### Sorting (`sort()`)
The `sort()` method is chained after a `find()` to order the results. It takes a document specifying the fields to sort by and the order.
*   `1` for ascending order.
*   `-1` for descending order.

**Example: Find all products, sorted by price descending.**
`db.products.find({}).sort({ price: -1 })`

#### Indexing (`createIndex()`)
Just like in SQL, indexes in MongoDB are crucial for query performance. Without indexes, MongoDB must perform a **collection scan**, reading every document to find matches.
*   MongoDB automatically creates an index on the `_id` field.
*   You should create indexes on fields that are frequently used in query filters and sort operations.

**Example: Create an index on the `price` field.**
`db.products.createIndex({ price: 1 })` // 1 for ascending

---

## Topic Summary & Revision

*   **MongoDB:** A leading document-oriented NoSQL database that stores data in flexible, JSON-like **BSON** documents.
*   **Analogy:** A `Database` contains `Collections`, which contain `Documents`. A `Document` contains `Fields`. The `_id` field is the primary key.
*   **CRUD Operations:** The fundamental operations for data manipulation.
    *   **Create:** `insertOne()`, `insertMany()`
    *   **Read:** `find()`, `findOne()`
    *   **Update:** `updateOne()`, `updateMany()` (commonly with the `$set` operator).
    *   **Delete:** `deleteOne()`, `deleteMany()`
*   **Upsert:** A special update option (`{ upsert: true }`) that creates a new document if one to update is not found.
*   **Querying:** Use query documents with operators like `$lt`, `$gt`, and `$in` to filter data.
*   **`sort()`:** Chained after `find()` to order results. `{ field: 1 }` for ascending, `{ field: -1 }` for descending.
*   **`createIndex()`:** Essential for query performance. Create indexes on fields you query and sort on often.

---

## MCQs for Exam Preparation

1.  **In MongoDB, what is the equivalent of a "row" in a traditional RDBMS?**
    - [ ] A Collection
    - [ ] A Field
    - [ ] A Document
    - [ ] An Index
    <br>

2.  **Which of the following is an advantage of BSON over JSON?**
    - [ ] It is human-readable text.
    - [ ] It supports more data types, like `Date` and binary data.
    - [ ] It does not require a schema.
    - [ ] It can be edited in any text editor.
    <br>

3.  **Which command is used to find all documents in a `users` collection where the `age` is greater than 30?**
    - [ ] `db.users.find({ age > 30 })`
    - [ ] `db.users.select({ age: { $gt: 30 } })`
    - [ ] `db.users.find({ age: { $gt: 30 } })`
    - [ ] `db.users.find("age > 30")`
    <br>

4.  **You want to increase the `price` of all products with the brand "Acme" by 10. Which update query is correct?**
    - [ ] `db.products.updateMany({ brand: "Acme" }, { price: price + 10 })`
    - [ ] `db.products.updateMany({ brand: "Acme" }, { $set: { price: 10 } })`
    - [ ] `db.products.updateMany({ brand: "Acme" }, { $inc: { price: 10 } })`
    - [ ] `db.products.updateMany({ $inc: { price: 10 } }, { brand: "Acme" })`
    <br>

5.  **What does the `{ upsert: true }` option in an `updateOne` operation do?**
    - [ ] It updates all documents that match the filter.
    - [ ] It inserts a new document if no document matches the filter criteria.
    - [ ] It returns an error if the document does not exist.
    - [ ] It forces the update to be applied immediately, skipping any locks.
    <br>

6.  **MongoDB achieves high availability primarily through which feature?**
    - [ ] Sharding
    - [ ] Indexing
    - [ ] BSON
    - [ ] Replica Sets
    <br>

7.  **How do you sort the results of a `find()` query in descending order by a `score` field?**
    - [ ] `db.collection.find().sort({ score: "DESC" })`
    - [ ] `db.collection.sort({ score: -1 }).find()`
    - [ ] `db.collection.find().order({ score: -1 })`
    - [ ] `db.collection.find().sort({ score: -1 })`
    <br>

8.  **What is the role of the `_id` field in a MongoDB document?**
    - [ ] It stores the ID of the user who created the document.
    - [ ] It acts as the primary key for the document and is automatically indexed.
    - [ ] It is an optional field for sorting.
    - [ ] It links the document to another collection.
    <br>

9.  **What happens if you perform an `insertOne()` operation without providing an `_id` field?**
    - [ ] MongoDB will reject the insertion with an error.
    - [ ] MongoDB will automatically generate a unique `ObjectId` for the `_id` field.
    - [ ] The document will be inserted without a primary key.
    - [ ] MongoDB will use the first field in the document as the `_id`.
    <br>

10. **Without an index, how does MongoDB find a document in a large collection?**
    - [ ] It uses a binary search.
    - [ ] It performs a collection scan, checking every document.
    - [ ] It asks the user for the location.
    - [ ] It is not possible to find a document without an index.
    <br>

**Answer Key**
1. C: ||In the MongoDB analogy, a table is a collection, and a row is a document.||
2. B: ||BSON (Binary JSON) is a binary-encoded format that is optimized for speed and space. It extends the JSON spec with additional data types like dates, binary data, and ObjectIDs, which are not native to JSON.||
3. C: ||MongoDB queries use a query document. The condition "greater than" is specified using the $gt comparison operator inside this document.||
4. C: ||The $inc operator is specifically designed to atomically increment (or decrement, with a negative value) a field's value. Using $set would replace the price with the value 10, not add to it.||
5. B: ||"Upsert" is a portmanteau of "update" and "insert." If the filter finds a document, it's updated. If not, the update document (often combined with the filter) is used as a template to insert a new document.||
6. D: ||A replica set is a group of MongoDB servers that maintain the same data set, providing redundancy and high availability. If the primary server goes down, one of the secondaries is elected as the new primary. Sharding is for scalability.||
7. D: ||The sort() method is chained after find(). It takes a document where the keys are the fields to sort by and the values are 1 for ascending or -1 for descending.||
8. B: ||The _id field is mandatory for every document and serves as its unique primary key. MongoDB automatically creates a unique index on this field to ensure fast lookups.||
9. B: ||If the user does not supply a value for _id, the MongoDB driver or server will automatically generate a unique 12-byte ObjectId and assign it to the _id field before insertion.||
10. B: ||Just like a relational database without an index on a WHERE clause column, MongoDB must perform a full collection scan, which is an O(n) operation that can be very slow on large collections.||

---

### **Bonus Tips**

*   **Document Design is Key:** The biggest shift from SQL to MongoDB is thinking about data modeling. Instead of normalizing data into many small tables, the common practice in MongoDB is to **embed** related data within a single document. For example, instead of a separate `Comments` table, a `BlogPost` document might contain an array field called `comments`. This makes reads very fast (you get the post and all its comments in one query) but can complicate updates. Choosing when to embed vs. when to link is the art of MongoDB schema design.
*   **Indexes are NOT Optional:** While you *can* run MongoDB without creating indexes, you should not do so in a production environment. Any query that cannot be fulfilled by an index will result in a collection scan. Use MongoDB Compass's "Explain Plan" feature to analyze your queries and ensure they are using indexes effectively.
*   **The Power of the Aggregation Framework:** For complex reporting and data analysis, `find()` is not enough. MongoDB has a powerful **Aggregation Framework** that allows you to process data through a multi-stage pipeline. You can group, sort, reshape, and perform calculations on your data on the server side, similar to `GROUP BY` in SQL but much more powerful.
*   **Read/Write Concerns:** When working with replica sets, you can configure the "write concern" (how many nodes must confirm a write before it's considered successful) and "read preference" (do you read from the primary for consistency or from secondaries for lower latency?). These are advanced topics but crucial for designing resilient distributed systems.

This concludes the Database Technologies module. Congratulations on completing the syllabus