### **Comprehensive MCQ Review: Web-based Java Programming**

Practice these questions to challenge your in-depth understanding of enterprise Java concepts. For best results, attempt to answer them before checking the key.

---

### **Topic 1: JDBC, J2EE & Servlets (Sessions 1-7)**

1.  **What is the primary reason for using a `PreparedStatement` over a `Statement` in JDBC?**
    - [ ] It allows multiple SQL statements to be executed in a single call.
    - [ ] It helps prevent SQL Injection attacks and allows the database to cache the query execution plan.
    - [ ] It can return multiple `ResultSet` objects from a single query.
    - [ ] It automatically manages database connections.
    <br>

2.  **In the context of the DAO (Data Access Object) design pattern, which layer is responsible for handling business logic and calling the DAO?**
    - [ ] The Controller Layer (e.g., Servlet)
    - [ ] The Presentation Layer (e.g., JSP)
    - [ ] The Service Layer
    - [ ] The DAO Layer itself
    <br>

3.  **Which statement best describes the relationship between the J2EE/Jakarta EE specification and an application server like Apache Tomcat?**
    - [ ] Tomcat is a specification, and J2EE is the implementation.
    - [ ] J2EE/Jakarta EE is a set of API specifications, and Tomcat is a software that implements a subset of those specifications (specifically, the Servlet and JSP specs).
    - [ ] They are competing technologies for web development.
    - [ ] Tomcat is a database server used by J2EE applications.
    <br>

4.  **What is the fundamental difference between `RequestDispatcher.forward()` and `HttpServletResponse.sendRedirect()`?**
    - [ ] `forward()` is a client-side redirect that changes the browser URL, while `sendRedirect()` is a server-side transfer.
    - [ ] `forward()` is a server-side transfer of control that is transparent to the client and keeps the same request object, while `sendRedirect()` tells the client to make a completely new request to a new URL.
    - [ ] `forward()` can only be used with JSPs, while `sendRedirect()` can be used with any URL.
    - [ ] `sendRedirect()` is more performant because it involves fewer network round trips.
    <br>

5.  **A servlet's `init(ServletConfig config)` method is called by the container:**
    - [ ] Once for every request the servlet handles.
    - [ ] Every time the user's session is created.
    - [ ] Exactly once in the servlet's lifecycle, after it is instantiated and before it serves any requests.
    - [ ] Only when the server is shutting down.
    <br>

6.  **In a multi-threaded servlet environment, why should instance variables of the servlet class be avoided for storing request-specific data?**
    - [ ] Because instance variables cannot be accessed from the `doGet()` or `doPost()` methods.
    - [ ] Because a single servlet instance is shared among multiple threads, leading to race conditions if instance variables are modified without proper synchronization.
    - [ ] Because instance variables are not garbage collected, leading to memory leaks.
    - [ ] Because storing data in instance variables is slower than storing it in local variables.
    - <br>

7.  **You need to store a "shopping cart" object for a user that must persist across multiple requests within their visit. Which is the most appropriate mechanism?**
    - [ ] `ServletContext` attributes
    - [ ] `HttpServletRequest` attributes
    - [ ] `HttpSession` attributes
    - [ ] Local variables in a servlet
    <br>

8.  **What is the primary function of the `web.xml` file (the Deployment Descriptor)?**
    - [ ] To define the HTML layout of the web application.
    - [ ] To store the Java source code for servlets.
    - [ ] To declare and configure servlets, filters, listeners, and other application components for the servlet container.
    - [ ] To list the third-party JAR files required by the application.
    <br>

9.  **Which JDBC object represents a pre-compiled SQL statement that can be executed multiple times efficiently?**
    - [ ] `Connection`
    - [ ] `Statement`
    - [ ] `ResultSet`
    - [ ] `PreparedStatement`
    <br>

10. **The `service()` method of the `HttpServlet` class typically:**
    - [ ] Contains the main business logic for a request.
    - [ ] Is overridden by developers to handle both GET and POST requests.
    - [ ] Examines the HTTP method of the request and delegates to the appropriate `doGet()`, `doPost()`, etc., method.
    - [ ] Is responsible for initializing the servlet.
    <br>

**Answer Key (1-10)**
1.  **Answer:** (B) PreparedStatement separates the SQL command from the data, preventing malicious input from being executed as code. Because the query structure is pre-compiled, the database can reuse the execution plan for subsequent calls with different data, which is more performant.
2.  **Answer:** (C) In a layered architecture, the Service Layer contains the business logic (e.g., how to process a new order). It coordinates the actions, calling one or more DAO methods (e.g., `orderDAO.save()`, `inventoryDAO.update()`) to perform the actual data persistence.
3.  **Answer:** (B) J2EE/Jakarta EE provides the "blueprint" (the interfaces and behavior contracts). An application server like Tomcat or WildFly provides the actual working code that implements this blueprint.
4.  **Answer:** (B) This is the key distinction. `forward()` is an internal, server-side hand-off. `sendRedirect()` involves two separate client-server round trips and is visible to the user as a URL change in their browser.
5.  **Answer:** (C) The `init()` method is the initialization hook in the servlet lifecycle. It is called by the container after the servlet object is created but before it is put into service.
6.  **Answer:** (B) The servlet container creates only one instance of a servlet and uses it to serve many concurrent requests, each in its own thread. If these threads modify a shared instance variable, the data can become corrupted. All request-specific data must be stored in local variables.
7.  **Answer:** (C) The `HttpSession` is designed specifically for this purpose. It provides a stateful "memory" for a specific user across multiple stateless HTTP requests. `ServletContext` is global to all users.
8.  **Answer:** (C) In traditional J2EE apps, the deployment descriptor is the central configuration file that tells the container which classes are servlets, which URL patterns they map to, and other application-wide settings.
9.  **Answer:** (D) A `PreparedStatement` is sent to the database and compiled once. It can then be executed efficiently many times with different parameter values, reducing the overhead of parsing and compiling the SQL each time.
10. **Answer:** (C) The base `HttpServlet`'s `service()` method acts as a front controller, inspecting the request method (`request.getMethod()`) and dispatching to the appropriate `doXxx()` method. This is why developers typically override `doGet` or `doPost` instead of `service` itself.
<br>

### **Topic 2: JSP, JSTL & Hibernate (Sessions 8-13)**

11. **What is the ultimate fate of a JSP file (e.g., `home.jsp`) in a J2EE application?**
    - [ ] It is sent to the browser and rendered using JavaScript.
    - [ ] It is translated into a Java Servlet class by the servlet container, then compiled and executed.
    - [ ] It is directly interpreted by the JVM.
    - [ ] It is used as a configuration file by the server.
    <br>

12. **What is the primary advantage of using Expression Language `${...}` and JSTL `<c:forEach>` over JSP scriptlets `<% ... %>`?**
    - [ ] They provide better performance due to native browser support.
    - [ ] They allow more complex Java logic to be embedded in the page.
    - [ ] They promote a clean separation of presentation from logic, making JSPs more readable and maintainable.
    - [ ] They are more secure and prevent cross-site scripting.
    <br>

13. **In an MVC pattern using Servlets and JSP, what is the standard flow?**
    - [ ] The client requests a JSP, which calls a Servlet to get data, then renders itself.
    - [ ] The client requests a Servlet (Controller), which gets data from a Model, places the data in request scope, and forwards to a JSP (View) for rendering.
    - [ ] The JSP and Servlet are independent and do not communicate.
    - [ ] The client requests a Servlet, which uses `PrintWriter` to generate all the HTML.
    <br>

14. **What is the state of a Hibernate entity object after it has been retrieved from the database using `session.get()` and the session is still open?**
    - [ ] Transient
    - [ ] Persistent
    - [ ] Detached
    - [ ] Removed
    <br>

15. **What is the "N+1 selects" problem in Hibernate?**
    - [ ] A situation where fetching N entities requires N+1 database connections.
    - [ ] An error that occurs when N+1 users try to access the same record.
    - [ ] A performance issue where one query is executed to retrieve N parent entities, and then N additional queries are executed to retrieve a lazy-loaded collection for each parent.
    - [ ] A requirement that a table must have at least N+1 columns to be mapped.
    <br>

16. **What is the fundamental difference between HQL and native SQL?**
    - [ ] HQL is a newer version of SQL.
    - [ ] HQL operates on Java entity objects and their properties, while SQL operates on database tables and columns.
    - [ ] HQL is faster than SQL.
    - [ ] HQL can only be used for `SELECT` queries.
    <br>

17. **What does the `@GeneratedValue(strategy = GenerationType.IDENTITY)` annotation signify in a JPA entity?**
    - [ ] The application is responsible for generating the primary key value.
    - [ ] The primary key value is a universally unique identifier (UUID).
    - [ ] It tells the underlying database to generate the primary key value, typically using an auto-increment column.
    - [ ] It generates a key based on the hash code of the object.
    <br>

18. **The Hibernate `Session` object is:**
    - [ ] A heavyweight, thread-safe object.
    - [ ] A lightweight, single-threaded object representing a unit of work with the database.
    - [ ] A representation of the user's web session.
    - [ ] An object that manages the connection pool.
    <br>

19. **What does "automatic dirty checking" in Hibernate mean?**
    - [ ] It automatically checks for SQL injection vulnerabilities.
    - [ ] When a transaction is committed, Hibernate automatically compares the current state of persistent objects with their original state and generates `UPDATE` statements for any changes.
    - [ ] It validates that all required fields are not null.
    - [ ] It checks the database schema for any un-mapped tables.
    <br>

20. **Which JSP implicit object is used to store data that should be available to all users across the entire web application?**
    - [ ] `request`
    - [ ] `session`
    - [ ] `pageContext`
    - [ ] `application`
    <br>

**Answer Key (11-20)**
11. **Answer:** (B) This is the fundamental mechanism of JSP. The container does a one-time translation of the JSP (which is easy for web designers to write) into a performance-optimized Java Servlet.
12. **Answer:** (C) Scriptlets embed raw Java code, mixing logic and presentation, which is hard to maintain. JSTL and EL provide a clean, declarative, tag-based approach that separates these concerns.
13. **Answer:** (B) This is the standard MVC flow. The Servlet acts as the entry point and controller, the Model handles the data logic, and the JSP is purely for presenting the data prepared by the controller.
14. **Answer:** (B) An object is in the persistent state when it is associated with an active Hibernate session. Any changes made to it will be tracked and can be automatically saved to the database.
15. **Answer:** (C) This is a major performance pitfall. It can be solved by using an eager fetching strategy (like a `JOIN FETCH` in HQL) to retrieve the parent entities and their associated collections in a single, more efficient query.
16. **Answer:** (B) HQL is an object-oriented, database-agnostic query language. This allows you to write your data access code in terms of your Java classes, and Hibernate handles the translation to the specific SQL dialect of your database.
17. **Answer:** (C) `IDENTITY` is a generation strategy that relies on the database's built-in auto-increment feature to generate and assign the primary key when a new row is inserted.
18. **Answer:** (B) The `Session` is designed to be a short-lived "conversation" with the database. It is not thread-safe and should never be shared between threads. The `SessionFactory` is the thread-safe object that creates sessions.
19. **Answer:** (B) This is a key feature of ORMs. You don't need to call `session.update()` on a persistent object you have modified. At commit time, Hibernate automatically detects the "dirty" (changed) state and persists it.
20. **Answer:** (D) The `application` scope is backed by the `ServletContext` object. It is a global, application-wide key-value store.
<br>

### **Topic 3: Spring Core & Spring MVC (Sessions 14-17)**

21. **The core principle of Inversion of Control (IoC) is implemented in Spring through:**
    - [ ] The `new` keyword.
    - [ ] The Factory pattern.
    - [ ] Aspect-Oriented Programming.
    - [ ] Dependency Injection.
    <br>

22. **What is the primary role of the `DispatcherServlet` in Spring MVC?**
    - [ ] To resolve view names to JSP files.
    - [ ] To act as a Front Controller, receiving all incoming requests and delegating them to the appropriate handlers.
    - [ ] To manage database transactions.
    - [ ] To directly render the HTML response.
    <br>

23. **Which annotation is used to mark a class as a service layer component in Spring?**
    - [ ] `@Component`
    - [ ] `@Repository`
    - [ ] `@Controller`
    - [ ] `@Service`
    <br>

24. **A bean is declared with `@Scope("prototype")`. What does this mean?**
    - [ ] A single shared instance of the bean will be created for the entire application.
    - [ ] A new instance of the bean will be created every time it is requested or injected.
    - [ ] The bean is only available during a single HTTP request.
    - [ ] The bean can only be used in the prototype phase of development.
    <br>

25. **What is the purpose of the `@Autowired` annotation?**
    - [ ] To define a class as a Spring bean.
    - [ ] To mark a dependency that the Spring IoC container should automatically resolve and inject.
    - [ ] To specify the URL mapping for a controller method.
    - [ ] To enable automatic transaction management.
    <br>

26. **In Spring MVC, what component is responsible for mapping a logical view name (like "userProfile") to a physical view file (like `/WEB-INF/views/userProfile.jsp`)?**
    - [ ] `HandlerMapping`
    - [ ] `ViewResolver`
    - [ ] `ApplicationContext`
    - [ ] The Controller itself
    <br>

27. **Why is constructor injection generally preferred over field injection (`@Autowired` on a field)?**
    - [ ] It is less verbose.
    - [ ] It allows for circular dependencies.
    - [ ] It makes it possible to create immutable components and clearly defines a class's required dependencies.
    - [ ] It is the only way to inject collections.
    <br>

### **Topic 4: Spring Boot, Data JPA, AOP & REST (Sessions 18-25)**

28. **What is the main advantage of Spring Boot's "starter" dependencies (e.g., `spring-boot-starter-web`)?**
    - [ ] They are smaller in size than individual libraries.
    - [ ] They simplify dependency management by providing a curated, compatible set of libraries for a specific functionality.
    - [ ] They provide starter code templates for your application.
    - [ ] They automatically configure security for your application.
    <br>

29. **What does the `@RestController` annotation signify in a Spring Boot application?**
    - [ ] It is a combination of `@Controller` and `@ResponseBody`, indicating that all methods will return data directly in the response body, not a view name.
    - [ ] It marks a controller that can only handle RESTful `GET` requests.
    - [ ] It enables transaction management for all methods in the controller.
    - [ ] It is a standard `@Controller` that requires a `ViewResolver`.
    <br>

30. **In Spring Data JPA, how do you define a custom query to find users by their email address?**
    - [ ] By implementing the repository interface and writing the JDBC code yourself.
    - [ ] By declaring a method in the repository interface named `User findByEmail(String email);`.
    - [ ] By configuring the query in an XML file.
    - [ ] You must use the `Criteria API`.
    <br>

**Answer Key (21-30)**  
21. **Answer:** (D) Dependency Injection is the primary pattern through which the Inversion of Control principle is implemented in Spring. The container "injects" dependencies rather than the object creating them itself.  
22. **Answer:** (B) The DispatcherServlet is the core of Spring MVC's Front Controller pattern. It intercepts all requests and orchestrates the entire process of finding a handler, invoking it, and rendering a view.  
23. **Answer:** (D) While @Component is the generic stereotype, @Service is the specialized annotation used to indicate that a class belongs to the business logic or service layer.  
24. **Answer:** (B) The prototype scope ensures that a brand-new instance of the bean is created for every injection or every request to the container. The default scope is singleton.  
25. **Answer:** (B) @Autowired is the primary mechanism for triggering dependency injection. It tells the Spring container to find a compatible bean in its context and inject it at that point (a constructor, field, or setter method).  
26. **Answer:** (B) The ViewResolver is responsible for translating the logical string name returned by a controller (e.g., "userProfile") into a physical view resource that can be rendered (e.g., a specific JSP or Thymeleaf file).  
27. **Answer:** (C) Constructor injection makes the required dependencies explicit in the constructor's signature. This prevents an object from being created without its essential dependencies and makes it easier to instantiate in unit tests without needing a Spring container. It also allows fields to be final.  
28. **Answer:** (B) "Starters" are the core of Spring Boot's "convention over configuration" philosophy. They provide a single, version-managed dependency in your pom.xml that transitively pulls in all the other necessary libraries for a specific task, like building a web app or connecting to a database.  
29. **Answer:** (A) @RestController is a convenience annotation specifically for building REST APIs. It implies that the return value of every method should be serialized (e.g., to JSON) and written directly to the HTTP response body, bypassing the view resolution mechanism.  
30. **Answer:** (B) Spring Data's derived query feature allows developers to define queries simply by creating a method signature that follows a specific naming convention. Spring parses the name and automatically generates the corresponding query.  
<br>

31. **What is an "Aspect" in AOP?**
    - [ ] The specific point in a program's execution where an action can be taken.
    - [ ] The action that is taken at a join point.
    - [ ] A module that encapsulates a cross-cutting concern, containing both advice and pointcuts.
    - [ ] The object that is being advised.
    <br>

32. **Which AOP advice type would you use to log the successful return value of a method?**
    - [ ] `@Before`
    - [ ] `@AfterThrowing`
    - [ ] `@Around`
    - [ ] `@AfterReturning`
    <br>

33. **In a RESTful API, which HTTP method is idempotent and used to fully replace an existing resource?**
    - [ ] `POST`
    - [ ] `GET`
    - [ ] `PUT`
    - [ ] `PATCH`
    <br>

34. **What is the purpose of the `@PathVariable` annotation in a Spring MVC controller method?**
    - [ ] To bind a URL query parameter (e.g., `?id=123`) to a method parameter.
    - [ ] To bind a value from the URI path itself (e.g., the `123` in `/users/123`) to a method parameter.
    - [ ] To bind the entire HTTP request body to a parameter.
    - [ ] To specify the path of the view to be rendered.
    <br>

### **Topic 5: Advanced Spring & Microservices (Sessions 26-29)**

35. **The `@SpringBootTest` annotation is used to:**
    - [ ] Run only unit tests for a specific layer.
    - [ ] Bootstrap the entire Spring ApplicationContext to run full integration tests.
    - [ ] Test the performance of the Spring Boot startup process.
    - [ ] Generate a test report.
    <br>

36. **What is the primary role of an API Gateway in a microservice architecture?**
    - [ ] To discover the location of other services.
    - [ ] To act as a single, unified entry point for all external clients, handling concerns like routing, authentication, and rate limiting.
    - [ ] To store the shared data for all microservices.
    - [ ] To deploy and manage the lifecycle of microservices.
    <br>

37. **The principle of "one database per service" in microservices helps to ensure:**
    - [ ] Loose coupling between services.
    - [ ] Strong transactional consistency across the entire application.
    - [ ] Simplified database management.
    - [ ] Faster query performance through joins.
    <br>

38. **What problem does a "Service Registry" (like Eureka) solve in a microservice architecture?**
    - [ ] It handles user authentication.
    - [ ] It provides a mechanism for services to dynamically find the network locations of other services.
    - [ ] It aggregates logs from all services.
    - [ ] It routes traffic between services.
    <br>

39. **What is the key difference between Authentication and Authorization?**
    - [ ] Authentication is for external users, while Authorization is for internal services.
    - [ ] Authentication determines "who you are," while Authorization determines "what you are allowed to do."
    - [ ] Authorization happens before Authentication.
    - [ ] They are the same concept in Spring Security.
    <br>

40. **What is a key characteristic of JWT (JSON Web Token) based authentication?**
    - [ ] It is stateful and requires the server to store session information.
    - [ ] The token is self-contained and digitally signed, allowing for stateless verification by the server.
    - [ ] The token must be stored in a server-side cookie.
    - [ ] It can only be used for authorization, not authentication.
    <br>

31. **Answer:** (C) An Aspect is a class (marked with @Aspect) that modularizes a cross-cutting concern. It contains both the Advice (the logic to execute) and the Pointcuts (the definitions of where to execute it).  
32. **Answer:** (D) @AfterReturning is the specific advice type that executes only after the target method completes successfully. It can also be given access to the return value of the method for logging or modification.  
33. **Answer:** (C) PUT is the standard HTTP verb for fully replacing a resource at a given URI. It is idempotent because sending the same PUT request multiple times results in the same final state. PATCH is for partial updates.  
34. **Answer:** (B) @PathVariable is used to extract values from the URI itself. For a URL template like /users/{userId}, the @PathVariable annotation would bind the value from that segment to a method parameter.  
35. **Answer:** (B) @SpringBootTest is used for integration testing. It bootstraps the entire Spring application, loading all beans and configurations, allowing you to test the interaction between different layers of your application.  
36. **Answer:** (B) The API Gateway pattern provides a single point of entry for all external clients. It simplifies the client by acting as a facade, and it can handle cross-cutting concerns like authentication, logging, and rate limiting before routing requests to the appropriate internal microservices.  
37. **Answer:** (A) By giving each service exclusive ownership of its own database, you ensure that the service's data schema can be evolved independently without breaking other services. This enforces loose coupling, a core goal of microservices.  
38. **Answer:** (B) In a dynamic, cloud-based environment where services can be scaled up or down and their network addresses change, a Service Registry provides a lookup service (like a phonebook) for one service to find the current, healthy location of another.  
39. **Answer:** (B) This is the fundamental distinction. Authentication verifies identity (e.g., checking a username and password). Authorization checks permissions based on that verified identity (e.g., checking if a user has the ROLE_ADMIN to access a specific feature).  
40. **Answer:** (B) A JWT is self-contained. It includes user identity and permissions in its payload and is digitally signed. A server can verify the token's authenticity using the signature without needing to store any session state, which makes the architecture highly scalable.  
<br>

### **Final Review Questions (All Topics)**

41. **What is the return type of the `findById(ID id)` method in Spring Data's `CrudRepository`?**
    - [ ] `T`
    - [ ] `List<T>`
    - [ ] `Optional<T>`
    - [ ] `boolean`
    <br>

42. **A "Pointcut" in Spring AOP defines:**
    - [ ] The action to be taken.
    - [ ] The location of the aspect class.
    - [ ] A predicate that matches the join points (methods) where an advice should be executed.
    - [ ] A point where the application has failed.
    <br>

43. **Which tool would you use to test a REST API endpoint by sending a `POST` request with a JSON body?**
    - [ ] A web browser's address bar.
    - [ ] A JDBC client.
    - [ ] An application like Postman or a command-line tool like cURL.
    - [ ] A J-Unit test without any mocking.
    <br>

44. **Which `pom.xml` dependency would you add to a Spring Boot project to build a RESTful web service?**
    - [ ] `spring-boot-starter-jpa`
    - [ ] `spring-boot-starter-security`
    - [ ] `spring-boot-starter-web`
    - [ ] `spring-boot-starter-aop`
    <br>

45. **Which `@Transactional` propagation level will execute in the context of the current transaction if one exists, or start a new one if it does not?**
    - [ ] `REQUIRED`
    - [ ] `REQUIRES_NEW`
    - [ ] `MANDATORY`
    - [ ] `NEVER`
    <br>

46. **What is the most significant challenge introduced by the "database per service" pattern in microservices?**
    - [ ] Managing database schemas.
    - [ ] Managing data consistency and transactions across multiple services.
    - [ ] Connecting to the databases from the services.
    - [ ] Backing up the individual databases.
    <br>

47. **To test a Spring MVC controller in isolation from the service layer, you would use:**
    - [ ] `@SpringBootTest` and a real database.
    - [ ] `@DataJpaTest` to test only the repository layer.
    - [ ] `@WebMvcTest` along with `@MockBean` for the service dependency.
    - [ ] A simple JUnit test without any Spring context.
    <br>

48. **In Spring AOP, `@Around` advice is considered the most powerful because:**
    - [ ] It runs before all other advice types.
    - [ ] It can prevent the target method from executing at all and can modify the return value.
    - [ ] It is the only advice that can be used with static methods.
    - [ ] It runs in a separate thread.
    <br>

49. **What is the purpose of the `spring-boot-maven-plugin` in a `pom.xml`?**
    - [ ] To download Spring Boot's dependencies.
    - [ ] To compile the Java code.
    - [ ] To package the application into a single, executable "fat JAR" with all dependencies included.
    - [ ] To run the application's unit tests.
    <br>

50. **The concept of `_links` in a JSON response, which provides URLs for related actions or resources, is an implementation of which REST constraint?**
    - [ ] Stateless
    - [ ] Client-Server
    - [ ] Cacheable
    - [ ] HATEOAS (Hypermedia as the Engine of Application State)
    <br>

**Answer Key (41-50)**
41. **Answer:** (C) To avoid NullPointerExceptions, modern repository methods return an `Optional<T>`. This forces the calling code to explicitly handle the case where no entity is found for the given ID.
42. **Answer:** (C) The pointcut is the "where" of AOP. It is an expression that selects the set of join points (methods) that the advice should apply to.
43. **Answer:** (C) A browser's address bar can only make GET requests. Tools like Postman are specifically designed for API testing, allowing you to construct requests with any HTTP method, set headers, and add a request body.
44. **Answer:** (C) The `spring-boot-starter-web` is the primary starter for building web applications, including REST APIs. It brings in Spring MVC, an embedded Tomcat server, and JSON serialization libraries.
45. **Answer:** (A) `REQUIRED` is the default propagation level. It ensures that the method runs within a transaction, either by joining an existing one or creating a new one if none is active. `REQUIRES_NEW` would always suspend the current transaction and start a new one.
46. **Answer:** (B) Since there is no single database with ACID properties, ensuring data remains consistent when an operation spans multiple services (e.g., placing an order that must update inventory, charge a payment, and send a notification) requires complex patterns like the Saga pattern or two-phase commit.
47. **Answer:** (C) `@WebMvcTest` loads only the web layer (controllers, filters, etc.) and not the service or repository layers. `@MockBean` is then used to provide a mock implementation of the service that the controller depends on.
48. **Answer:** (B) `@Around` advice wraps the target method. It receives a `ProceedingJoinPoint` which it can use to call the original method (`pjp.proceed()`). It can choose not to call it, call it multiple times, or modify the arguments and the final return value.
49. **Answer:** (C) This plugin is essential for Spring Boot. It collects all the project's compiled code and all of its dependency JARs and packages them into a single, executable JAR file, making deployment trivial.
50. **Answer:** (D) HATEOAS is the principle that a REST API should be discoverable, just like a website. By including links to related actions in the response, the client can navigate the API without needing to have all the possible URLs hardcoded.