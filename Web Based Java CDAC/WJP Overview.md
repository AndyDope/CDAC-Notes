## Web-based Java Programming Overview

This page provides a high-level summary of the essential concepts covered in the PG-DAC Web-based Java Programming module. Use it as a quick-recall cheat sheet before exams.

---

### [[WJP Sessions 1 & 2 - JDBC & Transaction Management|Sessions 1-2: JDBC & Transaction Management]]
*   [[WJP Sessions 1 & 2 - JDBC & Transaction Management#Introduction to JDBC API|JDBC API]]: A standard Java specification for connecting to databases, consisting of interfaces like `Connection`, `Statement`, and `ResultSet`.
*   [[WJP Sessions 1 & 2 - JDBC & Transaction Management#JDBC Architecture|JDBC Architecture]]: A two-tier model separating the standard API from vendor-specific **Drivers**, managed by a `DriverManager`.
*   [[WJP Sessions 1 & 2 - JDBC & Transaction Management#SQL Injection overview and prevention|PreparedStatement]]: The preferred method over `Statement` for executing SQL queries, as it is pre-compiled and prevents SQL injection attacks.
*   [[WJP Sessions 1 & 2 - JDBC & Transaction Management#Design Pattern: Data Access Object (DAO)|DAO Pattern]]: A design pattern that encapsulates data access logic, separating it from business logic.

---

### [[WJP Session 3 - J2EE Overview|Session 3: J2EE Overview]]
*   [[WJP Session 3 - J2EE Overview#The J2EE Container|J2EE Container]]: A runtime environment provided by an **Application Server** (e.g., Tomcat) that manages the lifecycle of web components and provides services like security and transaction management.
*   [[WJP Session 3 - J2EE Overview#Packaging Web Applications|WAR (Web Application Archive)]]: The standard packaging format for Java web applications, containing servlets, JSPs, static files, and libraries.
*   [[WJP Session 3 - J2EE Overview#The Web Application Life Cycle|Web Application Life Cycle]]: The container manages the deployment, initialization, servicing of requests, and destruction of a web application.

---

### [[WJP Sessions 4, 5, 6 & 7 - Servlets|Sessions 4-7: Servlets]]
*   [[WJP Sessions 4, 5, 6 & 7 - Servlets#The Servlet Life Cycle|Servlet Life Cycle]]: Managed by the container with three key methods: `init()` (once), `service()` (per request), and `destroy()` (once).
*   [[WJP Sessions 4, 5, 6 & 7 - Servlets#The Servlet API|HttpServlet]]: The base class for creating servlets that handle HTTP requests. You typically override `doGet()` and `doPost()`.
*   [[WJP Sessions 4, 5, 6 & 7 - Servlets#`HttpServletRequest` and `HttpServletResponse`|Request & Response Objects]]: The `HttpServletRequest` contains incoming data from the client. The `HttpServletResponse` is used to send the response back.
*   [[WJP Sessions 4, 5, 6 & 7 - Servlets#Session Management|HttpSession]]: The standard server-side mechanism for tracking a user's state across multiple stateless HTTP requests.
*   [[WJP Sessions 4, 5, 6 & 7 - Servlets#Request Dispatcher & Page Navigation|forward() vs. sendRedirect()]]: `forward()` is a server-side transfer of control where the URL doesn't change. `sendRedirect()` is a client-side redirect that involves a new request and a URL change.

---

### [[WJP Sessions 8 & 9 - JSP|Sessions 8-9: JSP (JavaServer Pages)]]
*   [[WJP Sessions 8 & 9 - JSP#JSP: Separating UI from Content Generation|JSP]]: A technology for writing web pages with HTML-like syntax that allows embedding dynamic content. A JSP is translated into a servlet.
*   [[WJP Sessions 8 & 9 - JSP#The MVC Architecture|MVC Pattern]]: In this pattern, JSPs serve as the **View** (presentation), while Servlets serve as the **Controller**.
*   [[WJP Sessions 8 & 9 - JSP#Implicit and Explicit Objects|Implicit Objects]]: Objects like `request`, `response`, `session`, and `application` that are automatically available within a JSP.
*   [[WJP Sessions 8 & 9 - JSP#Scope|Scopes]]: Attributes can be stored in four scopes: `page`, `request`, `session`, and `application`.
*   [[WJP Sessions 8 & 9 - JSP#JSTL (JSP Standard Tag Library)|JSTL & EL]]: The modern standard for writing JSPs. Use JSTL tags (`<c:forEach>`) and Expression Language (`${...}`) to avoid Java scriptlets.

---

### [[WJP Sessions 10, 11, 12 & 13 - Hibernate Framework|Sessions 10-13: Hibernate Framework]]
*   [[WJP Sessions 10, 11, 12 & 13 - Hibernate Framework#Introduction to Hibernate Framework|ORM (Object-Relational Mapping)]]: A framework like Hibernate that automates the mapping between Java objects (POJOs) and database tables.
*   [[WJP Sessions 10, 11, 12 & 13 - Hibernate Framework#Hibernate Architecture|`Session` & `SessionFactory`]]: The `SessionFactory` is a heavyweight factory for creating `Session` objects. A `Session` is a lightweight object representing a single unit of work with the database.
*   [[WJP Sessions 10, 11, 12 & 13 - Hibernate Framework#Hibernate Mappings and Relationships (using Annotations)|JPA Annotations]]: Metadata like `@Entity`, `@Id`, and `@Column` used to map a POJO to a table.
*   [[WJP Sessions 10, 11, 12 & 13 - Hibernate Framework#HQL, Named Queries, and Criteria Queries|HQL (Hibernate Query Language)]]: An object-oriented, database-independent query language that operates on entities and their properties.

---

### [[WJP Sessions 14, 15, 16 & 17 - Spring Framework|Sessions 14-17: Spring Framework]]
*   [[WJP Sessions 14, 15, 16 & 17 - Spring Framework#What is IoC (Inversion of Control)?|IoC (Inversion of Control)]]: A design principle where a container manages object creation and dependency wiring, rather than the objects themselves.
*   [[WJP Sessions 14, 15, 16 & 17 - Spring Framework#Dependency Injection (DI)|DI (Dependency Injection)]]: The implementation of IoC. **Constructor Injection** is the preferred method.
*   [[WJP Sessions 14, 15, 16 & 17 - Spring Framework#The IoC Container and Spring Beans|ApplicationContext & Beans]]: The `ApplicationContext` is the Spring IoC container that manages objects called **Beans**.
*   [[WJP Sessions 14, 15, 16 & 17 - Spring Framework#Spring MVC|Spring MVC]]: A web framework using the **Front Controller** pattern, where a central `DispatcherServlet` handles all requests.

---

### [[WJP Sessions 18, 19 & 20 - Spring Boot|Sessions 18-20: Spring Boot]]
*   [[WJP Sessions 18, 19 & 20 - Spring Boot#Why Spring Boot? The Problem it Solves|Spring Boot]]: An opinionated extension of Spring that simplifies development with auto-configuration and starter dependencies.
*   [[WJP Sessions 18, 19 & 20 - Spring Boot#Auto-Configuration|Auto-Configuration]]: Spring Boot intelligently configures the application based on the JARs present on the classpath.
*   [[WJP Sessions 18, 19 & 20 - Spring Boot#Starter POMs / Dependencies|Starter Dependencies]]: Bundles of dependencies (e.g., `spring-boot-starter-web`) that simplify Maven/Gradle configuration.
*   [[WJP Sessions 18, 19 & 20 - Spring Boot#Embedded Server|Embedded Server]]: Applications are packaged as executable `.jar` files with an embedded server like Tomcat, making deployment easy.

---

### [[WJP Sessions 21 & 22 - Spring Data JPA|Sessions 21-22: Spring Data JPA]]
*   [[WJP Sessions 21 & 22 - Spring Data JPA#Repository Support for JPA|Repository Pattern]]: A data access pattern where you define an interface, and Spring Data JPA **automatically creates the implementation** at runtime.
*   [[WJP Sessions 21 & 22 - Spring Data JPA#`CrudRepository` & `JpaRepository`|JpaRepository]]: The primary interface to extend for full CRUD and JPA functionality.
*   [[WJP Sessions 21 & 22 - Spring Data JPA#Query Methods (Derived Queries)|Derived Queries]]: Spring Data automatically creates queries from method names like `findByNameAndStatus(...)`.
*   [[WJP Sessions 21 & 22 - Spring Data JPA#Using Custom Query (`@Query`)|@Query Annotation]]: Allows you to provide a custom JPQL or native SQL query for a repository method.

---

### [[WJP Session 23 - Spring AOP|Session 23: Spring AOP]]
*   [[WJP Session 23 - Spring AOP#AOP Overview|AOP (Aspect-Oriented Programming)]]: A paradigm for modularizing **cross-cutting concerns** (like logging, security, transactions) into **Aspects**.
*   [[WJP Session 23 - Spring AOP#AOP Terminology and Annotations|Core AOP Terms]]:
    *   **Advice**: The action to take (`@Before`, `@After`).
    *   **Pointcut**: An expression that defines *where* the advice runs.
    *   **Join Point**: A point of execution (always a method in Spring AOP).
*   [[WJP Session 23 - Spring AOP#AOP Terminology and Annotations|Proxy-Based]]: Spring AOP works by creating a dynamic proxy around your bean at runtime to weave in the advice.

---

### [[WJP Sessions 24 & 25 - REST services with Spring|Sessions 24-25: REST Services with Spring]]
*   [[WJP Sessions 24 & 25 - REST services with Spring#RESTful Web Service Introduction|REST]]: An architectural style for building web services that leverages the HTTP protocol. It is stateless and resource-oriented.
*   [[WJP Sessions 24 & 25 - REST services with Spring#Using HTTP Verbs|HTTP Verbs]]: REST uses standard HTTP methods for CRUD operations: `GET` (Read), `POST` (Create), `PUT` (Update/Replace), `DELETE` (Delete).
*   [[WJP Sessions 24 & 25 - REST services with Spring#Creating a RESTful Web Service in Java using Spring Boot|@RestController]]: A Spring annotation that combines `@Controller` and `@ResponseBody`, used for building REST APIs that return data (like JSON) directly.
*   [[WJP Sessions 24 & 25 - REST services with Spring#Creating a RESTful Web Service in Java using Spring Boot|@PathVariable & @RequestBody]]: Used to bind data from the URL path and the request body to method parameters.

---

### [[WJP Sessions 26 & 27 - Testing and Security in Spring|Sessions 26-27: Testing and Security in Spring]]
*   [[WJP Sessions 26 & 27 - Testing and Security in Spring#Unit Testing|Unit Testing]]: Testing a component in isolation. Use **Mockito** to create mock objects for dependencies.
*   [[WJP Sessions 26 & 27 - Testing and Security in Spring#Integration Testing|Integration Testing]]: Testing how multiple components work together, often by loading the full Spring context with `@SpringBootTest`.
*   [[WJP Sessions 26 & 27 - Testing and Security in Spring#Securing Web Application with Spring Security|Spring Security]]: A framework for handling **Authentication** (who you are) and **Authorization** (what you can do).
*   [[WJP Sessions 26 & 27 - Testing and Security in Spring#JWT (JSON Web Token) Authorization|JWT (JSON Web Token)]]: A modern, stateless token-based standard for securing APIs.

---

### [[WJP Sessions 28 & 29 - Microservices|Sessions 28-29: Microservices]]
*   [[WJP Sessions 28 & 29 - Microservices#Introduction to Microservices|Microservices Architecture]]: An architectural style that structures an application as a collection of small, autonomous, and independently deployable services.
*   [[WJP Sessions 28 & 29 - Microservices#Key Concepts and Patterns in Microservices|Key Patterns]]:
    *   **API Gateway**: A single entry point for all client requests.
    *   **Service Discovery**: A mechanism for services to find each other dynamically.
    *   **Database per Service**: A core principle to ensure loose coupling.

---

🔗 **[[WJP MCQs|All MCQs]]**