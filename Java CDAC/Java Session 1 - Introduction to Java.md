### **Session 1: Introduction to Java**

Welcome to your first session on Object Oriented Programming with Java! While you've seen OOP concepts in C++, Java was built from the ground up with OOP in mind. It is one of the most popular and in-demand programming languages in the world, powering everything from web applications and mobile apps (Android) to large-scale enterprise systems.

The guiding philosophy of Java is **"Write Once, Run Anywhere" (WORA)**. Let's explore what that means.

---

#### **1. Introduction and Features of Java**

Java is a high-level, class-based, object-oriented programming language designed to have as few implementation dependencies as possible.

**Key Features:**

*   **Platform Independent:** This is Java's most famous feature. Unlike C++, which compiles to native machine code for a specific OS, Java source code is compiled into an intermediate format called **bytecode**. This bytecode can then be run on any machine that has a Java Virtual Machine (JVM).
*   **Object-Oriented:** Java treats everything as an object (with the exception of primitive data types). It fully supports the core OOP principles like [[Java Session 4 - Object Oriented Programming Concepts#3. OOP Principles|Encapsulation, Inheritance, and Polymorphism]].
*   **Simple:** Java removed many complex and error-prone features from C++, such as explicit pointers and manual memory management (it has automatic garbage collection).
*   **Robust:** Java is a strongly-typed language and includes excellent exception handling capabilities, which helps in creating reliable applications.
*   **Secure:** Java was designed with security in mind. It runs applications inside a "sandbox" (the JVM) to prevent them from harming the host system.

**Analogy:**
Think of C++ as hiring a local architect who designs a building specifically for your city's climate and building codes (the Operating System). That design won't work in a different city.
Java is like creating a universal, pre-fabricated building plan (**bytecode**). You can take this plan to any city in the world, and the local construction crew (**JVM**) will know exactly how to build it according to their local codes.

> **Quick Question:** What is the famous slogan that describes Java's platform independence?
> **Answer:** "Write Once, Run Anywhere" (WORA).

---

#### **2. The Java Virtual Machine (JVM) Architecture**

The JVM is the heart of Java's platform independence. It is a virtual "machine" or processor that exists only in software. Its job is to load, verify, and execute Java bytecode.

**How it works:**
1.  You write your program in a `.java` file (source code).
2.  You use the Java compiler (`javac`) to compile it. The output is not machine code, but a `.class` file containing **bytecode**.
3.  When you run your program, the JVM for your specific operating system (e.g., Windows JVM, Linux JVM) starts up.
4.  The JVM reads the platform-neutral bytecode and translates it into native machine code that your computer's actual processor can understand and execute.

The JVM is the component that is platform-dependent, but because it understands the platform-independent bytecode, your Java program can run anywhere.

> **Quick Question:** What does the Java compiler (`javac`) produce as output?
> **Answer:** A `.class` file containing platform-independent bytecode.

---

#### **3. JDK, JRE, and its Usage**

These three acronyms are often confusing but represent a simple hierarchy.

*   **JVM (Java Virtual Machine):** The core component that *runs* bytecode. It cannot be downloaded alone.
*   **JRE (Java Runtime Environment):** Contains the JVM and the Java standard libraries. It provides everything you need to **run** existing Java applications.
*   **JDK (Java Development Kit):** The full toolkit for Java **developers**. It contains the JRE, which in turn contains the JVM, plus development tools like the compiler (`javac`), debugger, and archiver (`jar`).

**Analogy - The Car Factory:**
*   **JVM:** The engine of the car.
*   **JRE:** A complete car, ready to drive. You can't build another car with it, but you can go places.
*   **JDK:** The entire car factory, with all the tools, machinery (compiler), and a finished car (JRE) to test drive.

As a developer, you will always install the **JDK**.

> **Quick Question:** If you only want to run a Java application on your computer, but not develop one, which component do you need?
> **Answer:** The JRE.

---

#### **4. Structure of a Java Class**

Every executable Java program must contain a class with a `main` method. This method is the entry point of the program.

**Example: `HelloWorld.java`**
```java
// The class name must match the file name (HelloWorld.java)
public class HelloWorld {
    
    // This is the entry point of the program
    public static void main(String[] args) {
        
        // This prints a line of text to the console
        System.out.println("Hello, World!");
    }
}
```

**Breakdown:**
*   `public class HelloWorld`: Declares a class named `HelloWorld` that is accessible to anyone.
*   `public static void main(String[] args)`: This is the exact signature the JVM looks for to start the program.
    *   `public`: It can be called from anywhere.
    *   `static`: It can be run without creating an object of the `HelloWorld` class.
    *   `void`: The method doesn't return any value.
    *   `main`: The name of the method.
    *   `String[] args`: An array of strings to receive any command-line arguments.
*   `System.out.println()`: The standard way to print output to the console, followed by a new line.

> **Quick Question:** If you save a Java source file with the class declaration `public class MyProgram`, what must the filename be?
> **Answer:** `MyProgram.java`.

---

#### **5. Working with Primitive Data Types**

Java has two categories of data types: **primitive** and **reference**. Primitive types are the most basic types and are not objects. They store simple values directly.

| Category | Type | Size | Description |
| :--- | :--- | :--- | :--- |
| **Integers** | `byte` | 1 byte | Stores whole numbers from -128 to 127 |
| | `short` | 2 bytes | Stores whole numbers from -32,768 to 32,767 |
| | `int` | 4 bytes | The most common integer type |
| | `long` | 8 bytes | For very large whole numbers |
| **Floating-Point** | `float` | 4 bytes | Single-precision floating point number |
| | `double`| 8 bytes | Double-precision, default type for decimals |
| **Character** | `char` | 2 bytes | Stores a single character (Unicode) |
| **Boolean** | `boolean`| 1 bit | Stores only `true` or `false` |

**Key Difference from C++:**
*   The sizes of these types are **fixed and standard** across all platforms. An `int` is always 4 bytes, whether you are on Windows or Linux. This is crucial for platform independence.
*   A `boolean` cannot be treated as an integer (`0` or `1`). It is strictly `true` or `false`.

> **Quick Question:** What is the key difference between Java's `char` type and the `char` type in C?
> **Answer:** Java's `char` is 2 bytes and represents a Unicode character, while C's `char` is typically 1 byte and represents an ASCII character.

---

### **Topic Summary & Revision**

*   **Java Philosophy:** "Write Once, Run Anywhere" (WORA), enabled by the JVM.
*   **Compilation Process:** `Source Code (.java)` -> `Compiler (javac)` -> `Bytecode (.class)` -> `JVM` -> `Machine Code`.
*   **JDK vs JRE:** You **develop** with the JDK; you **run** with the JRE.
*   **Program Structure:** Every Java program starts in the `public static void main(String[] args)` method inside a public class.
*   **Primitive Types:** Java has 8 primitive types (`byte`, `short`, `int`, `long`, `float`, `double`, `char`, `boolean`) with fixed sizes, which are not objects.

---

### **#MCQs for Exam Preparation (Tricky)**

1.  **A developer compiles a `.java` file on a 64-bit Windows machine using JDK 11. Which of the following environments can run the resulting `.class` file without recompilation?**
    (A) Only a 64-bit Windows machine with JRE 11 or higher.
    (B) Any machine (Windows, Linux, macOS) with a JRE of version 11 or higher.
    (C) Only 64-bit machines with any version of the JRE.
    (D) Any machine, but it must have JDK 11 installed, not just the JRE.
    **Answer:** ||(B) The bytecode is platform-independent; only a compatible JRE (same or higher version) is needed to run it on any supported OS.||
<br>
2.  **Which of the following `main` method declarations is NOT a valid entry point for a Java application?**
    (A) `public static void main(String[] arguments)`
    (B) `public static void main(String... args)`
    (C) `static public void main(String[] args)`
    (D) `public void main(String[] args)`
    **Answer:** ||(D) The 'main' method must be 'static' so the JVM can call it without creating an object of the class. All other options are valid syntactical variations.||
<br>
3.  **What is the defining characteristic of Java bytecode?**
    (A) It is optimized for the specific architecture of the machine it was compiled on.
    (B) It is a human-readable text format similar to source code.
    (C) It is platform-neutral and can be executed by any standard JVM.
    (D) It is directly executable machine code, making it very fast.
    **Answer:** ||(C) Its key feature is platform neutrality. It is not machine code (D is wrong), not human-readable (B is wrong), and not platform-specific (A is wrong).||
<br>
4.  **Consider the following code snippet. What will be the result?**
   ```java
    int a = 1;
    boolean b = true;
    if (b) {
        // some code
    }
    // if (a) {  // This line is commented out
    //     // some code
    // }
```

(A) The code compiles and runs without issue.
(B) The code fails to compile because `boolean b = true;` is an invalid declaration.
(C) The code compiles, but would fail if `if (a)` was uncommented, because an integer cannot be used as a boolean condition.
(D) The code fails to compile because `int` and `boolean` cannot be used in the same block.
**Answer:** ||(C) In Java, 'if' statements require a strict 'boolean' expression. Unlike C++, an integer like '1' cannot be interpreted as 'true'. The code as given compiles, but the commented-out line highlights this critical, tricky difference.||
<br>
5.  **A file is named `MyTest.java`. Which of the following class declarations inside this file will cause a compilation error?**
    (A) `class MyTest { ... }`
    (B) `public class MyTest { ... }`
    (C) `class Test { ... }` (and no other public class)
    (D) `public class MyProgram { ... }`
    **Answer:** ||(D) A Java source file can have at most one 'public' class, and if it has one, the name of the class must match the name of the file.||

---

### **Bonus Tips**

*   **Viva/Interview Tip:** The most fundamental question you will be asked is **"What is the difference between JDK, JRE, and JVM?"**. Use the "developer vs. user" or the "factory vs. car" analogy to explain it clearly. Also, be prepared to explain *why* Java is platform-independent (the role of bytecode).
*   **Exam Tip:** The rule about the public class name matching the filename is a very common source for tricky multiple-choice questions. Remember it!
*   **Lab Tip:** The first challenge for any new Java developer is setting up the environment. Make sure your JDK is installed correctly and that your system's `PATH` environment variable is configured to point to the JDK's `bin` directory. This allows you to run `javac` and `java` from any command prompt location.

**🔗Links:** [[Java Session 2 & 3 - Basic programming concepts]]