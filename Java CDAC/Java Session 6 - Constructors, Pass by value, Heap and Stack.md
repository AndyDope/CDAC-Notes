### **Session 6: Constructors, Pass by value, Heap and Stack**

Welcome to Session 6. We have learned that the `new` keyword creates an object, but what happens right after? This is where **constructors** come in. They are special methods responsible for initializing the state of a new object. We will also demystify the "pass-by-value vs. pass-by-reference" debate in Java and visualize how memory is organized.

---

#### **1. Constructors**

A **constructor** is a special block of code, similar to a method, that is called when an instance of an object is created. Its primary job is to initialize the fields of the object.

**Rules for a Constructor:**
1.  A constructor must have the **same name** as the class.
2.  A constructor **must not** have an explicit return type (not even `void`).
3.  A constructor is called automatically when an object is created with the `new` keyword.

**Types of Constructors:**
*   **Default Constructor:** If you don't provide any constructor in your class, the Java compiler provides one for you. This default constructor has no parameters and an empty body.
*   **No-Argument Constructor:** A constructor that you write yourself, which takes no arguments.
*   **Parameterized Constructor:** A constructor that accepts one or more parameters to initialize the object's fields with specific values.

**Example: Using Constructors**
```java
class Employee {
    String name;
    int employeeId;

    // 1. A No-Argument Constructor
    public Employee() {
        this.name = "Unknown";
        this.employeeId = 0;
        System.out.println("No-arg constructor called. Employee created with default values.");
    }

    // 2. A Parameterized Constructor
    public Employee(String name, int employeeId) {
        this.name = name; // 'this.name' refers to the instance variable
        this.employeeId = employeeId;
        System.out.println("Parameterized constructor called. Employee '" + name + "' created.");
    }
}

public class TestEmployee {
    public static void main(String[] args) {
        // Calls the no-argument constructor
        Employee emp1 = new Employee(); 
        
        // Calls the parameterized constructor
        Employee emp2 = new Employee("Priya", 101);
    }
}
```
**Important:** If you define *any* constructor (e.g., a parameterized one), the compiler **will not** provide a default constructor for you. If you still need a no-argument constructor, you must define it yourself.

> **Quick Question:** What is the main purpose of a constructor?
> **Answer:** To initialize the state (fields) of an object when it is created.

---

#### **2. Pass-by-value vs. Pass-by-reference**

This is a critical concept and a frequent source of confusion.
**Java is strictly pass-by-value.**

What does this mean?
When you pass a variable to a method, a **copy** of the variable's value is passed. The method works on the copy, not the original.

*   **For Primitive Types:** A copy of the actual value is passed. Changes inside the method do not affect the original variable.

*   **For Reference Types:** A copy of the **reference (memory address)** is passed. Both the original reference and the copied reference point to the *exact same object* on the heap. Therefore, if the method uses its copied reference to modify the object, the change is visible through the original reference. However, if the method re-assigns its reference to a *new* object, it does not affect the original reference variable.

**Example Clarification:**
```java
class Wallet {
    int money;
    Wallet(int money) { this.money = money; }
}

public class PassByValueDemo {
    public static void main(String[] args) {
        // --- Primitive Example ---
        int primitiveValue = 10;
        modifyPrimitive(primitiveValue);
        System.out.println("Original primitive value: " + primitiveValue); // Output: 10

        // --- Reference Example ---
        Wallet myWallet = new Wallet(100);
        modifyReference(myWallet);
        System.out.println("Original wallet money: " + myWallet.money); // Output: 500
    }

    public static void modifyPrimitive(int valueCopy) {
        valueCopy = 20; // Modifies the copy, original is unaffected
    }
    
    public static void modifyReference(Wallet walletRefCopy) {
        // walletRefCopy holds a copy of the address to the original Wallet object.
        // It's pointing to the SAME object as myWallet.
        
        // 1. Modifying the object's state: This change WILL be visible outside.
        walletRefCopy.money = 500;
        
        // 2. Re-assigning the reference: This change will NOT be visible outside.
        // This makes walletRefCopy point to a brand new object.
        // The original myWallet reference is unaffected.
        walletRefCopy = new Wallet(1000); 
    }
}
```

> **Quick Question:** If a method receives a reference to an `Employee` object and changes that employee's salary, will the change be visible back in the calling method?
> **Answer:** Yes, because both the original and copied references point to the same `Employee` object on the heap.

---

#### **3. Heap and Stack Memory**

Java's memory is divided into several areas, but the two most important for us are the Stack and the Heap.

*   **Stack:**
    *   Used for **static memory allocation** and execution threads.
    *   Stores **primitive variables** and **reference variables**.
    *   Each method call creates a new "stack frame" which holds its local variables.
    *   Memory is managed automatically in a LIFO (Last-In, First-Out) manner. When a method finishes, its stack frame is popped off, and the memory is reclaimed.
    *   It is fast but limited in size.

*   **Heap:**
    *   Used for **dynamic memory allocation**.
    *   **All objects** (created with `new`) and arrays are stored here.
    *   This memory is globally accessible from anywhere in the application.
    *   Memory is managed by the **Garbage Collector**. It is slower but much larger than the stack.

**Visualization:**
When `Wallet myWallet = new Wallet(100);` is executed inside `main`:
1.  A reference variable `myWallet` is created on the **stack** (in `main`'s stack frame).
2.  A `Wallet` object is created on the **heap**.
3.  The memory address of the heap object is placed into the `myWallet` variable on the stack.



---

### **Topic Summary & Revision**

*   **Constructor:** A special method with the same name as the class and no return type. It initializes a newly created object.
*   **Pass-by-value:** Java always passes copies of variables to methods. For primitives, it's a copy of the value. For references, it's a copy of the memory address.
*   **Modifying Objects:** You can change an object's state from within a method (via a copied reference), but you cannot change which object the original reference variable points to.
*   **Stack Memory:** Holds primitive and reference variables for local method execution. Fast and LIFO.
*   **Heap Memory:** Holds all objects and arrays. Slower, larger, and managed by the Garbage Collector.

---
Understood. I will reformat the previous MCQ section to use single quotes for code elements inside the hidden answer blocks (`||...||`) and will adhere to this format for all future responses.

Here is the updated MCQ section for Session 6.

---

### **MCQs for Exam Preparation (Tricky)**

1.  **A class `Book` does not have any constructors explicitly defined. What happens when a developer writes `Book b = new Book();`?**
    (A) A compilation error occurs because no constructor is found.
    (B) The code compiles, and a default constructor provided by the compiler is called.
    (C) A `NullPointerException` is thrown at runtime.
    (D) The code compiles, but the object `b` will be `null`.
    **Answer:** ||(B) If a class has no user-defined constructors, the Java compiler automatically inserts a public, no-argument constructor (the 'default constructor') that calls the superclass's constructor.||
<br>

2.  **Consider this code. What will be the output?**
```java
public class Swapper {
	public static void swap(Integer i, Integer j) {
		Integer temp = i;
		i = j;
		j = temp;
	}
	public static void main(String[] args) {
		Integer a = 10;
		Integer b = 20;
		swap(a, b);
		System.out.println(a + " " + b);
	}
}
```
(A) 20 10
(B) 10 20
(C) null null
(D) Compilation Error
**Answer:** ||(B) 10 20. This is a very tricky question. 'Integer' is a reference type (a wrapper class), but it is also immutable. When you do 'i = j', you are not changing the object 'i' points to; you are changing the local reference 'i' to point to what 'j' is pointing to. The original references 'a' and 'b' in 'main' are completely unaffected. The swap happens only to the copies of the references inside the 'swap' method.||
<br>

3.  **Where are the `name` and `company` variables stored in memory for the following code?**
```java
class Employee {
	String name; // Instance variable
	static String company = "CDAC"; // Static variable
}
public class Test {
	public static void main(String[] args) {
		Employee emp = new Employee();
	}
}
```
(A) `name` on Stack, `company` on Heap.
(B) Both on the Heap.
(C) `name` on Heap (as part of the `emp` object), `company` in a special Method Area/Metaspace.
(D) Both on the Stack.
**Answer:** ||(C) The 'emp' object is created on the Heap, so its instance field 'name' lives with it on the Heap. Static variables like 'company' are stored in a separate part of memory (often called Method Area or Metaspace in modern JVMs) along with other class-level data.||
<br>

4.  **A class has a single constructor defined as `public Car(String model)`. Which statement will cause a compilation error?**
    (A) `Car c1 = new Car("Sedan");`
    (B) `Car c2;`
    (C) `Car c3 = new Car();`
    (D) Both B and C.
    **Answer:** ||(C) Because a parameterized constructor was provided, the compiler does not add a default no-argument constructor. Therefore, 'new Car()' is an invalid call. 'Car c2;' is just a declaration of a reference variable and does not call any constructor, so it is valid.||
<br>

5.  **Which of the following is NOT stored on the Heap?**
    (A) An object of type `String`.
    (B) An array `new int[10]`.
    (C) A local variable `int x = 5;` inside a method.
    (D) An object created from `new Employee()`.
    **Answer:** ||(C) Local variables, which include primitives and reference variables themselves (but not the objects they point to), are stored on the stack in the current method's stack frame.||
---

### **Bonus Tips**

*   **Viva/Interview Tip:** The "Is Java pass-by-value or pass-by-reference?" question is extremely common. The correct, nuanced answer is: **"Java is strictly pass-by-value. For primitives, the value is copied. For objects, the reference (address) is copied."** Explaining this with the wallet/house analogy demonstrates a deep understanding. The `Integer` swap (MCQ #2) is the expert-level follow-up to this question.
*   **Exam Tip:** Be very careful with questions involving multiple constructors. Remember the rule: if you write *any* constructor, the compiler *will not* provide a default one. This is a frequent trap.
*   **Lab Tip:** Always initialize your object's fields in a constructor. Relying on default values (`0`, `null`, `false`) can lead to `NullPointerException` and other bugs. A good constructor ensures an object is created in a valid, usable state.

**🔗Links:** [[Java Session 7 - Inheritance, Association, Aggregation and Composition]]