### **Session 11: Access Modifiers, Packages, Imports**

Welcome to Session 11. So far, our classes have existed in a single default space. In real-world applications, which can contain hundreds or thousands of classes, this is unmanageable. **Packages** are Java's way of organizing related classes into namespaces. To control what is visible across these package boundaries, Java uses **access modifiers**. This session covers how these two mechanisms work together to create well-structured and encapsulated code.

---

#### **1. Packages and `import` Statements**

A **package** is a namespace that organizes a set of related classes and interfaces. It's like a folder or directory on your filesystem that groups related files.

**Why use packages?**
1.  **Organization:** Keeps related classes grouped together (e.g., `java.util` for utility classes, `java.io` for I/O classes).
2.  **Preventing Naming Conflicts:** Two classes can have the same name if they are in different packages (e.g., `java.util.Date` and `java.sql.Date`).
3.  **Access Control:** Packages provide a level of access control for classes and their members.

**Declaring a Package:**
The `package` statement must be the very first line in a Java source file.
```java
package com.mycompany.project.model; // This file belongs to this package

public class Employee {
    // ...
}
```
This corresponds to a directory structure: `com/mycompany/project/model/Employee.java`.

**The `import` Statement:**
To use a class from another package, you must either use its fully qualified name or `import` it.

*   **Fully Qualified Name:** `java.util.ArrayList list = new java.util.ArrayList();` (Verbose)
*   **`import` Statement:** Makes the class available to use by its simple name. It's placed after the `package` statement but before the class declaration.

```java
package com.mycompany.project.service;

import com.mycompany.project.model.Employee; // Import a single class
import java.util.*; // Import all classes from the java.util package (wildcard import)

public class EmployeeService {
    public void processEmployee() {
        Employee emp = new Employee(); // Can use simple name because it's imported
        List<Employee> empList = new ArrayList<>(); // ArrayList is available via wildcard import
    }
}
```

> **Quick Question:** If you need to use both `java.util.Date` and `java.sql.Date` in the same file, can you import both with a wildcard? What is the solution?
> **Answer:** You can, but you would still have a naming conflict. The solution is to import one (e.g., `import java.util.Date;`) and use the fully qualified name for the other (e.g., `java.sql.Date sqlDate = new java.sql.Date(...);`).

---

#### **2. Access Modifiers**

Access modifiers in Java determine the visibility of a class, field, method, or constructor. They are the core of [[Java Session 4 - Object Oriented Programming Concepts#a) Encapsulation|encapsulation]].

Java has four access modifiers, listed here from most restrictive to least restrictive:

| Modifier | Same Class | Same Package | Subclass (diff package) | World (diff package) |
| :--- | :--- | :--- | :--- | :--- |
| **`private`** | Yes | No | No | No |
| **`default`** (no keyword) | Yes | Yes | No | No |
| **`protected`** | Yes | Yes | Yes | No |
| **`public`** | Yes | Yes | Yes | Yes |

*   **`private`**: The member is only accessible within its own class. This is the highest level of encapsulation. **Use this for class fields by default.**
*   **`default` (Package-Private)**: This is the access level you get when you **don't specify a modifier**. The member is accessible to any class in the *same package*, but not outside.
*   **`protected`**: The member is accessible within its own package and also by subclasses in *different packages*. This is directly related to [[Java Session 7 - Inheritance, Association, Aggregation and Composition|inheritance]].
*   **`public`**: The member is accessible from anywhere. This provides no encapsulation. **Use this for public APIs, like constructors and methods intended for external use.**

**Example:**
```java
// In package: com.library.core
package com.library.core;

public class Book {
    public String title;       // Accessible everywhere
    protected int issueCount;    // Accessible in com.library.core and any subclass
    String author;             // default: Accessible only within com.library.core
    private String isbn;       // Accessible only within the Book class
}
```

```java
// In package: com.library.user
package com.library.user;

import com.library.core.Book;

public class LibraryUser {
    public void checkBook() {
        Book b = new Book();
        System.out.println(b.title); // OK, public
        // System.out.println(b.issueCount); // ERROR, not a subclass and in diff package
        // System.out.println(b.author);     // ERROR, in different package
        // System.out.println(b.isbn);       // ERROR, private to Book class
    }
}
```

> **Quick Question:** If you want a method to be used by subclasses, but not by other random classes in different packages, which access modifier should you use?
> **Answer:** `protected`.

---

#### **3. Static Imports**

A static import allows you to import the `static` members (fields and methods) of a class. This lets you use them without prefixing the class name.

**Use case:** Useful when you are frequently using static members from a single class, like `Math` or constants from a utility class.

**Example:**
```java
import static java.lang.Math.PI;
import static java.lang.Math.pow;
// Or wildcard: import static java.lang.Math.*;

public class Circle {
    double radius;
    
    public Circle(double radius) { this.radius = radius; }
    
    public double getArea() {
        // We can use PI and pow directly without 'Math.'
        return PI * pow(radius, 2);
    }
}
```
**Caution:** Overusing static imports can make code harder to read because it's not always clear where the method or constant is coming from.

---

#### **4. Constructor Chaining**

Constructor chaining is the process of calling one constructor from another within the same class. It is used to avoid code duplication in constructors.

*   **`this()`:** To call another constructor in the **same class**.
*   **`super()`:** To call a constructor in the **superclass**. (We will discuss this more with inheritance).

**Rule:** The `this()` or `super()` call must be the **very first statement** in a constructor.

**Example:**
```java
public class Box {
    private int length, width, height;

    // 1. The most specific constructor does the work
    public Box(int length, int width, int height) {
        this.length = length;
        this.width = width;
        this.height = height;
    }

    // 2. A constructor for a cube
    public Box(int side) {
        // Calls the first constructor with the same value for all sides
        this(side, side, side); 
    }

    // 3. A default constructor
    public Box() {
        // Calls the cube constructor with a default side of 1
        this(1); 
    }
}
```

---

### **Topic Summary & Revision**

*   **Package:** A namespace to organize classes and prevent naming conflicts. Declared with the `package` keyword.
*   **`import`:** Used to access classes from other packages by their simple names.
*   **Access Modifiers:** Control visibility (`private` -> `default` -> `protected` -> `public`).
*   **`private`:** Same class only. The default for encapsulation.
*   **`default`:** Same package only.
*   **`protected`:** Same package + subclasses anywhere.
*   **`public`:** Accessible everywhere.
*   **Static Import:** Imports static members of a class for direct use (`import static ...`).
*   **Constructor Chaining:** Calling one constructor from another using `this()` to reduce code duplication.

---

### **MCQs for Exam Preparation (Tricky)**

1.  **A class `A` is in `package p1`. A class `B` is in `package p2`. Class `B` extends `A`. A method `m()` in class `A` is declared with the `protected` modifier. Can `m()` be accessed from within class `B`?**
    (A) Yes, because `B` is a subclass of `A`.
    (B) No, because `B` and `A` are in different packages.
    (C) Only if class `B` is declared `final`.
    (D) Only if an object of `B` is created inside package `p1`.
    **Answer:** ||(A) This is the exact definition of 'protected': accessible within its own package OR to subclasses in different packages. Since 'B' is a subclass, it gets access.||
<br>

2.  **A source file `Test.java` contains the following two class declarations. What is the result of compiling this file?**
    ```java
    package com.test;
    public class Test { }
    class AnotherTest { } 
    ```
    (A) Compilation fails because two classes cannot be in the same file.
    (B) Compilation succeeds, and two files are created: `Test.class` and `AnotherTest.class`.
    (C) Compilation fails because `AnotherTest` does not have an access modifier.
    (D) Compilation fails because `AnotherTest` must also be declared `public`.
    **Answer:** ||(B) A single Java source file can contain multiple classes, but at most one can be 'public'. The non-public class ('AnotherTest' here) gets 'default' (package-private) access. The compiler will generate a separate '.class' file for each class defined.||
<br>

3.  **A method is declared in a class without any access modifier. Which of the following statements is true about its visibility?**
    (A) It is visible to all classes in the same project.
    (B) It is visible only to the class it is in and any of its subclasses.
    (C) It is visible to all other classes within the same package.
    (D) It is equivalent to being declared `private`.
    **Answer:** ||(C) No modifier means 'default' or 'package-private' access. It can be accessed by any class in the same package but is hidden from all classes outside the package, including subclasses.||
<br>

4.  **What is the primary risk of overusing `import static com.utils.MyConstants.*;`?**
    (A) It significantly increases the size of the compiled `.class` file.
    (B) It can lead to namespace pollution and make the code harder to read by hiding the origin of constants.
    (C) It slows down runtime performance due to dynamic lookups.
    (D) It prevents the `MyConstants` class from being extended.
    **Answer:** ||(B) This is a readability and maintenance issue. If you see a variable named 'MAX_USERS' in the code, it's not immediately clear if it's a local variable or a static constant from some imported class. Using 'MyConstants.MAX_USERS' is unambiguous.||
<br>

5.  **What happens if a constructor tries to call both `this()` and `super()`?**
    ```java
    public class MyClass extends Parent {
        public MyClass() {
            super(); // Call to parent constructor
            this(10);  // Call to another constructor in this class
        }
        public MyClass(int x) { }
    }
    ```
    (A) The code compiles and runs, calling the parent constructor first.
    (B) The code compiles and runs, calling the `this()` constructor first.
    (C) A compilation error occurs.
    (D) A runtime exception is thrown.
    **Answer:** ||(C) A compilation error occurs because a call to 'this()' or 'super()' must be the absolute first statement in a constructor. You cannot have both. When you use 'this()', the chained-to constructor is responsible for calling 'super()'.||

---

### **Bonus Tips**

*   **Viva/Interview Tip:** Be prepared to draw the access modifier table (MCQ #1). A common follow-up question is, "What is the difference between `default` and `protected`?" The key difference is `protected`'s extra visibility to subclasses *outside* the package.
*   **Standard Practice:** The convention for package names is the reverse domain name of your organization, all in lowercase (e.g., `com.google.common`, `org.apache.commons`). This ensures uniqueness.
*   **Design Principle:** The "Principle of Least Privilege." Always use the most restrictive access modifier that still gets the job done. Start with `private` for everything, and only increase visibility (`default`, `protected`, `public`) when necessary. This maximizes encapsulation and reduces the "surface area" of your classes, making them more robust.

**🔗Links:** [[Java Session 12 - Garbage collection]]