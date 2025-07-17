## **Sessions 21 & 22: Spring Data JPA**

Welcome. We have seen how [[WJP Sessions 10, 11, 12 & 13 - Hibernate Framework|Hibernate]] solves the problem of writing boilerplate [[WJP Sessions 1 & 2 - JDBC & Transaction Management|JDBC]]. However, even with Hibernate, you still have to write a **DAO (Data Access Object)** class for each entity, which involves writing code to get a session, begin a transaction, save the entity, and commit.

**Spring Data JPA** takes this abstraction one level higher. Its goal is to make the data access layer incredibly simple by **eliminating the need to write the DAO implementation class entirely.**

---

### Spring Data Module
Spring Data is a high-level project within the Spring ecosystem whose purpose is to unify and simplify access to different kinds of persistence stores, both relational (JPA) and NoSQL (MongoDB, Redis, etc.). **Spring Data JPA** is the specific module for working with relational databases via the JPA specification.

### Repository Support for JPA
The core idea of Spring Data is the **Repository** pattern. A repository is an interface that defines the data access operations for a specific domain entity.

**The Magic:** You only need to **define the interface**. Spring Data JPA will automatically create a proxy class at runtime that provides the implementation for you.

#### `CrudRepository` & `JpaRepository`
Spring Data provides a set of base interfaces that you can extend to get standard CRUD functionality for free.

1.  **`CrudRepository<T, ID>`**: The most basic interface. It provides standard Create, Read, Update, and Delete operations.
    *   `T`: The entity type (e.g., `Student`).
    *   `ID`: The data type of the entity's primary key (e.g., `Integer`).
    *   **Provides methods like:** `save()`, `findById()`, `findAll()`, `deleteById()`, `count()`.

2.  **`JpaRepository<T, ID>`**: This interface extends `CrudRepository` and adds JPA-specific functionality.
    *   **Adds methods like:** `findAll()` (with sorting), `flush()`, `saveAndFlush()`.
    *   This is the interface you will most commonly use for relational data.

**How to Create a Repository:**
It's as simple as creating an interface.

```java
// Import the necessary classes
import org.springframework.data.jpa.repository.JpaRepository;

// No @Repository annotation is needed here, Spring Boot detects it automatically
public interface StudentRepository extends JpaRepository<Student, Integer> {
    // That's it! All CRUD methods are now available.
}
```

**Using the Repository in a Service:**
You can now inject this repository into your service layer just like any other bean.

```java
@Service
public class StudentServiceImpl implements StudentService {
    private final StudentRepository studentRepo;

    @Autowired // Constructor Injection
    public StudentServiceImpl(StudentRepository studentRepo) {
        this.studentRepo = studentRepo;
    }

    public Student registerStudent(Student student) {
        // No more boilerplate! Just call the method from the interface.
        return studentRepo.save(student);
    }
    
    public Optional<Student> findStudentById(Integer id) {
        return studentRepo.findById(id);
    }
}
```
Spring Boot's auto-configuration sees `spring-boot-starter-data-jpa`, detects your `StudentRepository` interface, and automatically generates a bean that implements all the standard CRUD methods.

> **Quick Question:** If you create an interface `public interface ProductRepository extends CrudRepository<Product, Long>` and inject it into your service, which method would you call to save a new `Product` object?
> **Answer:** You would call the `save()` method (e.g., `productRepository.save(newProduct)`), which is provided automatically by the `CrudRepository`.

---

### Query Methods (Derived Queries)
This is another powerful feature. You can define custom query methods just by declaring a method in your repository interface with a specific naming convention. Spring Data will parse the method name and create the appropriate query for you.

The convention is typically `findBy...`, `readBy...`, `queryBy...`, `countBy...`, `getBy...`.

**Examples:**
Assuming an `Employee` entity with fields `name` and `department`:

*   **`List<Employee> findByName(String name);`**
    *   Spring Data generates: `SELECT * FROM employees WHERE name = ?`

*   **`List<Employee> findByNameAndDepartment(String name, String dept);`**
    *   Spring Data generates: `SELECT * FROM employees WHERE name = ? AND department = ?`

*   **`List<Employee> findBySalaryGreaterThan(double salary);`**
    *   Spring Data generates: `SELECT * FROM employees WHERE salary > ?`

*   **`List<Employee> findByNameContainingIgnoreCase(String substring);`**
    *   Spring Data generates: `SELECT * FROM employees WHERE LOWER(name) LIKE ?`

This allows you to write a huge number of common queries without writing a single line of HQL or SQL.

### Using Custom Query (`@Query`)
For queries that are too complex for the method name convention, you can provide your own query using the `@Query` annotation. This gives you full control.

*   You can write the query in **JPQL** (Java Persistence Query Language - similar to HQL) or native SQL.

**Example (using JPQL):**
```java
public interface EmployeeRepository extends JpaRepository<Employee, Integer> {

    // JPQL uses entity and property names
    @Query("SELECT e FROM Employee e WHERE e.department = :dept AND e.salary > :minSalary")
    List<Employee> findByDeptAndMinSalary(
        @Param("dept") String department, 
        @Param("minSalary") double salary
    );

    // Example using native SQL
    @Query(value = "SELECT * FROM employees WHERE department_name = ?1", nativeQuery = true)
    List<Employee> findByDepartmentNative(String departmentName);
}
```
*   `:` syntax (e.g., `:dept`) is for named parameters, which are mapped using the `@Param` annotation.
*   `?` syntax (e.g., `?1`) is for positional parameters.

---

### Topic Summary & Revision

*   **Spring Data JPA:** A framework that dramatically simplifies the data access layer by providing repository support.
*   **Repository Pattern:** You define an `interface` for your data access methods, and Spring Data **automatically provides the implementation** at runtime.
*   **`JpaRepository`**: The main interface to extend for full CRUD and JPA-specific functionality. `JpaRepository<EntityType, PrimaryKeyType>`.
*   **Derived Queries:** Spring Data can automatically generate queries from method names like `findByNameAndStatus(...)`.
*   **`@Query` Annotation:** Used to define custom, complex queries using JPQL or native SQL directly on a repository method.

---

### MCQs for Exam Preparation

1.  **What is the main purpose of the Spring Data repository abstraction?**
    - [ ] To replace the need for a database.
    - [ ] To eliminate the need for writing boilerplate implementation code for the data access layer.
    - [ ] To provide a web interface for accessing the database.
    - [ ] To automatically generate business logic.
    <br>

2.  **To get basic CRUD (Create, Read, Update, Delete) functionality for an entity `Product` with a primary key of type `String`, which interface would you create?**
    - [ ] `public interface ProductRepository extends JpaRepository<Product, String> {}`
    - [ ] `public class ProductRepository implements CrudRepository<Product, String> {}`
    - [ ] `public interface ProductRepository {}`
    - [ ] `public class ProductRepository extends JpaRepository<String, Product> {}`
    <br>

3.  **You declare a method `List<User> findByLastName(String lastName);` in your `UserRepository`. How does Spring Data JPA implement this?**
    - [ ] You must provide a class that implements this method.
    - [ ] It scans the method name at runtime, parses it, and automatically generates the appropriate query (`WHERE lastName = ?`).
    - [ ] It requires an `@Query` annotation to work.
    - [ ] This is not a valid way to define a query.
    <br>

4.  **Which method is provided by `JpaRepository` but NOT by the more basic `CrudRepository`?**
    - [ ] `save(entity)`
    - [ ] `findById(id)`
    - [ ] `findAll(Sort sort)`
    - [ ] `deleteById(id)`
    <br>

5.  **What is JPQL (Java Persistence Query Language)?**
    - [ ] A proprietary query language for the Oracle database.
    - [ ] Another name for standard SQL.
    - [ ] A database-independent query language that operates on persistent entities and their properties, not on database tables.
    - [ ] A JavaScript-based language for querying JSON.
    <br>

6.  **In an `@Query` annotation, what does `nativeQuery = true` signify?**
    - [ ] The query is guaranteed to run faster.
    - [ ] The query string provided is plain, database-specific SQL, not JPQL.
    - [ ] The query can only be run on the developer's local machine.
    - [ ] The query returns native Java objects instead of entities.
    <br>

7.  **You need to define a query to find all users whose email address is NOT NULL and who are active. What would the derived query method signature look like?**
    - [ ] `List<User> findByEmailNotNullAndStatusActive();`
    - [ ] `List<User> findByEmailIsNotNullAndActiveIsTrue();`
    - [ ] `List<User> findByEmail_IsNotNull_And_Status_IsTrue();`
    - [ ] `List<User> findUsersWhereEmailIsNotNullAndIsActive();`
    <br>

8.  **What is the return type of the `findById(ID id)` method in `CrudRepository`?**
    - [ ] `T` (the entity type)
    - [ ] `List<T>`
    - [ ] `Optional<T>`
    - [ ] `boolean`
    <br>

9.  **To pass a named parameter `p_name` to a JPQL query defined with `@Query`, which annotation do you use on the method parameter?**
    - [ ] `@Parameter`
    - [ ] `@Bind`
    - [ ] `@Param`
    - [ ] `@Named`
    <br>

10. **The implementation of your repository interface is created by Spring Data JPA at:**
    - [ ] Compile time.
    - [ ] Application startup time (runtime).
    - [ ] The first time the repository is injected.
    - [ ] It must be manually written by the developer.
    <br>

**Answer Key**
1.  **B**: ||The goal of Spring Data is to make data access incredibly easy by providing a repository abstraction that removes the need for developers to write the implementation of common CRUD and query methods.||
2.  **A**: ||You define an interface that extends one of Spring Data's base repository interfaces, like JpaRepository. You specify the entity type (Product) and the primary key type (String) as generic parameters.||
3.  **B**: ||This feature is called "derived queries" or "query methods". Spring Data's powerful mechanism parses the method name, recognizes keywords like FindBy, And, Or, GreaterThan, etc., and constructs the corresponding JPQL or SQL query automatically.||
4.  **C**: ||JpaRepository extends PagingAndSortingRepository, which extends CrudRepository. It adds JPA-specific features, including methods that accept Sort objects for ordering and methods for batch operations.||
5.  **C**: ||JPQL (and HQL) is a portable, object-oriented query language. You write queries using your Java class names and field names (SELECT u FROM User u WHERE u.lastName = ...), and the persistence provider (like Hibernate) translates it to the appropriate SQL dialect for your database.||
6.  **B**: ||Setting nativeQuery = true tells Spring Data that the query string is not JPQL and should be passed directly to the database as a native SQL query. This is useful for database-specific features but makes the query non-portable.||
7.  **B**: ||Spring Data can parse complex method names. The keywords IsNotNull and IsTrue are recognized and translated into the appropriate WHERE clause conditions.||
8.  **C**: ||To avoid NullPointerExceptions, modern data access methods return an Optional\<T>. This forces the caller to explicitly handle the case where no entity is found for the given ID (e.g., using .isPresent() or .orElse()).||
9.  **C**: ||When using named parameters in a @Query (e.g., :p_name), you must use the @Param("p_name") annotation on the corresponding method parameter to link them.||
10. **B**: ||During application startup, Spring scans for interfaces that extend its repository interfaces. For each one it finds, it dynamically creates a proxy class that implements the interface and registers it as a bean in the application context.||

---

### **Bonus Tips**

*   **`Optional<T>` is Your Friend:** Always use the `Optional<T>` return type for methods that find a single entity (like `findById` or `findByName`). It makes your service layer code much safer and more explicit by forcing you to handle the "not found" case, thus preventing `NullPointerException`s.
*   **Don't Expose `JpaRepository`:** In a well-designed application, your service layer should not depend on the `JpaRepository` interface directly. Your custom repository (`ProductRepository`) should extend it, but the service should only be aware of your custom repository. This follows the Interface Segregation Principle and hides the implementation details of the data layer.
*   **Projections:** Sometimes you don't need the entire entity object; you just need a few fields. Spring Data allows you to use **projections**. You can define an interface with just the getter methods for the fields you want, and Spring Data will automatically generate a query that selects only those columns, which is very efficient.
*   **Pageable and Sort:** For queries that can return many results, you should use the `PagingAndSortingRepository` (which `JpaRepository` extends). This allows you to pass `Pageable` and `Sort` objects to your query methods to easily implement pagination and sorting at the database level, which is far more efficient than doing it in memory.

**🔗Links:** [[WJP Session 23 - Spring AOP]]