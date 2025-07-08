### **Sessions 2 & 3: Basic Programming Concepts**

Welcome to your second lesson. Having understood the JVM, Java's structure, and its primitive types, we will now cover the fundamental building blocks of writing any program: variables, operators, and control flow statements. Much of this will feel familiar from C++, but we will focus on the key differences and Java's specific syntax.

---

#### **1. Java Tokens**

Just like in C++, **tokens** are the smallest individual units of a program that are meaningful to the compiler. These include:

*   **Keywords:** Reserved words with special meaning (e.g., `public`, `class`, `int`, `if`, `for`).
*   **Identifiers:** Names given to variables, methods, and classes (e.g., `myVariable`, `calculateSum`, `Employee`).
*   **Literals:** Constant values assigned to variables (e.g., `101`, `3.14`, `'A'`, `"Hello"`).
*   **Operators:** Symbols that perform operations (e.g., `+`, `=`, `==`, `&&`).
*   **Separators:** Symbols used to define the structure of the code (e.g., `( )`, `{ }`, `;`).

---

#### **2. Declaring Variables and Methods**

**Variables** are named memory locations that store data. The syntax is straightforward:
`dataType variableName = value;`

```java
int score = 95;          // Declaring and initializing an integer variable
double interestRate = 7.5; // A double for floating-point values
char grade = 'A';        // A single character
String name = "Ravi";    // A string (Note: String is a class, not a primitive)
```

A **Method** is a block of code that performs a specific action and only runs when it is called. It's Java's term for a function.

**Syntax:**
`accessModifier static/non-static returnType methodName(parameterList) { // method body }`

```java
public class Calculator {
    
    // A simple method to add two integers
    public int add(int num1, int num2) {
        int result = num1 + num2;
        return result;
    }

    // A static method that can be called without creating an object
    public static void printWelcomeMessage() {
        System.out.println("Welcome to the Calculator!");
    }
}
```

> **Quick Question:** What is the fundamental difference between `int` and `String` in terms of Java's type system?
> **Answer:** `int` is a [[Java Session 1 - Introduction to Java#5. Working with Primitive Data Types|primitive data type]], while `String` is a reference type (an object/class).

---

#### **3. Data Type Compatibility and Casting**

Java is a **strongly-typed** language, meaning you cannot mix incompatible types without explicit permission.

**Implicit Casting (Widening Conversion):**
This happens automatically when you assign a value from a "smaller" data type to a "larger" one. It's safe because there's no risk of losing data.

```java
int myInt = 100;
long myLong = myInt;  // Implicit cast from int to long (safe)
double myDouble = myLong; // Implicit cast from long to double (safe)
```
Hierarchy: `byte` -> `short` -> `int` -> `long` -> `float` -> `double`

**Explicit Casting (Narrowing Conversion):**
This is required when you assign a value from a "larger" type to a "smaller" one. You must tell the compiler you are aware of the potential data loss by using the cast operator `(dataType)`.

```java
double price = 99.98;
// int myIntPrice = price; // Compilation Error! Possible data loss.

int myIntPrice = (int) price; // Explicit cast. myIntPrice will be 99.
```

**Analogy:**
*   **Implicit Casting:** Pouring water from a small bottle into a large bucket. No problem.
*   **Explicit Casting:** Pouring water from a large bucket into a small bottle. You have to do it carefully (`(int)`) and accept that some water might spill (data loss).

> **Quick Question:** Will `float myFloat = 12.3;` compile?
> **Answer:** No. By default, decimal literals like `12.3` are treated as `double`. You must explicitly tell the compiler it's a float: `float myFloat = 12.3f;` or `float myFloat = (float)12.3;`.

---

#### **4. Operators**

Java's operators are nearly identical to C++'s.

*   **Arithmetic:** `+`, `-`, `*`, `/`, `%` (modulus)
*   **Relational:** `==` (equals), `!=` (not equals), `>`, `<`, `>=`, `<=`
*   **Logical:** `&&` (logical AND), `||` (logical OR), `!` (logical NOT)
*   **Assignment:** `=`, `+=`, `-=`, `*=`, `/=`
*   **Increment/Decrement:** `++` (increment), `--` (decrement)
*   **Ternary Operator:** `condition ? value_if_true : value_if_false`

**Key Difference from C++:** Java does not support operator overloading. You cannot redefine what the `+` operator does for your custom classes.

---

#### **5. Control Statements**

These statements direct the flow of execution in your program. They are syntactically identical to their C++ counterparts.

*   **Selection:**
    *   `if`, `else if`, `else`
    *   `switch` (can switch on `byte`, `short`, `char`, `int`, `String`, and `Enum` types).
*   **Iteration (Loops):**
    *   `for` loop
    *   `while` loop
    *   `do-while` loop
*   **Enhanced `for` loop (for-each loop):** A simplified loop for iterating over arrays or collections.

**Example: Enhanced `for` loop**
```java
int[] numbers = {10, 20, 30, 40, 50};

// Traditional for loop
for (int i = 0; i < numbers.length; i++) {
    System.out.println(numbers[i]);
}

// Enhanced for loop - simpler and less error-prone
for (int number : numbers) {
    System.out.println(number);
}
```

---

#### **6. Arrays (1-D and Multidimensional)**

An **array** is an object that holds a fixed number of values of a single type.

**1-D Array:**
```java
// Declaration
int[] scores; 

// Instantiation (allocating memory)
scores = new int[5]; // An array to hold 5 integers

// Initialization
scores[0] = 98;
scores[1] = 87;

// Declaration, Instantiation, and Initialization in one line
String[] names = {"Ravi", "Priya", "Amit"};
```
A key property of a Java array is `length`, which gives its size. `names.length` would be `3`.

**Multidimensional Array (2-D Array):**
This is an array of arrays, useful for representing grids or matrices.

```java
// A 2x3 matrix
int[][] matrix = {
    {1, 2, 3},  // row 0
    {4, 5, 6}   // row 1
};

// Accessing an element
int element = matrix[1][2]; // Accesses the value 6
```

---

### **Topic Summary & Revision**

*   **Variables & Methods:** The basic building blocks. Remember `String` is a class, not a primitive.
*   **Type Casting:** Java performs **implicit casting** (widening) automatically but requires **explicit casting** (narrowing) for potentially unsafe conversions.
*   **Operators:** Mostly the same as C++, but Java does **not** allow operator overloading.
*   **Control Flow:** `if`, `switch`, `for`, `while` work just like in C++. The **enhanced for loop** (`for-each`) provides a simpler syntax for iterating over collections.
*   **Arrays:** Are objects in Java, created with the `new` keyword. Their size is fixed at creation and can be accessed via the `length` property.

---

### **MCQs for Exam Preparation (Tricky)**

1.  **What is the result of the following Java code snippet?**
    ```java
    int a = 5;
    double b = 2.0;
    System.out.println(a / b);
    ```
    (A) 2
    (B) 2.0
    (C) 2.5
    (D) Compilation Error
    **Answer:** ||(C) 2.5. In the expression `a / b`, the `int` `a` is promoted (widened) to a `double` to match the type of `b`. The division is then performed as floating-point arithmetic (`5.0 / 2.0`), resulting in `2.5`.||
<br>

2.  **Which of the following code snippets will fail to compile?**
```java
// Snippet 1
byte b = 127;
b++;

// Snippet 2
byte c = 50;
c = c * 2;
```
(A) Only Snippet 1
(B) Only Snippet 2
(C) Both Snippet 1 and Snippet 2
(D) Neither will fail to compile.
**Answer:** ||(B) Only Snippet 2. In Snippet 1, 'b++' is a special compound assignment operator that includes an implicit cast, so it compiles. In Snippet 2, the expression 'c \* 2' promotes 'c' to an 'int' (because '2' is an 'int' literal). The result is an 'int', which cannot be assigned back to a 'byte' without an explicit cast: 'c = (byte) (c * 2);'. This is a very tricky rule of arithmetic promotion.||
<br>

3.  **A programmer wants to iterate through an array `String[] names`. Which approach is valid but generally considered the most error-prone due to "off-by-one" errors?**
    (A) `for (String name : names) { ... }`
    (B) `for (int i = 0; i < names.length; i++) { ... }`
    (C) `for (int i = 1; i <= names.length; i++) { ... }`
    (D) `int i = 0; while (i < names.length) { ...; i++; }`
    **Answer:** ||(C) This loop starts at index 1 (missing the first element at index 0) and tries to access 'names[names.length]', which will cause an 'ArrayIndexOutOfBoundsException'. The enhanced for-loop (A) is the safest.||
<br>

4.  **Examine the switch statement below. What will be printed?**
```java
String day = "SUN";
switch (day) {
	case "SAT":
		System.out.print("Weekend ");
	case "SUN":
		System.out.print("Rest ");
	default:
		System.out.print("Day");
}
```
(A) Rest
(B) Rest Day
(C) Weekend Rest Day
(D) Compilation Error
**Answer:** ||(B) Rest Day. The 'switch' will jump to the 'case "SUN":'. Since there is no 'break' statement, execution will "fall through" to the 'default' case, printing "Rest " followed by "Day".||
<br>

5.  **Which statement about Java arrays is FALSE?**
(A) An array is an object and is created on the heap.
(B) The size of an array can be changed after it is created.
(C) An array has a public final member named `length`.
(D) Declaring an array (`int[] arr;`) does not allocate memory for its elements.
**Answer:** ||(B) The size of a Java array is fixed at the time of instantiation ('new int[10]'). To have a collection that can grow or shrink, you must use a class like 'ArrayList' from the Collections Framework.||

---

### **Bonus Tips**

*   **Viva/Interview Tip:** The question about `byte c = c * 2;` (MCQ #2) is a classic trick question to test your understanding of Java's type promotion rules in expressions. Remember that any integer arithmetic involving `byte`, `short`, or `char` promotes the operands to `int` before the calculation.
*   **Exam Tip:** Pay very close attention to `switch` statements without `break` clauses (fall-through behavior) and loops that might go out of bounds. These are common sources for exam questions.
*   **Lab Tip:** When starting out, always use the enhanced `for` loop to iterate over arrays whenever you don't need the index `i`. It's cleaner, more readable, and prevents common `ArrayIndexOutOfBoundsException` errors.

**🔗Links:** [[Java Session 4 - Object Oriented Programming Concepts]]