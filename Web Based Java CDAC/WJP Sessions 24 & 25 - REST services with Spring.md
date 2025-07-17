## **Sessions 24 & 25: Building REST Services with Spring**

Welcome. So far, our [[WJP Sessions 14, 15, 16 & 17 - Spring Framework|Spring MVC]] applications have been designed to return HTML views for browsers. However, in modern application architecture, it is far more common to build a backend that provides data to many different types of clients (e.g., a web front-end, a mobile app, another backend service).

This is achieved by building a **Web Service**. We will focus on the **REST (REpresentational State Transfer)** architectural style, which is the de facto standard for building web APIs today.

---

### Introduction to Web Services
A **Web Service** is a standardized way for applications to communicate with each other over the web. It provides a service that can be invoked remotely.

#### SOAP vs. RESTful Web Services
*   **SOAP (Simple Object Access Protocol):** An older, formal protocol-based standard.
    *   **Format:** Strictly uses XML.
    *   **Transport:** Can use various protocols, but most often HTTP.
    *   **Characteristics:** Has a rigid structure defined by a WSDL (Web Services Description Language) file. It is generally considered "heavyweight" but has strong standards for security and transactions.

*   **REST (REpresentational State Transfer):** An architectural style, not a strict protocol. It leverages the existing features of the HTTP protocol.
    *   **Format:** Can use any format, but almost always uses **JSON**.
    *   **Transport:** Uses HTTP exclusively.
    *   **Characteristics:** It is simple, lightweight, and stateless. It is the dominant architectural style for web APIs today.

### RESTful Web Service Introduction
REST is not a protocol; it's a set of architectural constraints. When an API adheres to these constraints, it is called "RESTful".

**The Six Constraints of REST:**

1.  **Client-Server Architecture:** The client (front-end) and server (back-end) are separated.
2.  **Stateless:** Each request from a client to the server must contain all the information needed to understand and complete the request. The server does not store any client session state between requests.
3.  **Cacheable:** Responses must be definable as cacheable or non-cacheable.
4.  **Uniform Interface:** This is the most important constraint and has four sub-constraints:
    *   **Identification of Resources:** Everything is a **resource**, and each resource is identified by a unique URI (Uniform Resource Identifier), e.g., `/api/products/123`.
    *   **Manipulation of Resources Through Representations:** The client interacts with a representation of the resource (e.g., a JSON object).
    *   **Self-descriptive Messages:** Each request/response contains enough information for the other party to understand it (e.g., using HTTP headers like `Content-Type: application/json`).
    *   **HATEOAS (Hypermedia as the Engine of Application State):** Responses can contain links to other related actions or resources.
5.  **Layered System:** A client cannot ordinarily tell whether it is connected directly to the end server or to an intermediary along the way.
6.  **Code on Demand (Optional):** The server can temporarily extend or customize the functionality of a client by transferring logic that it can execute (e.g., JavaScript).

#### Using HTTP Verbs
REST leverages standard HTTP methods (verbs) to perform CRUD operations on resources.

*   **`GET`**: Retrieve a resource. (e.g., `GET /api/products/123` -> Get product with ID 123).
*   **`POST`**: Create a new resource. (e.g., `POST /api/products` -> Create a new product from the data in the request body).
*   **`PUT`**: Fully update/replace an existing resource. (e.g., `PUT /api/products/123` -> Replace product 123 with the data in the request body).
*   **`DELETE`**: Delete a resource. (e.g., `DELETE /api/products/123` -> Delete product with ID 123).
*   **`PATCH`**: Partially update a resource.

### Creating a RESTful Web Service in Java using Spring Boot
[[WJP Sessions 18, 19 & 20 - Spring Boot|Spring Boot]] makes creating REST APIs incredibly simple. The key is the `@RestController` annotation.

```java
import org.springframework.web.bind.annotation.*;
import java.util.List;

@RestController // This combines @Controller and @ResponseBody
@RequestMapping("/api/products") // Base URL for all methods in this controller
public class ProductController {

    // Assume we have a ProductService injected here
    private final ProductService productService;

    // ... constructor ...

    // GET /api/products
    @GetMapping
    public List<Product> getAllProducts() {
        return productService.findAll();
    }

    // GET /api/products/{id}
    @GetMapping("/{id}")
    public Product getProductById(@PathVariable Long id) {
        return productService.findById(id);
    }

    // POST /api/products
    @PostMapping
    public Product createProduct(@RequestBody Product product) {
        return productService.save(product);
    }

    // PUT /api/products/{id}
    @PutMapping("/{id}")
    public Product updateProduct(@PathVariable Long id, @RequestBody Product productDetails) {
        return productService.update(id, productDetails);
    }

    // DELETE /api/products/{id}
    @DeleteMapping("/{id}")
    public void deleteProduct(@PathVariable Long id) {
        productService.deleteById(id);
    }
}
```
**Key Annotations:**
*   **`@RestController`**: Marks the class as a controller where every method's return value is automatically serialized (e.g., to JSON) and sent as the response body.
*   **`@RequestMapping("/api/products")`**: Sets the base URL path for this controller.
*   **`@GetMapping`, `@PostMapping`, `@PutMapping`, `@DeleteMapping`**: Shorthand annotations for mapping specific HTTP methods to your controller actions.
*   **`@PathVariable`**: Binds a value from the URL path (e.g., the `{id}`) to a method parameter.
*   **`@RequestBody`**: Tells Spring to deserialize the JSON from the request body into a Java object.

### Consuming REST APIs
You often need your application to be a **client** that consumes another REST API.

*   **Using Postman:** Postman is a popular GUI tool for testing and interacting with APIs. You can easily construct `GET`, `POST`, `PUT`, `DELETE` requests, set headers, and view the response from the server.
*   **Using `RestTemplate` (Spring):** `RestTemplate` is Spring's classic, synchronous template for making HTTP requests from one service to another.
    ```java
    // Example of using RestTemplate
    RestTemplate restTemplate = new RestTemplate();
    String url = "http://api.example.com/products/123";
    Product product = restTemplate.getForObject(url, Product.class);
    ```
    *(Note: In modern Spring, the preferred way is to use the asynchronous `WebClient`)*.

---

### Topic Summary & Revision

*   **Web Service:** A standard way for applications to communicate over the web.
*   **SOAP vs. REST:** SOAP is a formal, XML-based protocol. REST is a lightweight, HTTP-based architectural style that typically uses JSON. REST is the modern standard.
*   **REST Principles:** Based on resources identified by URIs, manipulated via standard HTTP verbs (`GET`, `POST`, `PUT`, `DELETE`), and communicating with stateless, self-descriptive messages.
*   **Spring Boot for REST:** Use the `@RestController` annotation to easily create REST APIs. Spring Boot handles the JSON serialization/deserialization automatically.
*   **Key Annotations:** `@RequestMapping`, `@GetMapping`, `@PostMapping`, `@PathVariable`, `@RequestBody`.
*   **Consuming APIs:** Use tools like **Postman** for testing and classes like `RestTemplate` or `WebClient` to make HTTP requests from your Java application.

---

### MCQs for Exam Preparation

1.  **Which architectural style for web services is based on leveraging the standard features of the HTTP protocol itself?**
    - [ ] SOAP
    - [ ] WSDL
    - [ ] XML-RPC
    - [ ] REST
    <br>

2.  **In a RESTful API, which HTTP method is the most appropriate for retrieving a specific resource, like a user with ID 123, from the URL `/api/users/123`?**
    - [ ] `POST`
    - [ ] `GET`
    - [ ] `UPDATE`
    - [ ] `FETCH`
    <br>

3.  **What is the role of the `@RequestBody` annotation in a Spring `@RestController` method?**
    - [ ] It indicates that the method's return value should be written to the response body.
    - [ ] It binds the HTTP request body (e.g., a JSON payload) to a method parameter (e.g., a Java object).
    - [ ] It specifies that the method can only accept plain text in the request body.
    - [ ] It is used to get a parameter from the URL path.
    <br>

4.  **A RESTful API is described as "stateless". What does this mean?**
    - [ ] The API cannot store any data in a database.
    - [ ] The client does not need to send any data to the server.
    - [ ] The server does not store any client session information between requests. Each request must contain all information needed to process it.
    - [ ] The API does not use HTTP sessions or cookies.
    <br>

5.  **Which annotation in Spring combines the functionality of `@Controller` and `@ResponseBody`?**
    - [ ] `@Component`
    - [ ] `@Service`
    - [ ] `@RestController`
    - [ ] `@RequestMapping`
    <br>

6.  **To map an incoming `PUT` request for the URL `/api/items/42` to an action method, which annotation would you use on the method?**
    - [ ] `@GetMapping("/{id}")`
    - [ ] `@PostMapping("/42")`
    - [ ] `@PutMapping("/{id}")`
    - [ ] `@RequestMapping(value = "/42", method = RequestMethod.PUT)`
    <br>

7.  **What is the purpose of the `@PathVariable` annotation?**
    - [ ] To extract a value from the request body.
    - [ ] To extract a value from a query string parameter (e.g., `?name=John`).
    - [ ] To extract a value from the URL path itself (e.g., the `42` in `/items/42`).
    - [ ] To define the path for the entire controller.
    <br>

8.  **When comparing SOAP and REST, which statement is generally true?**
    - [ ] SOAP is more lightweight and flexible than REST.
    - [ ] REST typically uses XML, while SOAP typically uses JSON.
    - [ ] REST is an architectural style, while SOAP is a formal protocol with a strict standard.
    - [ ] SOAP relies only on the HTTP protocol.
    <br>

9.  **You are testing a REST API endpoint using Postman. To create a new user, you would set the HTTP method to `POST`, enter the URL, and where would you place the user's data (e.g., name, email) in JSON format?**
    - [ ] In the URL as query parameters.
    - [ ] In the "Headers" section.
    - [ ] In the "Body" section.
    - [ ] In the "Authorization" section.
    <br>

10. **In Spring, `RestTemplate` is a tool for:**
    - [ ] Creating RESTful servers.
    - [ ] Defining URL routing patterns.
    - [ ] Consuming RESTful web services from a client application.
    - [ ] Validating incoming JSON payloads.
    <br>

**Answer Key**
1.  **D**: ||REST is an architectural style, not a protocol, that is defined by a set of constraints that leverage the existing, well-understood features of HTTP, such as its verbs and status codes.||
2.  **B**: ||The GET verb is the standard, idempotent method for retrieving data. The URL /api/users/123 uniquely identifies the resource to be retrieved.||
3.  **B**: ||@RequestBody tells Spring's message converters (like Jackson) to deserialize the incoming HTTP request body (e.g., a JSON string) into an instance of the specified Java class parameter.||
4.  **C**: ||Statelessness is a key REST constraint. It improves scalability because any server in a cluster can handle any request from a client, as no session state is stored on a specific server.||
5.  **C**: ||@RestController is a convenience annotation that signifies that this controller is for a REST API. It implies that every method's return value should be serialized to the response body, which is the effect of @ResponseBody.||
6.  **C**: ||The @PutMapping annotation specifically maps HTTP PUT requests. The /{id} part is a path variable template that will match URLs like /api/items/42.||
7.  **C**: ||@PathVariable is used to bind a method parameter to a URI template variable. For a mapping like /{id}, @PathVariable Long id would bind the 42 from the URL to the id parameter.||
8.  **C**: ||This is a key distinction. SOAP is a rigid protocol with standards like WSDL for defining the service contract. REST is a more flexible set of architectural principles and constraints.||
9.  **C**: ||For POST and PUT requests, the data representing the resource to be created or updated is sent in the body of the HTTP request, typically in JSON format.||
10. **C**: ||RestTemplate (and the more modern WebClient) is a Spring component that simplifies the process of making HTTP requests from your application to consume external or internal REST APIs.||

---

### **Bonus Tips**

*   **REST is about Resources:** When designing a REST API, stop thinking in terms of "actions" and start thinking in terms of **"nouns" (resources)**. Your URLs should represent resources (`/products`, `/users/123`), and the HTTP methods (`GET`, `POST`, `PUT`, `DELETE`) should represent the actions you perform on those resources.
*   **Use HTTP Status Codes Correctly:** A well-designed REST API uses HTTP status codes to communicate the outcome of a request.
    *   `200 OK`: Standard success.
    *   `201 Created`: Successfully created a new resource (response to a `POST`).
    *   `204 No Content`: Success, but there is no data to return (e.g., after a `DELETE`).
    *   `400 Bad Request`: The client sent invalid data (e.g., validation error).
    *   `404 Not Found`: The requested resource does not exist.
    *   `500 Internal Server Error`: An unexpected error occurred on the server.
*   **Versioning is Important:** As your API evolves, you will need to introduce breaking changes. A good practice is to version your API (e.g., `/api/v1/products`, `/api/v2/products`). This allows older clients to continue using the stable `v1` while you develop new features in `v2`.
*   **`WebClient` over `RestTemplate`:** In modern, reactive Spring applications, `WebClient` is the preferred tool for consuming APIs. It is non-blocking and asynchronous, which makes it more efficient and scalable than the older, synchronous `RestTemplate`.

**🔗Links:** [[WJP Sessions 26 & 27 - Testing and Security in Spring]]