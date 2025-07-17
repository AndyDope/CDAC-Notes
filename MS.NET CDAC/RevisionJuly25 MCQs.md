### **Comprehensive MCQ Review: MS.Net Technologies (Hard)**

Practice these questions to challenge your in-depth understanding of .NET and C# concepts. For best results, attempt to answer them before checking the key.

---

### **Topic 1: .NET Architecture & C# Fundamentals (Sessions 1-3)**

1.  **Code that is executed under the control of the CLR, benefiting from services like garbage collection and type safety, is known as:**
    - [ ] Unmanaged Code
    - [ ] Native Code
    - [ ] Managed Code
    - [ ] Intermediate Language
    <br>

2.  **Which statement accurately describes the Just-In-Time (JIT) compilation process?**
    - [ ] The C# compiler converts source code directly to native code during the initial build.
    - [ ] The CLR interprets IL code line-by-line every time a method is run.
    - [ ] The CLR compiles a method's IL code into native machine code the first time the method is called, and caches the result for subsequent calls.
    - [ ] The entire assembly's IL is converted to native code when the application starts.
    <br>

3.  **An assembly manifest contains:**
    - [ ] The executable Intermediate Language (IL) code for the assembly's methods.
    - [ ] The source code of the C# files used to build the assembly.
    - [ ] Metadata describing the assembly itself, such as its name, version, culture, and a list of all referenced assemblies.
    - [ ] User-specific configuration settings for the application.
    <br>

4.  **What is the primary purpose of an AppDomain within a .NET process?**
    - [ ] To ensure every application runs in its own separate process.
    - [ ] To provide a security boundary and an isolated environment for running applications within a single process.
    - [ ] To manage the graphical user interface of an application.
    - [ ] To define the domain name for a web application.
    <br>

5.  **Which command-line utility is used to view the IL code, manifest, and metadata of a .NET assembly?**
    - [ ] `gacutil.exe`
    - [ ] `sn.exe`
    - [ ] `ildasm.exe`
    - [ ] `msbuild.exe`
    <br>

6.  **A C# property is defined as `public int Value { get; } = 10;`. What does this syntax create?**
    - [ ] A read-write property with a default value of 10.
    - [ ] A property that can only be set via reflection.
    - [ ] A truly immutable, read-only auto-property whose value can only be set at declaration or in a constructor.
    - [ ] A static property with the value 10.
    <br>

7.  **In a method call `UpdateUser(name: "John", id: 101);`, what C# feature is being used?**
    - [ ] Optional Parameters
    - [ ] Named Parameters
    - [ ] `ref` Parameters
    - [ ] Extension Methods
    <br>

8.  **Which of the following is a valid `char` literal in C#?**
    - [ ] `"c"`
    - [ ] `'c'`
    - [ ] `(char)"c"`
    - [ ] `'char'`
    <br>

9.  **What is the CTS (Common Type System) type that corresponds to the C# `float` keyword?**
    - [ ] `System.Double`
    - [ ] `System.Float`
    - [ ] `System.Single`
    - [ ] `System.Decimal`
    <br>

10. **A local function is defined inside another method. Which statement about it is TRUE?**
    - [ ] It must be declared `public` to be accessible.
    - [ ] It can access local variables and parameters of the outer method.
    - [ ] It can be overloaded.
    - [ ] A `static` local function can access instance members of the class.
    <br>

**Answer Key (1-10)**
1.  **Answer:** ||(C) Managed code is the term for any code whose execution is managed by a runtime environment like the .NET CLR, which provides benefits like garbage collection and security.||
2.  **Answer:** ||(C) JIT compilation provides the best of both worlds: platform independence (from IL) and performance (from native code). It compiles methods on-demand as they are needed.||
3.  **Answer:** ||(C) The assembly manifest is a crucial part of the assembly that contains all the metadata about the assembly's identity, version, and the types it contains.||
4.  **Answer:** ||(B) Application Domains provide isolation within a process, preventing one application from crashing or interfering with another application running in the same process.||
5.  **Answer:** ||(C) ildasm.exe (Intermediate Language Disassembler) is a developer tool included with Visual Studio that allows you to inspect the contents of a compiled .NET assembly.||
6.  **Answer:** ||(C) This syntax defines a read-only auto-property. The compiler generates a private, readonly backing field. The value can be set inline as shown, or within a constructor, but not from any other method.||
7.  **Answer:** ||(B) Named parameters allow you to pass arguments to a method by name instead of by position, which can improve code readability, especially for methods with many optional parameters.||
8.  **Answer:** ||(B) In C#, single quotes ' are used to define a single char literal, while double quotes " are used for string literals.||
9.  **Answer:** ||(C) The C# keyword float is an alias for the CTS type System.Single, which is a 32-bit single-precision floating-point number.||
10. **Answer:** ||(B) A key feature of local functions is that they form a closure, capturing the local variables of their containing method. They are implicitly private and cannot be overloaded.||
<br>

### **Topic 2: C# OOP & Advanced Types (Sessions 4-6)**

11. **A class is declared as `public sealed class Manager`. What is the implication of this declaration?**
    - [ ] The class cannot be instantiated.
    - [ ] The class can only contain `sealed` methods.
    - [ ] No other class can inherit from the `Manager` class.
    - [ ] The class is thread-safe by default.
    <br>

12. **What is the key difference between method hiding (using `new`) and method overriding (using `override`)?**
    - [ ] Hiding works on instance methods, while overriding works on static methods.
    - [ ] Hiding is resolved at compile-time (static binding), while overriding is resolved at run-time (late binding).
    - [ ] Only virtual methods can be hidden.
    - [ ] The `new` keyword is mandatory for hiding.
    <br>

13. **Why must a base class have a `virtual` destructor if it's part of an inheritance hierarchy where you might delete a derived object via a base class pointer?**
    - [ ] To prevent object slicing.
    - [ ] To ensure the derived class's destructor is called first, followed by the base class's destructor, preventing memory leaks.
    - [ ] To allow the destructor to be overridden with the `new` keyword.
    - [ ] To make the base class abstract.
    <br>

14. **When a class explicitly implements an interface method (e.g., `void IMyInterface.MyMethod()`), how can that method be called?**
    - [ ] Directly on an instance of the class (`myObject.MyMethod()`).
    - [ ] Only from within other methods of the same class.
    - [ ] Only on a reference variable that is of the interface type (`((IMyInterface)myObject).MyMethod()`).
    - [ ] It cannot be called.
    <br>

15. **A method is defined as `void ProcessData(out int result)`. Which statement is TRUE about the `result` argument when calling this method?**
    - [ ] The variable passed as `result` must be initialized before the call.
    - [ ] The method is not required to assign a value to `result`.
    - [ ] The `ProcessData` method MUST assign a value to `result` before it returns.
    - [ ] The `result` parameter is read-only inside the method.
    <br>

16. **What is the difference between a `struct` and a `class` in C#?**
    - [ ] `structs` are value types stored on the stack (for local variables), while classes are reference types stored on the heap.
    - [ ] `structs` can have multiple base classes.
    - [ ] `classes` do not have constructors.
    - [ ] `structs` cannot implement interfaces.
    <br>

17. **What does the C# `in` parameter modifier signify?**
    - [ ] The parameter is both an input and an output.
    - [ ] The parameter is passed by reference but cannot be modified by the called method.
    - [ ] The parameter must be an integer.
    - [ ] The parameter's value is provided by user input.
    <br>

18. **A `ValueTuple` like `(int Id, string Name)` is different from a `Tuple<int, string>` because:**
    - [ ] `ValueTuple` is a reference type, while `Tuple` is a value type.
    - [ ] `ValueTuple` is mutable and its elements can be named, while `Tuple` is immutable with item names like `Item1`, `Item2`.
    - [ ] `ValueTuple` has a limit of 2 items.
    - [ ] `Tuple` is a newer, more efficient implementation.
    <br>

19. **What is "unboxing"?**
    - [ ] The process of converting a reference type (like `object`) back to its original value type (like `int`).
    - [ ] A security feature to open a sandboxed assembly.
    - [ ] The process of creating a value type on the heap.
    - [ ] A compile-time error.
    <br>

20. **A jagged array is declared as `int[][] arr = new int[3][]`. What does this mean?**
    - [ ] It is a 3x3 rectangular array.
    - [ ] It is an array of 3 arrays, where each inner array can have a different size.
    - [ ] It is an array that can only store the number 3.
    - [ ] The declaration is invalid.
    <br>

**Answer Key (11-20)**
11. **Answer:** ||(C) The sealed keyword prevents a class from being used as a base class. This is a way to stop the inheritance chain.||
12. **Answer:** ||(B) Method hiding using new (or no keyword) is statically bound based on the reference type at compile time. Method overriding using virtual and override is dynamically bound based on the object's actual type at run time.||
13. **Answer:** ||(B) If the base destructor is not virtual, deleting a derived object through a base pointer will only call the base destructor, leaking any resources allocated by the derived class. A virtual destructor ensures the entire destruction chain is called correctly.||
14. **Answer:** ||(C) Explicit implementation hides the method from the class's public interface. To access it, you must first cast the object to the interface type it belongs to.||
15. **Answer:** ||(C) The contract of an out parameter requires the called method to assign a value to the variable before it returns. This is how methods can effectively "return" multiple values.||
16. **Answer:** ||(A) This is the fundamental difference. structs have value semantics (they are copied), while classes have reference semantics (the reference is copied). Structs cannot have inheritance.||
17. **Answer:** ||(B) The in modifier is a performance optimization. It passes the argument by reference (avoiding a potentially large copy for structs) but makes it read-only within the method to prevent modification.||
18. **Answer:** ||(B) ValueTuple, introduced in C# 7, is a much more flexible and efficient value type implementation. Its mutable, named fields (myTuple.Id) are a significant improvement over the read-only, generic myTuple.Item1 properties of the older System.Tuple reference type.||
19. **Answer:** ||(A) Unboxing is the explicit cast required to retrieve a value type that has been stored inside a reference type object on the heap. It can throw an InvalidCastException if the underlying type is not what you expect.||
20. **Answer:** ||(B) A jagged array is an "array of arrays." The outer array has a fixed size (3 in this case), but each of the inner arrays can be initialized with a different length, creating a ragged or jagged structure.||
<br>

### **Topic 3: Generics, Collections, Delegates, LINQ & Exceptions (Sessions 7-10)**

21. **What is the difference between `ICollection<T>` and `IList<T>`?**
    - [ ] `IList<T>` provides access to elements by index, while `ICollection<T>` does not.
    - [ ] `ICollection<T>` is read-only.
    - [ ] `IList<T>` cannot contain duplicate elements.
    - [ ] `ICollection<T>` is older and non-generic.
    <br>

22. **What does the `yield return` statement in a C# method do?**
    - [ ] It returns the entire collection at once.
    - [ ] It creates a state machine that allows the method to return multiple values over time, one at a time, without storing the entire sequence in memory.
    - [ ] It is a synonym for a simple `return` statement.
    - [ ] It yields control of the thread to another process.
    <br>

23. **Which generic delegate is defined as `public delegate bool Predicate<in T>(T obj);` and is used for methods that check a condition?**
    - [ ] `Action<T>`
    - [ ] `Func<T, bool>`
    - [ ] `Comparison<T>`
    - [ ] `Predicate<T>`
    <br>

24. **In exception handling, which `catch` block will be executed first?**
    ```csharp
    try { ... }
    catch (Exception ex) { ... }
    catch (ArgumentNullException ex) { ... }
    ```
    - [ ] The `ArgumentNullException` block.
    - [ ] The `Exception` block.
    - [ ] Neither, it will cause a compilation error.
    - [ ] It depends on the type of exception thrown.
    <br>

25. **What is "deferred execution" in LINQ?**
    - [ ] The LINQ query is executed on a separate thread.
    - [ ] The LINQ query is not executed when it is defined, but rather when the results are actually enumerated (e.g., in a `foreach` loop or by calling `.ToList()`).
    - [ ] The query execution is delayed by a specified amount of time.
    - [ ] The query is executed by the database, not in the application.
    <br>

26. **Which of the following is NOT a LINQ Standard Query Operator?**
    - [ ] `Where`
    - [ ] `Select`
    - [ ] `ForEach`
    - [ ] `OrderBy`
    <br>

27. **A "partial method" must:**
    - [ ] Be declared in a partial class or struct, have a `void` return type, and its implementation is optional.
    - [ ] Return a partial result.
    - [ ] Be `public`.
    - [ ] Be defined in a static class.
    <br>

28. **How can an extension method be called?**
    - [ ] Only on an instance of the class it extends.
    - [ ] Either as an instance method on the extended type or as a static method on the class that defines it.
    - [ ] Only as a static method.
    - [ ] Only from within the same assembly.
    <br>

29. **What is the purpose of the `.AsParallel()` method in LINQ?**
    - [ ] To execute the query on a remote server.
    - [ ] To convert a LINQ query into a PLINQ (Parallel LINQ) query, enabling parallel execution on multi-core processors.
    - [ ] To make the query execution asynchronous.
    - [ ] To order the results in parallel.
    <br>

30. **What happens if an exception is thrown and there is no matching `catch` block in the entire call stack?**
    - [ ] The exception is ignored, and the program continues.
    - [ ] The program terminates.
    - [ ] The `finally` blocks are not executed.
    - [ ] The system automatically retries the operation.
    <br>

**Answer Key (21-30)**
21. **Answer:** ||(A) ICollection\<T> defines basic collection functionality like Add, Remove, Count. IList\<T> inherits from ICollection\<T> and adds the ability to manage elements by an integer index, with methods like Insert, RemoveAt, and an indexer this[int].||
22. **Answer:** ||(B) yield return is used to implement iterators. The compiler generates a state machine behind the scenes. This allows you to write a method that "yields" values one by one without having to build a complete collection in memory first, which is very efficient for large sequences.||
23. **Answer:** ||(D) The Predicate\<T> delegate is specifically designed to represent a method that takes a single parameter and returns a boolean, indicating whether the item satisfies a certain condition. It's commonly used in methods like List\<T>.FindAll().||
24. **Answer:** ||(C) This code will not compile. C# requires that catch blocks be ordered from most specific to most general. Since ArgumentNullException derives from Exception, the more general Exception block would always catch it first, making the ArgumentNullException block unreachable code.||
25. **Answer:** ||(B) This is a core feature of LINQ. It allows you to build up a complex query by chaining operators. The query is only executed when the results are requested, allowing for more efficient processing, especially with databases.||
26. **Answer:** ||(C) ForEach is a method on the List\<T> class, but it is not a standard LINQ query operator. To perform an action on each item in a LINQ query, you would typically use a foreach loop after the query has executed.||
27. **Answer:** ||(A) Partial methods provide a hook for customization. The defining part is created in one partial class file. If an implementing part is not provided in another file, the compiler simply removes the method call and the definition entirely.||
28. **Answer:** ||(B) While it's designed to look like an instance method (e.g., myString.WordCount()), it is fundamentally a static method and can also be called directly: StringHelper.WordCount(myString).||
29. **Answer:** ||(B) PLINQ provides a simple way to introduce data parallelism into your applications. By adding .AsParallel(), you request that the runtime attempt to execute the subsequent query operators on different parts of the source collection simultaneously.||
30. **Answer:** ||(B) If an exception is not caught anywhere, it becomes an unhandled exception, which will cause the .NET runtime to terminate the application.||
<br>

### **Topic 4: Threading, I/O & Advanced .NET (Sessions 11-12)**

31. **What is a "shared assembly" in the .NET Framework?**
    - [ ] An assembly that can be used by multiple threads simultaneously.
    - [ ] An assembly that is signed with a strong name and installed in the Global Assembly Cache (GAC).
    - [ ] An assembly that is shared over a network drive.
    - [ ] A project type in Visual Studio.
    <br>

32. **What is the purpose of the `lock` statement in C#?**
    - [ ] To prevent an object from being garbage collected.
    - [ ] To make a class `sealed`.
    - [ ] To ensure that a block of code is executed by only one thread at a time, providing mutual exclusion.
    - [ ] To lock a file on the file system.
    <br>

33. **What is a "race condition"?**
    - [ ] When two threads are competing to finish first.
    - [ ] An error condition where the outcome of an operation depends on the unpredictable timing of concurrent threads accessing a shared resource.
    - [ ] A situation where a thread is blocked indefinitely.
    - [ ] When a thread runs faster than the main application thread.
    <br>

34. **In the Task Parallel Library (TPL), what is the primary difference between `Task.Run()` and `new Task()`?**
    - [ ] `Task.Run()` can accept parameters, while `new Task()` cannot.
    - [ ] `Task.Run()` automatically starts the task on a `ThreadPool` thread, while `new Task()` only creates the task object, which must be started manually with `.Start()`.
    - [ ] `new Task()` is for CPU-bound work, while `Task.Run()` is for I/O-bound work.
    - [ ] There is no difference.
    <br>

35. **The `Interlocked` class provides methods that are:**
    - [ ] Used to lock regions of code.
    - [ ] Atomic operations for simple numeric types.
    - [ ] Used for inter-process communication.
    - [ ] A way to pause and resume threads.
    <br>

36. **When using `async` and `await`, what does the `await` keyword do at a technical level?**
    - [ ] It blocks the current thread until the awaited task completes.
    - [ ] It configures a callback on the awaited task and immediately returns control to the caller, freeing up the thread.
    - [ ] It moves the execution to a background UI thread.
    - [ ] It cancels the asynchronous operation.
    <br>

37. **What is the primary benefit of using asynchronous I/O (e.g., `File.ReadAllTextAsync`) in a UI application?**
    - [ ] It makes the file read operation faster.
    - [ ] It prevents the user interface from freezing while waiting for the I/O operation to complete.
    - [ ] It uses less memory than synchronous I/O.
    - [ ] It automatically retries the operation if it fails.
    <br>

### **Topic 5: ASP.NET Core MVC (Sessions 13-19)**

38. **In the MVC pattern, what is the primary responsibility of the View?**
    - [ ] To handle business logic and data access.
    - [ ] To handle incoming HTTP requests.
    - [ ] To present data to the user and send user commands to the Controller.
    - [ ] To manage application state.
    <br>

39. **What is "convention-over-configuration" in ASP.NET Core MVC?**
    - [ ] The principle that requires all configuration to be explicitly defined in code.
    - [ ] A design paradigm where the framework makes assumptions about names and locations (e.g., a controller named `HomeController` will use views in the `Views/Home` folder) to reduce the need for explicit configuration.
    - [ ] A set of naming conventions for database tables.
    - [ ] A requirement to use conventional routing instead of attribute routing.
    <br>

40. **What is the role of `_ViewStart.cshtml`?**
    - [ ] It is the main view for the home page.
    - [ ] It is a partial view that is included in all other views.
    - [ ] It contains code that is executed before the code in any individual view in the same directory and its subdirectories.
    - [ ] It is used to declare model types for all views.
    <br>

**Answer Key (31-40)**
31. **Answer:** ||(B) A shared assembly is designed to be used by multiple applications on a machine. To avoid conflicts, it must have a unique strong name signature and is registered in the GAC.||
32. **Answer:** ||(C) The lock(object) statement acquires a mutual-exclusion lock for a given object. Only the thread that holds the lock can enter the code block. Other threads that try to enter will be blocked until the lock is released. This prevents race conditions.||
33. **Answer:** ||(B) A race condition occurs when the correctness of a program depends on the sequence or timing of threads. For example, if two threads execute count++ at the same time, the final result could be incorrect due to the interleaving of read-modify-write operations.||
34. **Answer:** ||(B) Task.Run() is a convenient shortcut that creates and starts a task on the thread pool in one step. Using new Task() separates the creation of the task object from its execution.||
35. **Answer:** ||(B) The Interlocked class provides static methods like Increment, Decrement, and Add that are guaranteed to be atomic, making them a highly efficient way to perform simple thread-safe updates on numeric variables without using a full lock.||
36. **Answer:** ||(B) This is the key to non-blocking asynchrony. The compiler transforms the await call into a state machine. It attaches a continuation (a callback) to the task and then immediately returns the thread to the thread pool to do other work. When the task completes, the continuation is scheduled to run.||
37. **Answer:** ||(B) In a UI application, long-running operations on the UI thread will cause the application to freeze and become unresponsive. Asynchronous I/O offloads the waiting period from the UI thread, keeping the application responsive.||
38. **Answer:** ||(C) The View is responsible for the presentation layer. It receives data from the Controller (via a Model or ViewModel) and renders the HTML markup for the user.||
39. **Answer:** ||(B) MVC frameworks rely heavily on conventions to simplify development. By naming your controllers and views in a standard way, the framework can automatically wire them up without requiring you to write explicit mapping code.||
40. **Answer:** ||(C) The _ViewStart.cshtml file is a powerful mechanism for defining common logic for a set of views. It is typically used to set the default Layout page for all views in a folder.||
<br>

### **Topic 6: Entity Framework, Web API & React Integration (Sessions 19-28)**

41. **In Entity Framework, what does a `DbSet<T>` property on a `DbContext` represent?**
    - [ ] A single entity object.
    - [ ] The database connection string.
    - [ ] A collection of entities in memory that can be queried, representing a table in the database.
    - [ ] A stored procedure or function.
    <br>

42. **What is the purpose of the `[ApiController]` attribute in an ASP.NET Core Web API controller?**
    - [ ] It enables routing for the controller.
    - [ ] It enables a set of opinionated behaviors that make building APIs more convenient, such as automatic model validation and HTTP 400 responses.
    - [ ] It specifies that the controller can only return JSON.
    - [ ] It converts the controller to a minimal API.
    <br>

43. **In a RESTful API, sending a `DELETE` request to `/api/products/123` is expected to:**
    - [ ] Retrieve the product with ID 123.
    - [ ] Update the product with ID 123.
    - [ ] Create a new product with ID 123.
    - [ ] Delete the product with ID 123.
    <br>

44. **What is the purpose of `_context.SaveChangesAsync()` in Entity Framework Core?**
    - [ ] It saves all tracked changes (inserts, updates, deletes) to the database in a single transaction asynchronously.
    - [ ] It only saves changes to a specific table.
    - [ ] It is a read-only operation.
    - [ ] It reloads all entities from the database.
    <br>

45. **Which is a primary reason to use a ViewModel instead of passing a domain model directly to an MVC View?**
    - [ ] ViewModels are generally faster than domain models.
    - [ ] To shape data specifically for the UI's needs and to prevent over-posting security vulnerabilities.
    - [ ] Domain models cannot be used with Razor syntax.
    - [ ] ViewModels can be stored in `ViewBag`.
    <br>

46. **How does Entity Framework's "Code-First" approach handle database schema updates?**
    - [ ] The database must be dropped and recreated manually.
    - [ ] Through a visual designer in Visual Studio.
    - [ ] Through "Migrations," which are code-based scripts that apply incremental changes to the schema.
    - [ ] It automatically updates the schema at runtime.
    <br>

47. **What does configuring CORS (Cross-Origin Resource Sharing) on a Web API enable?**
    - [ ] It allows the API to be called by multiple threads simultaneously.
    - [ ] It encrypts the data sent between the client and the server.
    - [ ] It allows a web browser on a different domain to make requests to the API, bypassing the Same-Origin Policy.
    - [ ] It enables API versioning.
    <br>

48. **In an ASP.NET Core application integrated with React, what is the typical role of the ASP.NET Core part in production?**
    - [ ] To transpile the JSX code.
    - [ ] To only serve the initial `index.html` and act as a backend API for the React single-page application.
    - [ ] To manage the state of the React components on the server.
    - [ ] It has no role in production; React is deployed independently.
    <br>

49. **In EF Core, what does the `Include()` method do in a LINQ query?**
    - [ ] It filters the results based on a condition.
    - [ ] It specifies related entities to be loaded along with the main entity, preventing lazy loading N+1 query problems.
    - [ ] It includes soft-deleted records in the query result.
    - [ ] It adds a new record to the database.
    <br>

50. **What is a key benefit of using Razor Pages over MVC for simple, page-focused scenarios?**
    - [ ] Razor Pages do not require a web server.
    - [ ] It more tightly couples the page's markup (`.cshtml`) and its server-side logic (`.cshtml.cs`) together, which can be simpler for page-based apps.
    - [ ] It uses a different programming language than C#.
    - [ ] It is better for creating RESTful APIs.
    <br>

**Answer Key (41-50)**
41. **Answer:** ||(C) A DbSet\<T> represents the collection of all entities of type T in the context. It acts as the entry point for creating LINQ queries against that table.||
42. **Answer:** ||(B) The [ApiController] attribute enables several helpful conventions for APIs, such as inferring binding sources for parameters and automatically triggering a 400 Bad Request response if ModelState is invalid, saving boilerplate code.||
43. **Answer:** ||(D) This follows the principles of REST (Representational State Transfer). The HTTP verb (DELETE) indicates the action, and the URL (/api/products/123) identifies the resource to act upon.||
44. **Answer:** ||(A) Entity Framework uses a "Unit of Work" pattern. You can make multiple changes to your entities in memory, and they are not sent to the database until you call SaveChanges() or SaveChangesAsync(), at which point they are executed within a single transaction.||
45. **Answer:** ||(B) A ViewModel is tailored for the UI, so you only expose the data that is needed. This prevents a malicious user from "over-posting" and binding values to sensitive properties on your domain model that were not present on the form.||
46. **Answer:** ||(C) Migrations create a history of schema changes that can be tracked in source control. You can apply migrations to update a database to the latest version or revert it to a previous version.||
47. **Answer:** ||(C) Browsers enforce the Same-Origin Policy for security. CORS is a standard mechanism where a server can explicitly tell a browser, via HTTP headers, that it is safe to allow requests from other specified origins.||
48. **Answer:** ||(B) In a typical modern web architecture, the backend (ASP.NET Core) is responsible for serving the initial static assets of the SPA (like the main HTML, CSS, and JS bundles) and then acts as the data API that the client-side React app communicates with.||
49. **Answer:** ||(B) This is for "eager loading." If you query for a Blog and know you will need its Posts, using .Include(b => b.Posts) tells EF to generate a single query with a JOIN to fetch both blogs and their related posts, which is more efficient than lazy loading them later.||
50. **Answer:** ||(B) MVC is great for complex applications with many actions related to a single model. Razor Pages are architected around the page itself. The logic and the view are tightly coupled, which can be a simpler and more direct approach for applications that are more page-centric, like a settings dashboard or a contact form.||