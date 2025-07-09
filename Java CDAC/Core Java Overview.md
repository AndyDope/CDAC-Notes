### **Java Overview**

This page provides a high-level summary of the essential concepts covered in the PG-DAC Java module, organized by session. Use it as a quick-recall cheat sheet before exams.

---

#### [[Java Session 1 - Introduction to Java|Session 1: Introduction to Java]]
*   **[[Java Session 1 - Introduction to Java#2. The Java Virtual Machine (JVM) Architecture|JVM (Java Virtual Machine)]]**: An abstract machine that enables Java to be platform-independent by executing platform-neutral bytecode.
*   **[[Java Session 1 - Introduction to Java#1. Introduction and Features of Java|WORA]]**: "Write Once, Run Anywhere" - Java's core philosophy.
*   **[[Java Session 1 - Introduction to Java#3. JDK, JRE, and its Usage|JDK vs JRE]]**: You **develop** with the JDK (Java Development Kit); you **run** with the JRE (Java Runtime Environment).
*   **[[Java Session 1 - Introduction to Java#5. Working with Primitive Data Types|Primitive Types]]**: 8 basic types (`int`, `boolean`, etc.) with fixed sizes across all platforms, which are not objects.

---

#### [[Java Session 2 & 3 - Basic programming concepts|Sessions 2 & 3: Basic programming concepts]]
*   **[[Java Session 2 & 3 - Basic programming concepts#2. Declaring Variables and Methods|Method]]**: A block of code that performs a task; Java's term for a function.
*   **[[Java Session 2 & 3 - Basic programming concepts#3. Data Type Compatibility and Casting|Type Casting]]**: Implicit (widening) casting is automatic; Explicit (narrowing) casting requires a `(type)` prefix and may cause data loss.
*   **[[Java Session 2 & 3 - Basic programming concepts#6. Arrays (1-D and Multidimensional)|Array]]**: An object holding a fixed number of values of a single type. Size is accessed via the `length` property.
*   **[[Java Session 2 & 3 - Basic programming concepts#5. Control Statements|Enhanced `for` loop]]**: A simplified loop (`for (Type var : collection)`) for iterating over arrays or collections.

---

#### [[Java Session 4 - Object Oriented Programming Concepts|Session 4: Object Oriented Programming Concepts]]
*   **[[Java Session 4 - Object Oriented Programming Concepts#2. Classes and Objects|Class]]**: A blueprint for creating objects, defining fields (state) and methods (behavior).
*   **[[Java Session 4 - Object Oriented Programming Concepts#2. Classes and Objects|Object]]**: An instance of a class, created with the `new` keyword.
*   **[[Java Session 4 - Object Oriented Programming Concepts#a) Encapsulation|Encapsulation]]**: Bundling data and methods together, often using `private` fields and public getters/setters.
*   **[[Java Session 4 - Object Oriented Programming Concepts#c) Inheritance|Inheritance]]**: An "is-a" relationship where a subclass acquires members of a superclass, using the `extends` keyword.
*   **[[Java Session 4 - Object Oriented Programming Concepts#d) Polymorphism|Polymorphism]]**: "Many forms." Achieved via method overloading (compile-time) and overriding (runtime).

---

#### [[Java Session 5 - Static, Reference variables and methods|Session 5: Static, Reference variables and methods]]
*   **[[Java Session 5 - Static, Reference variables and methods#1. Static Variables and Methods|`static`]]**: A keyword for members that belong to the class itself, not to individual objects. One copy is shared by all instances.
*   **[[Java Session 5 - Static, Reference variables and methods#2. Introduction to Reference Data Types|Reference Type]]**: Any non-primitive type (classes, arrays). The variable holds a memory address, not the object itself.
*   **[[Java Session 5 - Static, Reference variables and methods#3. Difference Between Reference and Primitive Data Types|`==` vs `.equals()`]]**: For objects, `==` compares memory addresses, while `.equals()` should be overridden to compare object state.

---

#### [[Java Session 6 - Constructors, Pass by value, Heap and Stack|Session 6: Constructors, Pass by value, Heap and Stack]]
*   **[[Java Session 6 - Constructors, Pass by value, Heap and Stack#1. Constructors|Constructor]]**: A special method with the same name as the class and no return type, used to initialize a new object.
*   **[[Java Session 6 - Constructors, Pass by value, Heap and Stack#2. Pass-by-value vs. Pass-by-reference|Pass-by-value]]**: Java is always pass-by-value. For objects, this means a *copy of the reference (address)* is passed.
*   **[[Java Session 6 - Constructors, Pass by value, Heap and Stack#3. Heap and Stack Memory|Stack Memory]]**: Stores local primitive and reference variables. Fast, LIFO, and managed automatically.
*   **[[Java Session 6 - Constructors, Pass by value, Heap and Stack#3. Heap and Stack Memory|Heap Memory]]**: Stores all objects and arrays. Slower, larger, and managed by the Garbage Collector.

---

#### [[Java Session 7 - Inheritance, Association, Aggregation and Composition|Session 7: Inheritance, Association, Aggregation and Composition]]
*   **[[Java Session 7 - Inheritance, Association, Aggregation and Composition#2. Association: The "has-a" Relationship|"is-a" vs "has-a"]]**: "is-a" implies Inheritance (`Car extends Vehicle`). "has-a" implies Composition/Association (`Car has an Engine`).
*   **[[Java Session 7 - Inheritance, Association, Aggregation and Composition#3. Aggregation|Aggregation]]**: A weak "has-a" relationship where the "part" can exist without the "whole" (e.g., Department and Professors).
*   **[[Java Session 7 - Inheritance, Association, Aggregation and Composition#4. Composition|Composition]]**: A strong "has-a" relationship where the "part" cannot exist without the "whole" (e.g., House and Rooms).

---

#### [[Java Session 8 - Upcasting, Downcasting, Abstract class, Interface|Session 8: Upcasting, Downcasting, Abstract class, Interface]]
*   **[[Java Session 8 - Upcasting, Downcasting, Abstract class, Interface#a) Upcasting|Upcasting]]**: Implicitly casting a subclass reference to a superclass type. Always safe.
*   **[[Java Session 8 - Upcasting, Downcasting, Abstract class, Interface#b) Downcasting|Downcasting]]**: Explicitly casting a superclass reference to a subclass type. Potentially unsafe; check with `instanceof` first.
*   **[[Java Session 8 - Upcasting, Downcasting, Abstract class, Interface#2. Abstract Class and Abstract Methods|Abstract Class]]**: A class that cannot be instantiated and may contain abstract (unimplemented) methods. A class `extends` one abstract class.
*   **[[Java Session 8 - Upcasting, Downcasting, Abstract class, Interface#3. Interface|Interface]]**: A 100% abstract blueprint defining a contract of methods. A class `implements` multiple interfaces.

---

#### [[Java Sessions 9 & 10 - Final, Functional Interface, Lambda, Inner Class|Sessions 9 & 10: Final, Functional Interface, Lambda, Inner Class]]
*   **[[Java Sessions 9 & 10 - Final, Functional Interface, Lambda, Inner Class#1. The `final` Keyword|`final`]]**: A keyword to make a variable a constant, a method non-overridable, or a class non-extendable.
*   **[[Java Sessions 9 & 10 - Final, Functional Interface, Lambda, Inner Class#2. Functional Interface|Functional Interface]]**: An interface with exactly one abstract method.
*   **[[Java Sessions 9 & 10 - Final, Functional Interface, Lambda, Inner Class#3. Lambda Expression (Java 8+)|Lambda Expression]]**: A concise, anonymous function to implement a functional interface. Syntax: `(params) -> expression`.
*   **[[Java Sessions 9 & 10 - Final, Functional Interface, Lambda, Inner Class#d) Anonymous Inner Class|Anonymous Inner Class]]**: A nameless, one-time-use class, often replaced by lambdas in modern Java.

---

#### [[Java Session 11 - Access Modifiers, Packages, Imports|Session 11: Access Modifiers, Packages, Imports]]
*   **[[Java Session 11 - Access Modifiers, Packages, Imports#1. Packages and `import` Statements|Package]]**: A namespace to organize classes (e.g., `com.mycompany.project`). Declared with the `package` keyword.
*   **[[Java Session 11 - Access Modifiers, Packages, Imports#2. Access Modifiers|Access Modifiers]]**: Control visibility: `private` (class) -> `default` (package) -> `protected` (package + subclass) -> `public` (world).
*   **[[Java Session 11 - Access Modifiers, Packages, Imports#4. Constructor Chaining|Constructor Chaining]]**: Calling one constructor from another in the same class using `this()`.

---

#### [[Java Session 12 - Garbage collection|Session 12: Garbage collection]]
*   **[[Java Session 12 - Garbage collection#1. Garbage Collection in Java|Garbage Collection (GC)]]**: The JVM's automatic process of reclaiming heap memory from unreachable objects.
*   **[[Java Session 12 - Garbage collection#3. Making an Object Eligible for Garbage Collection|Unreachable Object]]**: An object with no active references pointing to it. This can be achieved by nulling references or creating an "island of isolation".
*   **[[Java Session 12 - Garbage collection#4. The `finalize()` Method|`finalize()`]]**: A deprecated method called by the GC just before object destruction. It is unreliable and should not be used.

---

#### [[Java Sessions 13 & 14 - Wrapper Classes and String Class|Sessions 13 & 14: Wrapper Classes and String Class]]
*   **[[Java Sessions 13 & 14 - Wrapper Classes and String Class#1. Wrapper Classes|Wrapper Class]]**: Provides an object representation for a primitive type (e.g., `Integer` for `int`).
*   **[[Java Sessions 13 & 14 - Wrapper Classes and String Class#1. Wrapper Classes|Autoboxing]]**: The automatic conversion between primitives and their wrapper types.
*   **[[Java Sessions 13 & 14 - Wrapper Classes and String Class#2. The `String` Class|String Immutability]]**: `String` objects cannot be changed once created. Operations like concatenation create new `String` objects.
*   **[[Java Sessions 13 & 14 - Wrapper Classes and String Class#3. `StringBuffer` and `StringBuilder` Classes|StringBuilder vs StringBuffer]]**: Mutable classes for efficient string manipulation. Use `StringBuilder` for single-threaded tasks (faster) and `StringBuffer` for multi-threaded tasks (slower, thread-safe).

---

#### [[Java Sessions 15 & 16 - Exception Handling|Sessions 15 & 16: Exception Handling]]
*   **[[Java Sessions 15 & 16 - Exception Handling#1. Exception Hierarchy, Errors, and Exception Types|Checked Exception]]**: An exception the compiler forces you to handle (e.g., `IOException`). For recoverable conditions.
*   **[[Java Sessions 15 & 16 - Exception Handling#1. Exception Hierarchy, Errors, and Exception Types|Unchecked Exception]]**: An exception (a `RuntimeException`) not enforced by the compiler (e.g., `NullPointerException`). For programming errors.
*   **[[Java Sessions 15 & 16 - Exception Handling#2. `try`, `catch`, `finally`, `throw`, `throws`|try-catch-finally]]**: The core blocks for handling exceptions. `finally` always executes, making it ideal for resource cleanup.
*   **[[Java Sessions 15 & 16 - Exception Handling#2. `try`, `catch`, `finally`, `throw`, `throws`|throw vs throws]]**: You `throw` an instance of an exception. A method `throws` a type of exception in its signature.

---

#### [[Java Session 17 - java.io & java.nio Package|Session 17: java.io & java.nio Package]]
*   **[[Java Session 17 - java.io & java.nio Package#1. Brief Introduction to I/O Streams|Stream]]**: A sequence of data. Use Byte Streams (`InputStream`/`OutputStream`) for binary data and Character Streams (`Reader`/`Writer`) for text.
*   **[[Java Session 17 - java.io & java.nio Package#4. Serialization and Deserialization|Serialization]]**: The process of converting an object into a byte stream. A class must implement the `Serializable` marker interface.
*   **[[Java Session 17 - java.io & java.nio Package#4. Serialization and Deserialization|transient]]**: A keyword to mark a field so it is excluded from the serialization process.
*   **[[Java Session 17 - java.io & java.nio Package#2. `java.io` Package and Decorator Pattern|try-with-resources]]**: The modern, preferred way to automatically close I/O resources.

---

#### [[Java Session 18 - Object Class & java.util Package|Session 18: Object Class & java.util Package]]
*   **[[Java Session 18 - Object Class & java.util Package#1. The `Object` Class|Object Class]]**: The root of the class hierarchy. All Java classes extend it.
*   **[[Java Session 18 - Object Class & java.util Package#c) `hashCode()`|equals() / hashCode() Contract]]**: If two objects are equal via `.equals()`, they MUST have the same hash code. Essential for hash-based collections.
*   **[[Java Session 18 - Object Class & java.util Package#4. Modern Date and Time API (Java 8+) - `java.time`|java.time API]]**: The modern (Java 8+) API for dates and times (`LocalDate`, `LocalTime`). It is immutable and should be preferred over legacy `Date` and `Calendar`.

---

#### [[Java Sessions 19, 20, 21 & 22 - Collections|Sessions 19-22: Collections Framework (Part 1)]]
*   **[[Java Sessions 19, 20, 21 & 22 - Collections#2. The `List` Interface Ordered Collections|List]]**: An ordered collection that allows duplicates (`ArrayList`, `LinkedList`).
*   **[[Java Sessions 19, 20, 21 & 22 - Collections#3. The `Set` Interface Unordered, Unique Collections|Set]]**: A collection that does not allow duplicates (`HashSet`, `LinkedHashSet`, `TreeSet`).
*   **[[Java Sessions 19, 20, 21 & 22 - Collections#6. `Comparable` and `Comparator` Interfaces|Comparable]]**: An interface implemented by a class to define its *natural ordering*.
*   **[[Java Sessions 19, 20, 21 & 22 - Collections#6. `Comparable` and `Comparator` Interfaces|Comparator]]**: An interface implemented in a separate class to define a *custom or external ordering*.

---

#### [[Java Sessions 23, 24, 25 & 26 - Collections Continued (Map, Stream API)|Sessions 23-26: Collections Framework (Part 2)]]
*   **[[Java Sessions 23, 24, 25 & 26 - Collections Continued (Map, Stream API)#1. The `Map` Interface: Key-Value Pairs|`Map`]]**: A collection that stores key-value pairs (`HashMap`, `LinkedHashMap`, `TreeMap`).
*   **[[Java Sessions 23, 24, 25 & 26 - Collections Continued (Map, Stream API)#2. Introduction to the Stream API (Java 8+)|Stream API]]**: A declarative, functional-style way to process collections of data.
*   **[[Java Sessions 23, 24, 25 & 26 - Collections Continued (Map, Stream API)#2. Introduction to the Stream API (Java 8+)|Stream Pipeline]]**: Consists of a Source (`.stream()`), Intermediate operations (`.filter()`, `.map()`), and a Terminal operation (`.collect()`, `.forEach()`).

---

#### [[Java Session 27 - MultiThreading|Session 27: MultiThreading]]
*   **[[Java Session 27 - MultiThreading#1. Introduction to Threads|Thread]]**: A single path of execution within a process.
*   **[[Java Session 27 - MultiThreading#2. Creating Threads: `Thread` class and `Runnable` Interface|`Runnable` vs `Thread`]]**: Implementing `Runnable` is preferred over extending `Thread` for creating tasks.
*   **[[Java Session 27 - MultiThreading#2. Creating Threads: `Thread` class and `Runnable` Interface|`start()` vs `run()`]]**: `start()` creates a new thread. `run()` executes the task in the current thread.

---

#### [[Java Sessions 28 & 29 - Synchronization and Deadlock|Sessions 28 & 29: Synchronization and Deadlock]]
*   **[[Java Sessions 28 & 29 - Synchronization and Deadlock#2. Synchronization|synchronized]]**: A keyword to create a mutually exclusive critical section, preventing race conditions.
*   **[[Java Sessions 28 & 29 - Synchronization and Deadlock#3. Deadlock|Deadlock]]**: A state where two or more threads are blocked forever, each waiting for a resource held by the other.
*   **[[Java Sessions 28 & 29 - Synchronization and Deadlock#4. Inter-thread Communication `wait()`, `notify()`, `notifyAll()`|wait() / notify()]]**: Low-level mechanisms for inter-thread communication. Must be called within a `synchronized` block.

---

#### [[Java Session 30 - Generics and Reflection API|Session 30: Generics and Reflection API]]
*   **[[Java Session 30 - Generics and Reflection API#1. Introduction to Generics|Generics]]**: Provide compile-time type safety for classes and methods (`<T>`).
*   **[[Java Session 30 - Generics and Reflection API#5. Metadata & The Reflection API|Reflection API]]**: A mechanism to inspect and manipulate classes, methods, and fields at runtime. It is powerful but slow and breaks encapsulation.

---

🔗 **[[Java MCQs|All MCQs]]**