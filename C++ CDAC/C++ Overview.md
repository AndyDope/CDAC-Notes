### **C++ Overview**

This page provides a high-level summary of the essential concepts covered in the PG-DAC C++ module, organized by session. Use it as a quick-recall cheat sheet before exams.

---

#### [[C++ Session 1 - Getting Started|Session 1: Getting Started]]
*   [[C++ Session 1 - Getting Started#4. Writing Your First C++ Program (`Hello, World!`)|iostream]]: The header library for standard input and output stream operations.
*   [[C++ Session 1 - Getting Started#4. Writing Your First C++ Program (`Hello, World!`)|cout]]: The standard output stream object used to print data to the console (Character OUTput).
*   [[C++ Session 1 - Getting Started#4. Writing Your First C++ Program (`Hello, World!`)|cin]]: The standard input stream object used to read data from the console (Character INput).
*   [[C++ Session 1 - Getting Started#2. The Need for C++ & C++ versus C|C++ vs C]]: C++ is an extension of C that adds Object-Oriented Programming features, type safety, and a richer standard library.

---

#### [[C++ Sessions 2 & 3 - Beginning with C++|Sessions 2 & 3: Beginning with C++]]
*   **[[C++ Sessions 2 & 3 - Beginning with C++#1. C++Program structure|Program Structure]]**: A C++ program typically consists of preprocessor directives (`#include`), a `main` function, and statements ending with semicolons.
*   **[[C++ Sessions 2 & 3 - Beginning with C++#2. C++ Tokens|Tokens]]**: The smallest individual units in a program, such as keywords, identifiers, constants, and operators.
*   **[[C++ Sessions 2 & 3 - Beginning with C++#5. Operators|Operators]]**: Symbols that perform operations on variables and values (e.g., `+`, `-`, `*`, `/`, `%`, `==`, `&&`).
*   **[[C++ Sessions 2 & 3 - Beginning with C++#4. Constant and Static Members|Static Members]]**: Class members that belong to the class itself, not to individual objects (shared by all objects).
*   **[[C++ Sessions 2 & 3 - Beginning with C++#4. Constant and Static Members|Constant Members]]**: Class members whose values cannot be modified after initialization.

---

#### [[C++ Session 4 - Conditional and Looping Statements|Session 4: Conditional and Looping Statements]]
*   [[C++ Session 4 - Conditional and Looping Statements#**1. Conditional Statements (`if`, `else if`, `switch`)**|if-else]]: Executes code blocks conditionally based on a boolean expression.
*   [[C++ Session 4 - Conditional and Looping Statements#**1. Conditional Statements (`if`, `else if`, `switch`)**|switch]]: Selects one of many code blocks to be executed based on an integer or character value.
*   [[C++ Session 4 - Conditional and Looping Statements#**2. Looping Statements (`for`, `while`, `do-while`)**|for / while / do-while]]: Loops used for executing a block of code repeatedly.
*   [[C++ Session 4 - Conditional and Looping Statements#**3. Jump Statements (`break`, `continue`, `return`)**|break / continue]]: Keywords to exit a loop (`break`) or skip the current iteration (`continue`).
*   [[C++ Session 4 - Conditional and Looping Statements#**4. Arrays**|Array]]: A collection of fixed-size elements of the same data type stored sequentially in memory.

---

#### [[C++ Session 5 - Functions in C++|Session 5: Functions in C++]]
*   [[C++ Session 5 - Functions in C++|Function]]: A named block of code that performs a specific task and can be called from other parts of the program.
*   [[C++ Session 5 - Functions in C++#**3. Call by Reference**|Call by Reference]]: Passing arguments to a function by reference (`&`), allowing the function to modify the original variables.
*   [[C++ Session 5 - Functions in C++#**4. Inline Functions**|Inline Function]]: A function whose code is expanded at the call site by the compiler to reduce function-call overhead.

---

#### [[C++ Sessions 6 & 7 - Memory Management and Pointers|Sessions 6 & 7: Memory Management and Pointers]]
*   [[C++ Sessions 6 & 7 - Memory Management and Pointers#**2. Pointers in C++**|Pointer]]: A variable that stores the memory address of another variable.
*   [[C++ Sessions 6 & 7 - Memory Management and Pointers#**3. Dynamic Memory Allocation `new` and `delete`**|new]]: The C++ operator used to allocate memory dynamically on the heap.
*   [[C++ Sessions 6 & 7 - Memory Management and Pointers#**3. Dynamic Memory Allocation `new` and `delete`**|delete]]: The C++ operator used to deallocate memory that was allocated with `new`.
*   [[C++ Sessions 6 & 7 - Memory Management and Pointers#**5. Class Pointers and the `this` Pointer**|'this' pointer]]: A special pointer within a member function that points to the object on which the function was called.

---

#### [[C++ Session 8 - OOP Concepts|Session 8: OOP Concepts]]
*   [[C++ Session 8 - OOP Concepts#**1. Classes and Objects**|Class]]: A user-defined blueprint for creating objects, defining properties (data members) and behaviors (member functions).
*   [[C++ Session 8 - OOP Concepts#**1. Classes and Objects**|Object]]: An instance of a class.
*   [[C++ Session 8 - OOP Concepts#**2. Access Specifiers (`public`, `private`, `protected`) & Encapsulation**|Encapsulation]]: Bundling data and the methods that operate on that data into a single unit (a class).
*   [[C++ Session 8 - OOP Concepts#^e9adea|Abstraction]]: Hiding complex implementation details and showing only essential features of the object.
*   [[C++ Session 8 - OOP Concepts#^f6a695|Inheritance]]: The mechanism by which one class (derived) acquires the properties and behaviors of another class (base).
*   [[C++ Session 8 - OOP Concepts#^dd9d6a|Polymorphism]]: The ability to present the same interface for differing underlying forms (data types or classes).

---

#### [[C++ Session 9 - Constructors and Destructor|Session 9: Constructors and Destructor]]
*   [[C++ Session 9 - Constructors and Destructor#**1. Constructors**|Constructor]]: A special member function that is automatically called when an object is created, used for initialization.
*   [[C++ Session 9 - Constructors and Destructor#**4. Destructor**|Destructor]]: A special member function that is automatically called when an object is destroyed, used for cleanup.
*   [[C++ Session 9 - Constructors and Destructor#**2. Copy Constructor**|Copy Constructor]]: A constructor that creates a new object as a copy of an existing object.

---

#### [[C++ Session 10 - Inheritance - Extending Class|Session 10: Inheritance]]
*   [[C++ Session 10 - Inheritance - Extending Class#**1. The Basics of Inheritance**|Inheritance]]: The "is-a" relationship, enabling code reusability (e.g., `class Dog : public Animal`).
*   [[C++ Session 10 - Inheritance - Extending Class#**2. Types of Inheritance**|Types of Inheritance]]: Single, Multiple, Multilevel, Hierarchical, and Hybrid describe different ways classes can inherit from each other.
*   [[C++ Session 10 - Inheritance - Extending Class#**4. The Diamond Problem and Virtual Base Class**|Virtual Base Class]]: A solution to the "diamond problem" in multiple inheritance, ensuring a common base class is included only once.

---

#### [[C++ Session 11 - Polymorphism|Session 11: Polymorphism]]
*   [[C++ Session 11 - Polymorphism#**2. Function Overloading**|Function Overloading]]: Defining multiple functions with the same name but different parameters (compile-time polymorphism).
*   [[C++ Session 11 - Polymorphism#**3. Operator Overloading**|Operator Overloading]]: Redefining the behavior of C++ operators for user-defined types (classes).
*   **[[C++ Session 11 - Polymorphism#4. Friend functions|Friend Function]]**: A non-member function that is granted access to the `private` and `protected` members of a class.

---

#### [[C++ Session 12 - Virtual Functions and Abstract Class|Session 12: Virtual Functions and Abstract Class]]
*   [[C++ Session 12 - Virtual Functions and Abstract Class#^d52bb2|Run-Time Polymorphism]]: The ability of a program to decide which function to call at runtime, achieved using virtual functions.
*   [[C++ Session 12 - Virtual Functions and Abstract Class#^f129e5|virtual Function]]: A member function in a base class that you expect to be redefined in derived classes.
*   [[C++ Session 12 - Virtual Functions and Abstract Class#**3. Pure Virtual Functions and Abstract Classes**|Pure Virtual Function]]: A virtual function with no definition (`= 0;`), which must be implemented by derived classes.
*   [[C++ Session 12 - Virtual Functions and Abstract Class#^3a6ff5|Abstract Class]]: A class that has at least one pure virtual function and cannot be instantiated.

---

#### [[C++ Session 13 - Exception Handling|Session 13: Exception Handling]]
*   [[C++ Session 13 - Exception Handling#**1. Exception Handling Introduction**|Exception]]: An anomalous or exceptional condition requiring special processing, often detected at runtime.
*   [[C++ Session 13 - Exception Handling#**2. The `try`, `throw`, and `catch` Blocks**|try]]: A block of code that might throw an exception.
*   [[C++ Session 13 - Exception Handling#**3. Catching Multiple Exceptions and Re-throwing**|catch]]: A block of code that handles an exception thrown by a `try` block.
*   [[C++ Session 13 - Exception Handling#^f8febc|throw]]: A keyword used to signal that an exception has occurred.

---

#### [[C++ Session 14 - Managing Console IO Operations|Session 14: Managing Console I/O Operations]]
*   [[C++ Session 14 - Managing Console IO Operations#**1. Introduction to C++ Streams**|Stream]]: A sequence of bytes flowing from a source to a destination (e.g., from the keyboard to a program).
*   [[C++ Session 14 - Managing Console IO Operations#**2. C++ Stream Classes and Standard Objects**|Stream Classes]]: `istream` (input), `ostream` (output), and `iostream` (input/output) form the basis of C++ I/O.
*   [[C++ Session 14 - Managing Console IO Operations#**4. Formatted I/O and Manipulators**|Manipulators]]: Functions like `endl`, `setw`, and `setprecision` used to format stream I/O.

---

#### [[C++ Session 15 - File Handling in C++|Session 15: File Handling in C++]]
*   [[C++ Session 15 - File Handling in C++#**1. Definition of a File**|fstream]]: The header library for file stream operations.
*   [[C++ Session 15 - File Handling in C++#**3. Writing to a File (`ofstream`)**|ofstream]]: The output file stream class, used for writing to files.
*   [[C++ Session 15 - File Handling in C++#**4. Reading from a File (`ifstream`)**|ifstream]]: The input file stream class, used for reading from files.
*   [[C++ Session 15 - File Handling in C++#**5. File Modes**|ios::app]]: A file mode used to append data to the end of an existing file.

---

#### [[C++ Session 16 - Templates|Session 16: Templates]]
*   [[C++ Session 16 - Templates#**1. Introduction to Templates**|Template]]: A blueprint for creating generic functions or classes that can work with any data type.
*   [[C++ Session 16 - Templates#^115c3b|Generic Programming]]: A style of programming focused on writing type-independent code.
*   [[C++ Session 16 - Templates#^956979|Instantiation]]: The compile-time process of generating a specific function or class from a template for a given type.

---

#### [[C++ Sessions 17 & 18 - STL and RTTI|Sessions 17 & 18: STL and RTTI]]
*   [[C++ Sessions 17 & 18 - STL and RTTI#^06b372|STL (Standard Template Library)]]: A powerful library of generic containers, algorithms, and iterators.
*   [[C++ Sessions 17 & 18 - STL and RTTI#**1. Introduction to the C++ Standard Library & STL**|Container]]: A data structure that stores a collection of objects (e.g., `vector`, `map`).
*   [[C++ Sessions 17 & 18 - STL and RTTI#**`vector` - The Dynamic Array**|vector]]: A dynamic array that can automatically resize itself.
*   [[C++ Sessions 17 & 18 - STL and RTTI#stack - Last-In, First-Out (LIFO)|stack]]: A LIFO (Last-In, First-Out) container.
*   [[C++ Sessions 17 & 18 - STL and RTTI#queue - First-In, First-Out (FIFO)|queue]]: A FIFO (First-In, First-Out) container.
*   [[C++ Sessions 17 & 18 - STL and RTTI#map - Key-Value Pairs|map]]: An associative container that stores sorted key-value pairs.
*   [[C++ Sessions 17 & 18 - STL and RTTI#3. Introduction to RTTI (Run-Time Type Information)|RTTI (Run-Time Type Information)]]: A mechanism to determine the type of an object during program execution.
*   [[C++ Sessions 17 & 18 - STL and RTTI#^802f96|typeid]]: An operator that returns type information about an object or expression at runtime.

---

🔗 **[[C++ MCQs|All MCQs]]**