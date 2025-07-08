### **Sessions 13 & 14: Wrapper Classes and String Class**

Welcome. So far, we've distinguished between [[Java Session 5 - Static, Reference variables and methods#3. Difference Between Reference and Primitive Data Types|primitive types]] (like `int`, `double`) and reference types (objects). However, sometimes we need to treat a primitive as an object, especially when working with collections like `ArrayList` which can only store objects. **Wrapper classes** solve this problem. We will also take a deep dive into the most commonly used class in Java: `String`, and explore its properties and related helper classes.

---

#### **1. Wrapper Classes**

For each of the 8 primitive data types, Java provides a corresponding "wrapper" class in the `java.lang` package.

| Primitive Type | Wrapper Class |
| :--- | :--- |
| `byte` | `Byte` |
| `short` | `Short` |
| `int` | `Integer` |
| `long` | `Long` |
| `float` | `Float` |
| `double` | `Double` |
| `char` | `Character` |
| `boolean`| `Boolean` |

**Boxing and Unboxing:**
*   **Boxing:** The process of converting a primitive value into an object of its corresponding wrapper class.
*   **Unboxing:** The process of converting an object of a wrapper class back to its corresponding primitive value.

In modern Java, this happens automatically. This feature is called **autoboxing** and **auto-unboxing**.

```java
// Autoboxing: The compiler automatically converts the primitive int to an Integer object.
Integer myIntObject = 100; // Same as: Integer myIntObject = Integer.valueOf(100);

// Auto-unboxing: The compiler automatically converts the Integer object back to a primitive int.
int myPrimitive = myIntObject; // Same as: int myPrimitive = myIntObject.intValue();

// A practical example with collections:
List<Integer> numberList = new ArrayList<>();
numberList.add(10); // Autoboxing: int 10 is converted to an Integer object
numberList.add(20);

int firstNumber = numberList.get(0); // Auto-unboxing: Integer object is converted to int
```

> **Quick Question:** Why are wrapper classes necessary in Java?
> **Answer:** Because generic collections (like `ArrayList<T>`) and many other parts of Java's libraries are designed to work with objects (reference types), not primitives. Wrapper classes bridge this gap.

---

#### **2. The `String` Class**

The `String` class is one of the most important and frequently used classes in Java.

**Key Property: Immutability**
A `String` object is **immutable**, which means once it is created, its contents cannot be changed.

When you perform an operation that seems to modify a string, like concatenation, you are not changing the original string. Instead, you are creating a **new** `String` object in memory that contains the result.

```java
String s1 = "Hello";
s1 = s1 + " World"; // This does NOT change the original "Hello" string.

// What happens:
// 1. A new string " World" is created.
// 2. A third string "Hello World" is created by concatenating the two.
// 3. The reference s1 is updated to point to this new "Hello World" object.
// 4. The original "Hello" object is now eligible for garbage collection if there are no other references to it.
```

**Why is `String` immutable?**
*   **Security:** Prevents malicious code from changing string values that are used in security checks.
*   **Thread Safety:** Can be safely shared across multiple threads without risk of modification.
*   **Performance:** Allows the JVM to optimize string handling, for example, by using a **String Constant Pool**.

**String Constant Pool:**
The String Constant Pool is a special memory area in the heap where the JVM stores unique string literals. When you create a string literal (`String s = "Java";`), the JVM checks the pool first. If the string already exists, it returns a reference to the existing object instead of creating a new one.

```java
String a = "Test"; // "Test" is created in the pool. 'a' points to it.
String b = "Test"; // "Test" is found in the pool. 'b' points to the SAME object as 'a'.

System.out.println(a == b); // Output: true

// Using 'new' keyword bypasses the pool and creates a new object directly on the heap.
String c = new String("Test");

System.out.println(a == c); // Output: false
```

---

#### **3. `StringBuffer` and `StringBuilder` Classes**

Because `String` is immutable, performing many modifications can be inefficient (it creates a lot of temporary garbage objects). For situations where you need to perform many modifications to a sequence of characters, Java provides two helper classes:

*   **`StringBuffer`:**
    *   It is **mutable** (its contents can be changed).
    *   It is **thread-safe** (its methods are `synchronized`). This means it is safe to use in a multithreaded environment but comes with a small performance overhead.
*   **`StringBuilder`:**
    *   Also **mutable**.
    *   It is **not thread-safe** (its methods are not `synchronized`).
    *   It is **faster** than `StringBuffer` because it doesn't have the synchronization overhead.

**Rule of Thumb:**
*   If your string will not change, use `String`.
*   If your string will be modified by a single thread, use `StringBuilder` (this is the most common case).
*   If your string will be modified by multiple threads, use `StringBuffer`.

**Example:**
```java
// Inefficient way using String
String result = "";
for (String word : words) {
    result = result + word; // Creates a new object in every iteration
}

// Efficient way using StringBuilder
StringBuilder sb = new StringBuilder();
for (String word : words) {
    sb.append(word); // Modifies the same object in memory
}
String efficientResult = sb.toString(); // Convert to a String at the end
```

---

### **Topic Summary & Revision**

*   **Wrapper Classes:** Provide object representations for primitive types (e.g., `Integer` for `int`), enabling them to be used in object-only contexts like collections.
*   **Autoboxing/Unboxing:** The automatic conversion between primitives and their wrapper types.
*   **`String` Class:** An immutable class for representing character strings. Its immutability provides security and thread safety.
*   **String Constant Pool:** A memory optimization for string literals.
*   **`StringBuffer` vs. `StringBuilder`:** Mutable alternatives to `String` for efficient string manipulation.
    *   `StringBuilder` is faster but not thread-safe (preferred for single-threaded use).
    *   `StringBuffer` is slower but thread-safe (use in multi-threaded scenarios).

---

### **MCQs for Exam Preparation (Tricky)**

1.  **What is the output of the following code?**
```java
Integer i1 = 127;
Integer i2 = 127;
Integer i3 = 128;
Integer i4 = 128;

System.out.println(i1 == i2);
System.out.println(i3 == i4);
```
(A) true, true
(B) false, false
(C) true, false
(D) false, true
**Answer:** ||(C) true, false. This is a very tricky question about a JVM optimization. To save memory, Integer objects created via autoboxing for values between -128 and 127 are cached and reused (similar to the String pool). Therefore, 'i1' and 'i2' point to the same object. The value 128 is outside this cache range, so 'i3' and 'i4' point to two distinct objects on the heap.||
<br>

2.  **A method needs to build a large XML string from multiple pieces of data within a single thread. Which class should be used for the highest performance?**
    (A) `String`
    (B) `StringBuffer`
    (C) `StringBuilder`
    (D) `Character[]`
    **Answer:** ||(C) 'StringBuilder'. Since the string is being heavily modified and the environment is single-threaded, 'StringBuilder' is the optimal choice. It is mutable (unlike 'String') and faster than 'StringBuffer' because it is not synchronized.||
<br>

3.  **After this code executes, what is the value of `s1`?**
```java
String s1 = "Java";
String s2 = s1;
s1.toUpperCase();
System.out.println(s1);
```
(A) JAVA
(B) Java
(C) null
(D) The code produces a compilation error.
**Answer:** ||(B) Java. Because 'String' is immutable, the method 's1.toUpperCase()' does not change the object 's1' points to. It returns a new 'String' object with the value "JAVA", but this returned object is immediately lost because it is not assigned to any reference. The reference 's1' still points to the original "Java" object.||
<br>

4.  **Which of the following lines of code will not compile?**
    (A) `double d = new Double(10.5);`
    (B) `Integer i = 10;`
    (C) `int j = new Integer(10); j++;`
    (D) `Double k = 10;`
    **Answer:** ||(D) 'k' is a 'Double' reference, and '10' is an 'int' literal. While Java can autobox an 'int' to an 'Integer', it cannot directly autobox an 'int' to a 'Double'. You would need to write 'Double k = 10.0;' or 'Double k = (double) 10;'. All other lines are valid examples of auto-unboxing and autoboxing.||
<br>

5.  **Which statement best describes the difference between `StringBuffer` and `StringBuilder`?**
    (A) `StringBuilder` is immutable, while `StringBuffer` is mutable.
    (B) `StringBuffer` methods are synchronized, while `StringBuilder` methods are not.
    (C) `StringBuilder` can only be used for building strings, while `StringBuffer` can also be used for parsing.
    (D) There is no difference; `StringBuilder` is just a newer name for `StringBuffer`.
    **Answer:** ||(B) The core difference is thread safety. 'StringBuffer' is thread-safe (synchronized), making it suitable for multi-threaded access. 'StringBuilder' is not, which removes the overhead of synchronization and makes it faster for single-threaded use cases. Both are mutable.||

---

### **Bonus Tips**

*   **Viva/Interview Tip:** The `Integer` caching question (MCQ #1) is an advanced trick question that interviewers use to gauge the depth of a candidate's JVM knowledge. Knowing about the `-128` to `127` cache is a sign of a well-prepared candidate. The `String` immutability question (MCQ #3) is equally fundamental.
*   **Performance:** Never use the `+` operator to concatenate strings inside a loop. The performance degradation is significant because it creates a new `String` and `StringBuilder` object on every iteration. Always use an explicit `StringBuilder` for loop-based concatenation.
*   **Equality:** Remember the rule from [[Java Session 5 - Static, Reference variables and methods|Session 5]]: for objects, `==` compares references, while `.equals()` compares content. This is especially important for Strings. Always use `.equals()` to compare the content of two strings.

**🔗Links:** [[Java Sessions 15 & 16 - Exception Handling]]