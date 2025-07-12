## **Session 5: Static, Reference Variables and Methods**

Welcome to Session 5. In our last session, we discussed instance variables, which belong to each individual object. Now, we'll introduce **static** members, which belong to the class itself and are shared by all objects. We will also formally introduce **reference types** and contrast them with the primitive types we've already seen.

---

#### **1. Static Variables and Methods**

The `static` keyword in Java creates members that are associated with the **class**, not with any specific instance (object).

**Static Variables (Class Variables):**
*   There is only **one copy** of a static variable per class, regardless of how many objects are created.
*   All objects of the class share this single copy.
*   They are created when the class is loaded into memory, even before any objects are instantiated.

**Analogy:**
*   **Instance variable (`name`):** Like the name on an employee's ID badge. Each employee (object) has their own unique badge.
*   **Static variable (`companyName`):** Like the company name printed on all ID badges. It's the same for every employee (object) and is a property of the company (class) itself.

**Static Methods:**
*   A method that belongs to the class and can be called directly on the class name, without creating an object.
*   **Crucial Rule:** A static method can only access other static members (variables or methods) of the class directly. It **cannot** access non-static (instance) members because it doesn't have a specific object (`this`) to work with.

**Example:**
```java
class Employee {
    // Instance variable: each employee object has its own name
    String name;
    
    // Static variable: shared by all employee objects
    static String companyName = "CDAC Corp";

    // Static method
    public static void displayCompany() {
        System.out.println("Company: " + companyName);
        // The line below would cause a compilation error:
        // System.out.println("Name: " + name); // Error: Cannot access non-static field 'name' from a static context
    }
}

public class CompanyDemo {
    public static void main(String[] args) {
        // Accessing static members using the class name
        Employee.displayCompany(); // Output: Company: CDAC Corp
        System.out.println("All employees work at: " + Employee.companyName);

        Employee emp1 = new Employee();
        emp1.name = "Ravi";
        
        Employee emp2 = new Employee();
        emp2.name = "Priya";

        // Although possible, it's bad practice to access static members via an object reference
        // System.out.println(emp1.companyName); // Works, but should be Employee.companyName

        // If we change the static variable, it changes for everyone
        Employee.companyName = "Advanced Computing Training School";
        System.out.println("Company name changed to: " + emp2.companyName);
    }
}
```

> **Quick Question:** Why can't a `static` method access an instance variable?
> **Answer:** Because a `static` method is associated with the class, not a specific object. It doesn't know *which* object's instance variable to access. There could be zero or a thousand objects.

---

#### **2. Introduction to Reference Data Types**

We've seen Java's 8 [[Java Session 1 - Introduction to Java#5. Working with Primitive Data Types|primitive types]]. Every other type in Java is a **reference type**. This includes all classes (like `String`, `Employee`), interfaces, and arrays.

**Reference Variables:**
A reference variable does not store the object itself. Instead, it stores the **memory address** (or a "reference") where the object is located on the heap.

**Analogy:**
*   **Primitive variable (`int x = 10;`):** A small box labeled `x` that directly contains the value `10`.
*   **Reference variable (`Dog myDog = new Dog();`):** A small piece of paper labeled `myDog` that contains the *address* of a dog house (the object on the heap). The dog house itself is a separate, larger structure.

---

#### **3. Difference Between Reference and Primitive Data Types**

This is one of the most important distinctions in Java.

| Feature | Primitive Types (`int`, `double`, etc.) | Reference Types (`String`, `Employee`, arrays) |
| :--- | :--- | :--- |
| **Storage** | Stores the actual value directly. | Stores the memory address of an object. |
| **Memory** | Stored on the **stack**. | The reference variable is on the stack, but the object it points to is on the **heap**. |
| **Default Value** | `0` for numbers, `'\u0000'` for char, `false` for boolean. | `null`. |
| **Comparison (`==`)** | Compares the actual values. | Compares the memory addresses (checks if two references point to the *exact same* object). |
| **Passing to Methods** | Passed by **value** (a copy of the value is passed). | The reference is passed by **value** (a copy of the *address* is passed). |

**Example of `==` Comparison:**
```java
// Primitive comparison
int a = 10;
int b = 10;
// System.out.println(a == b); // Output: true (values are equal)

// Reference comparison
String s1 = new String("Hello");
String s2 = new String("Hello");
// System.out.println(s1 == s2); // Output: false!
// Explanation: s1 and s2 point to two different objects on the heap, even though they contain the same text.
// To compare the contents of objects, you must use the .equals() method.
// System.out.println(s1.equals(s2)); // Output: true
```

> **Quick Question:** You have two `Employee` references, `emp1` and `emp2`. If `emp1 == emp2` evaluates to `true`, what does this mean?
> **Answer:** It means that `emp1` and `emp2` are pointing to the exact same `Employee` object in memory.

---

#### **4. Difference Between Reference Variable and Static Variable**

This can be a point of confusion. Let's clarify. These concepts are orthogonal (independent).

*   **Reference vs. Primitive** is about **what the variable holds** (an address vs. a value).
*   **Static vs. Instance** is about **who the variable belongs to** (the class vs. an object).

You can have combinations:
*   `int x;` -> Primitive, instance variable.
*   `static int y;` -> Primitive, static variable.
*   `String s;` -> Reference, instance variable.
*   `static String t;` -> Reference, static variable.

---

### **Topic Summary & Revision**

*   **`static` Keyword:** Creates members that belong to the class, not to any object.
*   **Static Variables:** One copy shared by all objects of the class.
*   **Static Methods:** Called using the class name (e.g., `ClassName.method()`). Cannot access non-static members.
*   **Reference Types:** All non-primitive types (classes, arrays). Variables hold a memory address, not the object itself.
*   **Stack vs. Heap:** Primitives and reference variables live on the stack; all Objects live on the heap.
*   **`==` vs. `.equals()`:** For objects, `==` compares memory addresses, while `.equals()` (if properly implemented) compares the internal contents.

---

### **MCQs for Exam Preparation (Tricky)**

1.  **Examine this code. What is the output?**
```java
class Counter {
	int count = 0;
	static int staticCount = 0;
	
	Counter() {
		count++;
		staticCount++;
	}
}
public class Test {
	public static void main(String[] args) {
		Counter c1 = new Counter();
		Counter c2 = new Counter();
		Counter c3 = new Counter();
		System.out.println(c3.count + " " + Counter.staticCount);
	}
}
```
(A) 3 3
(B) 1 3
(C) 1 1
(D) 3 1
**Answer:** ||(B) 1 3. 'count' is an instance variable, so each object gets its own copy. When the 'c3' constructor runs, its personal 'count' becomes 1. 'staticCount' is a class variable shared by all objects. It is incremented three times, once for each object creation, so its final value is 3.||
<br>

2.  **Which line of code, if inserted into the `main` method of class `X`, will fail to compile?**
```java
class X {
	int a;
	static int b;
	void instanceMethod() {}
	static void staticMethod() {}
	
	public static void main(String[] args) {
		// Line to be inserted here
	}
}
```
(A) `b = 20;`
(B) `staticMethod();`
(C) `a = 10;`
(D) `X obj = new X(); obj.a = 10;`
**Answer:** ||(C) 'a = 10;'. The 'main' method is 'static'. It cannot directly access the non-static (instance) variable 'a'. It would need to do so through an object reference, as shown in option (D), which is valid. Options (A) and (B) are valid because they access other static members.||
<br>

3.  **What is the output of this code?**
```java
public class TestRef {
	public static void main(String[] args) {
		StringBuilder sb1 = new StringBuilder("Java");
		StringBuilder sb2 = sb1;
		sb1.append("Rocks");
		
		System.out.println(sb1 + " " + sb2);
	}
}
```
(A) JavaRocks Java
(B) Java JavaRocks
(C) JavaRocks JavaRocks
(D) Java Java
**Answer:** ||(C) JavaRocks JavaRocks. This demonstrates how references work. 'sb2' is assigned the same reference (address) as 'sb1'. They both point to the same 'StringBuilder' object on the heap. When 'sb1' is used to modify the object, 'sb2' sees the same change because it's the same object.||
<br>

4.  **When are static variables of a class initialized?**
    (A) When the first object of the class is created.
    (B) Each time an object of the class is created.
    (C) When the class is loaded into the JVM.
    (D) When the constructor is called.
    **Answer:** ||(C) Static variables are initialized when the class itself is loaded by the ClassLoader, which happens before any objects are created or any constructors are run.||
<br>
**5.  Given `String str1 = "test";` and `String str2 = new String("test");`, which statement is true?**
    (A) `str1 == str2` is true and `str1.equals(str2)` is true.
    (B) `str1 == str2` is false and `str1.equals(str2)` is true.
    (C) `str1 == str2` is false and `str1.equals(str2)` is false.
    (D) `str1 == str2` is true and `str1.equals(str2)` is false.
    **Answer:** ||(B) 'str1 == str2' is false and 'str1.equals(str2)' is true. This is a classic trick question about the String constant pool. 'str1 = "test"' uses a literal, and the JVM places this string in a special memory area called the "String constant pool." 'str2 = new String("test")' explicitly creates a new object on the heap. Therefore, 'str1' and 'str2' have different memory addresses ('\==' is false), but their content is the same ('.equals()' is true).||

---

### **Bonus Tips**

*   **Viva/Interview Tip:** Be ready to explain the difference between `static` and `final` and `static final`. (We will cover `final` soon, but as a preview: `static` means one copy per class; `final` means it cannot be changed. `static final` creates a true constant shared by all objects).
*   **Exam Tip:** The `==` vs. `.equals()` question with `String` objects (like MCQ #5) is one of the most frequently asked Java questions in exams and interviews. Master the concept of the String constant pool.
*   **Lab Tip:** Use `static` variables for constants or data that is truly universal to all objects of a class. For example, a `Math` utility class might have `public static final double PI = 3.14159;`. Use `static` methods for utility functions that don't depend on the state of a specific object, like `Math.max(a, b)`.

**🔗Links:** [[Java Session 6 - Constructors, Pass by value, Heap and Stack]]