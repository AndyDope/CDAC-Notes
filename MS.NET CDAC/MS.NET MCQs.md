### **Comprehensive MCQ Review: MS.Net Technologies (Hard)**

Practice these questions to challenge your in-depth understanding of web development concepts. For best results, attempt to answer them before checking the key.

---

### **Topic 1: .NET Architecture & C# Fundamentals (Sessions 1-3)**

1.  **What is the role of the Common Language Runtime (CLR) in the .NET ecosystem?**
    - [ ] It compiles C# source code directly into native machine code.
    - [ ] It manages the execution of .NET programs by handling memory management, security, and JIT compilation.
    - [ ] It provides a standard set of base class libraries for developers to use.
    - [ ] It translates C# code into other languages like VB.NET.
    <br>

2.  **A C# method is defined as `void Calculate(int x, int y = 10, int z = 20)`. Which of the following method calls is INVALID?**
    - [ ] `Calculate(5);`
    - [ ] `Calculate(5, 15);`
    - [ ] `Calculate(5, z: 30);`
    - [ ] `Calculate(z: 30, 5);`
    <br>

3.  **What is the key difference between "Managed Code" and "Unmanaged Code" in .NET?**
    - [ ] Managed code is written in C#, while unmanaged code is written in C++.
    - [ ] Managed code's execution lifecycle (memory, security) is managed by the CLR, while unmanaged code runs outside the CLR's control.
    - [ ] Managed code runs faster than unmanaged code.
    - [ ] Managed code is compiled to IL, while unmanaged code is interpreted.
    <br>

4.  **In C#, what is the purpose of an "assembly"?**
    - [ ] It is a text file containing C# source code.
    - [ ] It is a unit of deployment and versioning, typically a DLL or EXE file, containing IL code and metadata.
    - [ ] It is another name for a namespace.
    - [ ] It is a special type of class used for memory management.
    <br>

5.  **A C# property is defined as `public int Value { get; private set; }`. What does this mean?**
    - [ ] The property can be read from anywhere, but can only be set from within the same class.
    - [ ] The property can only be set in the constructor.
    - [ ] The property is read-only and can never be set.
    - [ ] The `set` accessor is accessible to derived classes.
    <br>

6.  **What does the `params` keyword in a C# method signature allow?**
    - [ ] It allows the method to accept a variable number of arguments of a specific type as an array.
    - [ ] It specifies that a parameter is passed by reference.
    - [ ] It defines an optional parameter with a default value.
    - [ ] It indicates that the parameter is a static variable.
    <br>

7.  **What is the primary function of the Common Type System (CTS) in .NET?**
    - [ ] To manage the memory heap and stack.
    - [ ] To provide a common set of data types that all .NET languages can understand, ensuring language interoperability.
    - [ ] To compile Intermediate Language (IL) into native code.
    - [ ] To enforce security policies on an assembly.
    <br>

8.  **What is the difference between `.NET Framework` and `.NET Core` (now just `.NET`)?**
    - [ ] `.NET Framework` is open source, while `.NET Core` is proprietary.
    - [ ] `.NET Framework` is cross-platform, while `.NET Core` is Windows-only.
    - [ ] `.NET Core` is the modern, cross-platform, and open-source successor to the Windows-only `.NET Framework`.
    - [ ] There is no difference; `.NET Core` is just a new name for `.NET Framework`.
    <br>

9.  **The JIT (Just-In-Time) compiler in the CLR is responsible for:**
    - [ ] Compiling C# source code into Intermediate Language (IL).
    - [ ] Compiling IL code into native machine code at runtime, just before it is executed.
    - [ ] Managing memory and garbage collection.
    - [ ] Verifying the type safety of the code.
    <br>

10. **A C# `readonly` field can be assigned a value:**
    - [ ] At any time, but only once.
    - [ ] Only within a `static` method.
    - [ ] Only at the time of declaration or within the constructor of the same class.
    - [ ] Never; it must be a compile-time constant.
    <br>

**Answer Key (1-10)**
1. **Answer:** ||(B) The CLR is the execution engine of .NET. It takes the compiled IL code and manages its execution, providing services like garbage collection, security verification, and JIT compilation to native code.||
2. **Answer:** ||(D) Positional arguments (like 5) cannot follow named arguments (like z: 30). Once you start using named arguments, all subsequent arguments must also be named.||
3. **Answer:** ||(B) This is the core distinction. Managed code benefits from the CLR's services. Unmanaged code, like a C++ library called via P/Invoke, is responsible for its own memory management and does not have the same safety guarantees.||
4. **Answer:** ||(B) An assembly is the fundamental building block of a .NET application. It's the logical and physical unit that contains compiled code (IL), a manifest with metadata, and other resources.||
5. **Answer:** ||(A) A private set accessor means the setter can only be called by code within the containing class, effectively making the property read-only to the outside world but writeable internally.||
6. **Answer:** ||(A) The params keyword allows a method to be called with a variable number of arguments. Those arguments are collected into an array within the method. It must be the last parameter in the method signature.||
7. **Answer:** ||(B) The CTS defines a standard set of types (like Int32, String, etc.) that are used by all .NET languages. This ensures that a component written in C# can seamlessly interact with a component written in VB.NET or F#.||
8. **Answer:** ||(C) .NET Core was created as a modular, high-performance, open-source, and cross-platform (Windows, macOS, Linux) re-imagination of .NET. It has since evolved into the main .NET platform, simply called .NET 5, .NET 6, etc.||
9. **Answer:** ||(B) The C# compiler (Roslyn) compiles source to IL. The JIT compiler, which is part of the CLR, compiles that IL into native code specific to the machine's architecture at runtime, which allows for platform independence.||
10. **Answer:** ||(C) A readonly field provides instance-level immutability. Its value can be set dynamically, but only during its declaration or within a constructor. After the object is constructed, it cannot be changed. A const must be a compile-time constant.||
<br>

### **Topic 2: C# OOP and Advanced Language Features (Sessions 4-6)**

11. **A method in a base class is marked with `virtual`. A method with the same signature in a derived class is marked with `new`. What happens when this method is called on a derived object through a base class reference?**
    - [ ] The base class version of the method is called.
    - [ ] The derived class version of the method is called.
    - [ ] It results in a compilation error.
    - [ ] A runtime exception is thrown.
    <br>

12. **In C#, what is the difference between `ref` and `out` parameters?**
    - [ ] `ref` is for value types, `out` is for reference types.
    - [ ] A variable passed as `ref` must be initialized before the call, while a variable passed as `out` does not.
    - [ ] `ref` passes a copy, while `out` passes a pointer.
    - [ ] They are functionally identical.
    <br>

13. **What is "boxing" in the context of .NET?**
    - [ ] Placing a value type into a secure container.
    - [ ] The process of converting a value type (like `int`) to a reference type (`object`).
    - [ ] The process of converting a reference type to a value type.
    - [ ] A technique for creating read-only types.
    <br>

14. **When should you prefer using a `struct` over a `class` in C#?**
    - [ ] When you need to use inheritance.
    - [ ] When the type represents a single, small, immutable value, and you expect to create many instances of it.
    - [ ] When you need a type that can be `null`.
    - [ ] Always, because structs are more performant.
    <br>

15. **A C# `abstract` class can:**
    - [ ] Be instantiated directly using the `new` keyword.
    - [ ] Contain both abstract methods (without a body) and regular, implemented methods.
    - [ ] Inherit from multiple other abstract classes.
    - [ ] Not have a constructor.
    <br>

16. **What is explicit interface implementation used for?**
    - [ ] To hide an interface member from the class's public API, making it accessible only when the object is cast to the interface type.
    - [ ] To make the implementation of an interface optional.
    - [ ] To allow a class to implement multiple interfaces.
    - [ ] To provide a `public` implementation of an interface method.
    <br>

17. **What is true about `static` constructors in C#?**
    - [ ] They are called every time an object of the class is created.
    - [ ] They can accept parameters.
    - [ ] They are called automatically before the first instance is created or any static members are referenced, and are used to initialize static fields.
    - [ ] They must be declared `public`.
    <br>

18. **A `switch` expression (introduced in C# 8.0) differs from a `switch` statement because it:**
    - [ ] Cannot have a `default` case.
    - [ ] Uses `=>` syntax and must produce a value.
    - [ ] Can only be used with integer types.
    - [ ] Does not support pattern matching.
    <br>

19. **What is the purpose of the `IDisposable` interface and the `using` statement?**
    - [ ] To manage memory for large objects.
    - [ ] To provide a standard mechanism for releasing unmanaged resources (like file handles or database connections) deterministically.
    - [ ] To make a class serializable.
    - [ ] To dispose of objects on a background thread.
    <br>

20. **What does the `??` operator (null-coalescing operator) do?**
    - [ ] It throws a `NullReferenceException` if the left-hand operand is null.
    - [ ] It returns the left-hand operand if it is not null; otherwise, it returns the right-hand operand.
    - [ ] It checks if two nullable types are equal.
    - [ ] It converts a nullable type to its underlying value.
    <br>

**Answer Key (11-20)**
11. **Answer:** ||(A) The new keyword explicitly breaks the polymorphic chain. It hides the base class method. Because the call is made through a base class reference, the compiler resolves the call to the base class version at compile-time. The override keyword is required to maintain polymorphic behavior.||
12. **Answer:** ||(B) This is a key difference. A variable passed to a ref parameter must be assigned a value before the call. An out parameter is designed for the method to pass a value out, so the variable passed to it does not need to be initialized beforehand, but it must be assigned a value inside the method.||
13. **Answer:** ||(B) Boxing is the process of wrapping a value type from the stack into a reference type object on the heap. This allows value types to be used where an object is expected, such as in non-generic collections like ArrayList. The reverse process is unboxing.||
14. **Answer:** ||(B) Structs are value types best suited for small, data-centric structures that behave like primitive types (e.g., Point, ComplexNumber). Their value semantics and stack allocation can be more efficient in tight loops, but they lack key features of classes like inheritance.||
15. **Answer:** ||(B) This is a primary feature of abstract classes. They act as a base class that provides some common implemented functionality while forcing derived classes to provide their own implementation for the abstract parts.||
16. **Answer:** ||(A) This is useful when a class implements two interfaces that have a method with the same name and signature. Explicit implementation allows the class to provide a separate implementation for each interface's method.||
17. **Answer:** ||(C) A static constructor is guaranteed to run at most once per AppDomain. It is parameterless and has no access modifiers. It's the perfect place to initialize static data that might require some logic.||
18. **Answer:** ||(B) The switch expression is a more functional and concise alternative to the statement. It uses a pattern-matching approach (variable switch { pattern => result, ... }) and must be exhaustive, meaning every possible input must be handled.||
19. **Answer:** ||(B) The using statement (using (var conn = new SqlConnection()) { ... }) is syntactic sugar that guarantees the .Dispose() method of an IDisposable object is called, even if an exception occurs. This is the standard way to ensure unmanaged resources are cleaned up promptly.||
20. **Answer:** ||(B) It's a convenient shortcut for providing a default value for a nullable type. string name = suppliedName ?? "Default Name"; assigns "Default Name" to name only if suppliedName is null.||
<br>
### **Topic 3: Generics, Collections, Delegates & LINQ (Sessions 7-10)**

21. **A method signature is `void ProcessItems<T>(List<T> items) where T : IComparable<T>`. What does the "generic constraint" mean?**
    - [ ] The type `T` must be a class.
    - [ ] The type `T` must have a method named `Compare`.
    - [ ] Any type `T` used with this method must implement the `IComparable\<T>` interface.
    - [ ] The method can only accept comparable integers.
    <br>

22. **What is the key difference between `Action<T>` and `Func<T, TResult>`?**
    - [ ] `Action` is for value types, `Func` is for reference types.
    - [ ] `Action` delegates represent methods that do not return a value (`void`), while `Func` delegates represent methods that return a value.
    - [ ] `Action` can only take one parameter, while `Func` can take multiple.
    - [ ] `Func` is a newer version of `Action`.
    <br>

23. **What is the output of this LINQ query?**
    ```csharp
    var numbers = new List<int> { 1, 2, 3, 4, 5 };
    var result = numbers.Where(n => n % 2 == 0).Select(n => n * 2);
    numbers.Add(6);
    foreach(var num in result) { Console.Write(num + " "); }
    ```
    - [ ] 4 8
    - [ ] 4 8 12
    - [ ] 4 8 10
    - [ ] The code throws an exception.
    <br>

24. **Which LINQ operator is used to project each element of a sequence into a new form?**
    - [ ] `Where`
    - [ ] `Select`
    - [ ] `OrderBy`
    - [ ] `GroupBy`
    <br>

25. **What is an "anonymous type" in C#?**
    - [ ] A class with no name that can be defined on the fly.
    - [ ] A class that has no methods.
    - [ ] A type that can hold any kind of data.
    - [ ] A class declared with the `dynamic` keyword.
    <br>

26. **Which of the following data structures from `System.Collections.Generic` provides O(1) average time complexity for add, remove, and contains operations?**
    - [ ] `List<T>`
    - [ ] `Queue<T>`
    - [ ] `SortedDictionary<TKey, TValue>`
    - [ ] `HashSet<T>`
    <br>

27. **What is the purpose of PLINQ (Parallel LINQ)?**
    - [ ] To make LINQ queries compatible with SQL databases.
    - [ ] To automatically parallelize the execution of a LINQ to Objects query across multiple CPU cores.
    - [ ] To provide a graphical interface for building LINQ queries.
    - [ ] To execute LINQ queries on a remote server.
    <br>

28. **What does the `yield return` statement do inside a method?**
    - [ ] It returns the entire collection at once.
    - [ ] It creates a state machine that allows the method to return multiple values over time, one at a time, without storing the entire sequence in memory.
    - [ ] It is a synonym for a simple `return` statement.
    - [ ] It yields control of the thread to another process.
    <br>

29. **What is a "multicast delegate"?**
    - [ ] A delegate that can only point to static methods.
    - [ ] A delegate that can hold references to and invoke multiple methods with the same signature.
    - [ ] A delegate that is used for network communication.
    - [ ] A delegate that returns multiple values.
    <br>

30. **Lambda expressions in C# provide a concise way to represent:**
    - [ ] A class definition.
    - [ ] An anonymous method.
    - [ ] A generic type constraint.
    - [ ] A project reference.
    <br>

**Answer Key (21-30)**
21. **Answer:** ||(C) The where T : ... clause adds constraints to the generic type parameter T. In this case, it ensures that any type passed as T must implement the IComparable\<T> interface, which guarantees it will have a .CompareTo() method.||
22. **Answer:** ||(B) This is the core distinction. Action delegates are for methods with a void return type. Func delegates are for methods that return a value. The last type parameter in a Func declaration is always the return type.||
23. **Answer:** ||(B) This demonstrates deferred execution. The result query is not executed until the foreach loop begins. At that point, the numbers list contains 6. The Where filter finds 2, 4, and 6. The Select operation transforms them into 4, 8, and 12.||
24. **Answer:** ||(B) Select is the LINQ equivalent of the projection operation. It takes each element from the source sequence and applies a transformation function to it, creating a new sequence of the transformed elements.||
25. **Answer:** ||(A) Anonymous types are created on the fly, typically in a LINQ Select statement, to create an object with a specific set of properties without having to formally define a class for it. Example: select new { Name = p.Name, Price = p.Price }.||
26. **Answer:** ||(D) HashSet\<T> is based on a hash table data structure, which provides constant-time average complexity for add, remove, and contains operations.||
27. **Answer:** ||(B) By simply adding .AsParallel() to a LINQ query, PLINQ attempts to partition the source data and process the query on multiple threads simultaneously, potentially providing a significant performance boost on multi-core machines.||
28. **Answer:** ||(B) yield return is used to implement iterators. The compiler generates a state machine behind the scenes. This allows you to write a method that "yields" values one by one without having to build a complete collection in memory first, which is very efficient for large sequences.||
29. **Answer:** ||(B) Delegates in C# are inherently multicast. You can use the + or += operator to combine multiple methods into a single delegate instance. When the delegate is invoked, all methods in its invocation list are called in order.||
30. **Answer:** ||(B) A lambda expression (e.g., x => x * 2) is a shorthand syntax for creating an anonymous method or function. It is most commonly used with delegates and LINQ.||
<br>

### **Topic 4: Advanced C#, Threading & I/O (Sessions 11-12)**

31. **In a `try-catch-finally` block, when is the `finally` block executed?**
    - [ ] Only if an exception is thrown in the `try` block.
    - [ ] Only if no exception is thrown in the `try` block.
    - [ ] It is never executed if a `catch` block is present.
    - [ ] Always, regardless of whether an exception was thrown or caught.
    <br>

32. **What is an "extension method" in C#?**
    - [ ] A method that extends the functionality of a `sealed` class.
    - [ ] A static method in a static class that can be called as if it were an instance method of another type.
    - [ ] A method that can be added to a class at runtime.
    - [ ] An `override` of a base class method.
    <br>

33. **What is a "race condition" in multithreading?**
    - [ ] When two threads are competing to finish first.
    - [ ] An error condition where the outcome of an operation depends on the unpredictable timing of concurrent threads accessing a shared resource.
    - [ ] A situation where a thread is blocked indefinitely.
    - [ ] When a thread runs faster than the main application thread.
    <br>

34. **What is the purpose of the `lock` statement in C#?**
    - [ ] To prevent an object from being garbage collected.
    - [ ] To make a class `sealed`.
    - [ ] To ensure that a block of code is executed by only one thread at a time, providing mutual exclusion.
    - [ ] To lock a file on the file system.
    <br>

35. **The `async` and `await` keywords in C# are primarily used to:**
    - [ ] Make the program run faster by using more CPU cores.
    - [ ] Simplify asynchronous programming, making non-blocking code look and behave like synchronous code.
    - [ ] Encrypt data for secure communication.
    - [ ] Handle hardware interrupts.
    <br>

36. **What is Reflection in .NET used for?**
    - [ ] To improve the performance of graphical applications.
    - [ ] To inspect the metadata of assemblies, types, and members at runtime and dynamically invoke them.
    - [ ] To provide a reflection of the screen for screen-capture applications.
    - [ ] To automatically handle exceptions.
    <br>

37. **A "partial class" allows:**
    - [ ] A class to be defined across multiple source files.
    - [ ] A class to inherit from only part of a base class.
    - [ ] A class to be instantiated only partially.
    - [ ] A class to be both `static` and an instance class.
    <br>

### **Topic 5: ASP.NET Core MVC & ADO.NET (Sessions 13-19)**

38. **In the MVC pattern, what is the primary responsibility of the Controller?**
    - [ ] To render the user interface.
    - [ ] To contain the application's business logic and data.
    - [ ] To handle incoming user requests, interact with the model, and select a view to render.
    - [ ] To manage the database connection.
    <br>

39. **What is the purpose of "Routing" in an ASP.NET Core MVC application?**
    - [ ] To route data from the Model to the View.
    - [ ] To map incoming URL requests to a specific Controller and Action method.
    - [ ] To route database queries to the correct table.
    - [ ] To manage the flow of control between different Views.
    <br>

40. **What is the difference between `ViewBag` and `ViewData` in ASP.NET Core MVC?**
    - [ ] `ViewBag` is strongly typed, while `ViewData` is dynamic.
    - [ ] `ViewBag` is a dynamic wrapper around the `ViewData` dictionary, offering a different syntax for the same underlying data store.
    - [ ] `ViewData` can pass data from a Controller to a View, but `ViewBag` cannot.
    - [ ] `ViewData` persists for multiple requests, while `ViewBag` is for a single request.
    <br>

**Answer Key (31-40)**
31. **Answer:** ||(D) The finally block provides a mechanism to clean up resources (like closing a file or database connection) because it is guaranteed to execute after the try block, regardless of whether an exception occurred or which catch block was executed.||
32. **Answer:** ||(B) Extension methods provide a way to "add" new methods to existing types without creating a new derived type, recompiling, or otherwise modifying the original type. LINQ's query operators are implemented as extension methods on the IEnumerable\<T> type.||
33. **Answer:** ||(B) A race condition occurs when the correctness of a program depends on the sequence or timing of threads. For example, if two threads execute count++ at the same time, the final result could be incorrect due to the interleaving of read-modify-write operations.||
34. **Answer:** ||(C) The lock(object) statement acquires a mutual-exclusion lock for a given object. Only the thread that holds the lock can enter the code block. Other threads that try to enter will be blocked until the lock is released. This prevents race conditions.||
35. **Answer:** ||(B) async/await is syntactic sugar over the Task-based Asynchronous Pattern (TAP). It allows developers to write non-blocking I/O-bound code with the same linear structure as synchronous code, which significantly improves readability and maintainability.||
36. **Answer:** ||(B) Reflection provides a powerful "meta-programming" capability. It's used by frameworks for tasks like dependency injection, serialization, and by testing tools to invoke methods, all without knowing the types at compile time.||
37. **Answer:** ||(A) The partial keyword allows the definition of a single class, struct, or interface to be split across two or more .cs files. This is often used by code generators (like the WinForms designer) to separate machine-generated code from user-written code.||
38. **Answer:** ||(C) The Controller acts as the orchestrator. It receives the HTTP request, interprets the user's intent, calls upon the Model to fetch or update data, and then selects the appropriate View to send back as a response.||
39. **Answer:** ||(B) Routing is the middleware component that inspects the URL of an incoming request and uses a set of configured rules (the route table) to decide which controller and action method should handle that request.||
40. **Answer:** ||(B) Both are mechanisms for passing data from a controller to a view and share the same underlying dictionary. ViewData uses dictionary-style access (ViewData["Key"]), while ViewBag uses dynamic properties (ViewBag.Key), which can be more convenient but lacks compile-time checking.||
<br>

### **Topic 6: Entity Framework, Web API & React Integration (Sessions 19-28)**

41. **What is an Object-Relational Mapper (ORM) like Entity Framework?**
    - [ ] A tool for mapping database schemas to UML diagrams.
    - [ ] A framework that enables developers to work with a database using domain-specific objects and classes, instead of writing raw SQL queries.
    - [ ] A database server.
    - [ ] A language for querying object-oriented databases.
    <br>

42. **What is the "Code-First" approach in Entity Framework?**
    - [ ] Writing the database SQL scripts first, then generating the C# classes.
    - [ ] Designing the database in a visual designer first.
    - [ ] Writing the C# domain classes (POCOs) first, from which Entity Framework generates the database schema.
    - [ ] Prioritizing code readability over performance.
    <br>

43. **In a RESTful API, which HTTP verb is idempotent and used to *partially* update an existing resource?**
    - [ ] `POST`
    - [ ] `PATCH`
    - [ ] `PUT`
    - [ ] `UPDATE`
    <br>

44. **What is the purpose of "Database Migrations" in Entity Framework?**
    - [ ] To move a database from one server to another.
    - [ ] To provide a way to incrementally evolve the database schema over time as the model classes change, without losing data.
    - [ ] To migrate data from a SQL database to a NoSQL database.
    - [ ] To back up the database.
    <br>

45. **What is the key difference between `IEnumerable<T>` and `IQueryable<T>` in the context of LINQ and Entity Framework?**
    - [ ] `IEnumerable<T>` executes the query on the client-side (in-memory), while `IQueryable<T>` translates the query into SQL to be executed on the database server.
    - [ ] `IQueryable<T>` is for synchronous queries, while `IEnumerable<T>` is for asynchronous queries.
    - [ ] `IEnumerable<T>` supports deferred execution, while `IQueryable<T>` does not.
    - [ ] There is no significant difference.
    <br>

46. **What is the role of `_Layout.cshtml` in a standard ASP.NET Core MVC project?**
    - [ ] It is the main configuration file for the application.
    - [ ] It is the view for the home page.
    - [ ] It is a special view that serves as a template, defining the common layout (e.g., header, footer, navigation) for other views.
    - [ ] It contains all the C# models for the application.
    <br>

47. **A `Task` object in C# represents:**
    - [ ] A thread in the thread pool.
    - [ ] A value that will be available in the future.
    - [ ] An asynchronous operation.
    - [ ] A user interface task.
    <br>

48. **What is a "ViewModel" in an MVC application?**
    - [ ] A model that is bound to the view using `ViewBag`.
    - [ ] The base class for all view components.
    - [ ] A class specifically designed to hold the data required for a particular view, often combining properties from multiple domain models.
    - [ ] A model that contains validation logic only.
    <br>

49. **What is the difference between a "shared assembly" and a "private assembly" in the context of the older .NET Framework?**
    - [ ] A private assembly is encrypted, while a shared assembly is not.
    - [ ] A shared assembly is signed with a strong name and placed in the Global Assembly Cache (GAC) to be used by multiple applications. A private assembly is copied into each application's local directory.
    - [ ] A shared assembly is for web applications, a private one for desktop apps.
    - [ ] A shared assembly can be written in multiple languages.
    <br>

50. **When integrating React with an ASP.NET Core MVC backend, what is the typical data flow for fetching data?**
    - [ ] React components directly query the database.
    - [ ] The MVC Controller renders a view that includes the data as JavaScript variables.
    - [ ] React components make asynchronous `fetch` or `Axios` calls to a Web API endpoint exposed by an ASP.NET Core Controller.
    - [ ] ASP.NET Core pushes data to the React front-end using WebSockets.
    <br>

**Answer Key (41-50)**
41. **Answer:** ||(B) An ORM like Entity Framework abstracts the database interaction. Developers can write LINQ queries against C# objects (DbSet\<T>), and the ORM translates these into the appropriate SQL, executes them, and maps the results back to C# objects.||
42. **Answer:** ||(C) In the Code-First workflow, your C# classes are the "source of truth." You define your domain model using POCOs, and EF can then generate a database schema that matches this model, often using EF Migrations.||
43. **Answer:** ||(B) PUT is used to fully replace a resource and is idempotent. PATCH is designed for partial updates (e.g., only updating an item's price, not its name) and is not considered idempotent.||
44. **Answer:** ||(B) Migrations provide a source-controlled, step-by-step way to manage changes to your database schema. Each migration contains the code to both apply (Up) and revert (Down) a schema change, allowing for safe database evolution.||
45. **Answer:** ||(A) This is a critical distinction for performance. An IQueryable\<T> builds up an expression tree. When you chain LINQ methods, you are modifying the expression tree. Only when the query is executed is the entire tree translated into a single, efficient SQL query. An IEnumerable\<T> would pull the entire table into memory first and then perform the filtering and projection client-side.||
46. **Answer:** ||(C) The layout page allows you to define a consistent look and feel for your application. Other views then specify this layout and render their specific content within a designated section, typically by calling @RenderBody().||
47. **Answer:** ||(C) A Task (and Task\<T>) is the core object in the Task Parallel Library (TPL) that represents the promise of a future result from an asynchronous operation. await is used to consume this promise.||
48. **Answer:** ||(C) A ViewModel acts as a data container shaped specifically for the needs of a UI screen. It prevents passing complex domain models directly to the view and helps to flatten or combine data as needed for display.||
49. **Answer:** ||(B) This was a key concept for managing dependencies in the .NET Framework. The GAC was a central repository for versioned, shared libraries to avoid "DLL Hell." .NET Core and modern .NET largely moved away from the GAC model in favor of package-based dependency management (like NuGet).||
50. **Answer:** ||(C) This is the standard, decoupled architecture. The ASP.NET Core application exposes data via a RESTful Web API. The React front-end (running in the user's browser) acts as a client, making HTTP requests to these API endpoints to fetch and submit data.||