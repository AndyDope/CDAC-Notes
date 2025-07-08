### **Session 12: Garbage Collection**

Welcome to Session 12. In languages like C++, developers are responsible for manually allocating and deallocating memory using `new` and `delete`. Forgetting to deallocate memory leads to **memory leaks**, a serious bug where a program consumes more and more memory over time. Java solves this problem with an automatic process called **Garbage Collection (GC)**.

---

#### **1. Garbage Collection in Java**

**Garbage Collection** is the process by which the Java Virtual Machine (JVM) automatically reclaims memory from objects that are no longer in use. An object is considered "garbage" when it is no longer reachable from any active part of the program.

*   The Garbage Collector is a low-priority background process that runs periodically.
*   It frees the programmer from the burden of manual memory management.
*   It helps prevent memory leaks and dangling pointers (referencing memory that has been freed).

**Analogy: The Smart Janitor**
Imagine the [[Java Session 6 - Constructors, Pass by value, Heap and Stack#3. Heap and Stack Memory|Heap]] is a large workshop with many tools (objects). You and other workers (your program's threads) use these tools.
*   A "reachable" object is a tool that is currently in someone's hand or connected by a cord to an active machine.
*   An "unreachable" object is a tool left lying on the floor, no longer held by anyone or connected to anything.
*   The **Garbage Collector** is a smart janitor who periodically walks through the workshop. He identifies all the tools lying on the floor (unreachable objects) and puts them back in the storeroom (frees the memory). He never touches the tools you are actively using.

---

#### **2. Requesting the JVM to Run Garbage Collection**

You **cannot force** the Garbage Collector to run. It is a process managed entirely by the JVM, which decides the best time to run it based on complex heuristics.

However, you can **suggest** or **request** that the GC run. There is no guarantee it will happen immediately, or at all.

This is done by calling:
`System.gc();`

This is generally considered **bad practice** to call in production code. The JVM is much better at determining the optimal time for garbage collection than a programmer is. Explicitly calling `System.gc()` can introduce unnecessary performance pauses. Its main use is for testing or academic purposes.

> **Quick Question:** What happens when you call `System.gc()` in your code?
> **Answer:** You are suggesting to the JVM that now might be a good time to run the Garbage Collector. There is no guarantee it will run.

---

#### **3. Making an Object Eligible for Garbage Collection**

For an object to be collected, it must become unreachable. Here are the common ways this happens:

##### **a) Nulling a Reference Variable**
If you set the only reference to an object to `null`, the object becomes unreachable (assuming no other references to it exist).
```java
public void myMethod() {
    Employee emp = new Employee("Ravi"); // Object is created on the heap
    // ... emp is used ...
    emp = null; // The reference is nulled. The 'Ravi' object is now eligible for GC.
}
```

##### **b) Re-assigning a Reference Variable**
If you assign a reference variable to a new object, the original object it was pointing to may become unreachable.
```java
Employee emp1 = new Employee("Priya"); // 'Priya' object is created
Employee emp2 = new Employee("Amit");  // 'Amit' object is created

emp1 = emp2; // Now emp1 points to the 'Amit' object.
             // The 'Priya' object is now eligible for GC (assuming no other references).
```

##### **c) Island of Isolation**
This is a more complex scenario where a group of objects reference each other, but the entire group is unreachable from any active part of the program. Modern garbage collectors are smart enough to identify and collect these "islands."
```java
class Test {
    Test other; // A reference to another Test object
}

// In main method:
Test t1 = new Test();
Test t2 = new Test();

t1.other = t2; // t1 points to t2
t2.other = t1; // t2 points to t1 (a circular reference)

// At this point, both t1 and t2 are reachable from main.
t1 = null;
t2 = null;

// Now, the two objects still point to each other, but nothing from the main
// program points to them. They have formed an 'Island of Isolation' and are
// both eligible for GC.
```

> **Quick Question:** If an object is created inside a method, what happens to it after the method finishes executing?
> **Answer:** The local reference variable to the object is destroyed when the method's stack frame is popped. If that was the only reference to the object, the object on the heap becomes eligible for garbage collection.

---

#### **4. The `finalize()` Method**

The `finalize()` method is a special method from the `Object` class. The Garbage Collector calls this method on an object **just before** it is destroyed.

*   **Signature:** `protected void finalize() throws Throwable`
*   **Purpose:** Its intended purpose was to perform cleanup activities, such as closing file handles or database connections, before an object is garbage collected.

**IMPORTANT: The `finalize()` method is deprecated and should NOT be used.**
*   **Unpredictable:** There is no guarantee *when* or even *if* `finalize()` will be called. The program might exit before the GC ever runs.
*   **Performance Issues:** It can slow down garbage collection.
*   **Better Alternatives:** For resource cleanup, modern Java provides much better and more reliable mechanisms like the **`try-with-resources`** statement.

We learn about `finalize()` for historical context and to understand legacy code, but you should not write new code that uses it.

---

### **Topic Summary & Revision**

*   **Garbage Collection (GC):** The JVM's automatic process of reclaiming memory from unreachable objects.
*   **Unreachable Object:** An object that can no longer be accessed through any active reference in the program.
*   **Making Objects Eligible:** This can happen by nulling references, re-assigning references, or creating an "island of isolation."
*   **`System.gc()`:** A *suggestion* to the JVM to run the GC; it is not a command. Using it is discouraged.
*   **`finalize()` Method:** A deprecated method called by the GC before destroying an object. It is unreliable and should be avoided in favor of modern resource management techniques like `try-with-resources`.

---

### **MCQs for Exam Preparation (Tricky)**

1.  **Which of the following statements about Garbage Collection in Java is TRUE?**
    (A) Calling `System.gc()` guarantees that all garbage objects will be immediately collected.
    (B) The primary trigger for Garbage Collection is when the stack memory is full.
    (C) An object becomes eligible for garbage collection when its `finalize()` method is called.
    (D) An object becomes eligible for garbage collection when it is no longer reachable through any chain of references from an active thread.
    **Answer:** ||(D) This is the definition of a garbage object. Reachability from a "GC Root" (like an active thread's stack) is how the collector determines if an object is still in use. 'finalize()' is called after an object is already marked for collection (C is backward). GC deals with Heap memory (B is wrong). 'System.gc()' is only a suggestion (A is wrong).||
<br>

2.  **Consider the following code. After line 5, how many objects are eligible for Garbage Collection?**
```java
1.  String s1 = new String("a");
2.  String s2 = new String("b");
3.  String s3 = s1;
4.  s1 = new String("c");
5.  s2 = null;
```
(A) 0
(B) 1
(C) 2
(D) 3
**Answer:** ||(B) 1. Let's trace it: (1.)After line 2: 2 objects ('a', 'b'). (2.)Line 3: 's3' now also points to object 'a'. (3.)Line 4: 's1' now points to a new object 'c'. Object 'a' is still referenced by 's3', so it's not garbage. (4.)Line 5: 's2' is nulled. The object 'b' it was pointing to now has no references. (5.)Result: Only object 'b' is eligible for GC.||
<br>

3.  **Why is the use of the `finalize()` method heavily discouraged in modern Java development?**
    (A) It can only be used to clean up memory, which the GC already does.
    (B) Its execution is not guaranteed, making it unreliable for critical resource cleanup.
    (C) It must be declared `public`, which breaks encapsulation.
    (D) It can only be overridden once in an inheritance hierarchy.
    **Answer:** ||(B) The biggest problem with 'finalize()' is its unpredictability. You can't rely on it to close a file or a network socket because it might run much later, or never at all. This makes it unsuitable for deterministic resource management. It is also declared 'protected', not 'public' (C is wrong).||
<br>

4.  **What is an "Island of Isolation"?**
    (A) A special memory area in the JVM reserved for objects that cannot be garbage collected.
    (B) A group of objects that reference each other but have no external references from the running program.
    (C) A programming error where a thread becomes deadlocked and isolated from the main application.
    (D) A single object on the heap that has no references pointing to it.
    **Answer:** ||(B) This describes the specific scenario where objects form a self-referencing cluster that is, as a whole, unreachable. A single unreferenced object (D) is the simplest case of garbage, not an "island".||
<br>

5.  **A developer writes a class to manage a database connection. What is the modern, recommended approach for ensuring the connection is always closed?**
    (A) Place the `connection.close()` call in the class's `finalize()` method.
    (B) Rely on the Garbage Collector to automatically close the connection when the object is collected.
    (C) Implement the `AutoCloseable` interface and use a `try-with-resources` block.
    (D) Explicitly call `System.gc()` after the connection is no longer needed.
    **Answer:** ||(C) The 'try-with-resources' statement, introduced in Java 7, is the standard, reliable, and deterministic way to manage resources like files, streams, and database connections. It guarantees that the 'close()' method will be called when the block is exited, regardless of whether an exception was thrown.||

---

### **Bonus Tips**

*   **Viva/Interview Tip:** A good interview answer about GC demonstrates that you know you don't control it. Emphasize that your job as a developer isn't to *manage* GC, but to *write code that allows the GC to work efficiently*. This means not holding on to object references longer than necessary (e.g., nulling them out in long-lived objects when they are no longer needed).
*   **Performance:** The JVM has many different garbage collectors (e.g., Serial, Parallel, G1, ZGC), each optimized for different workloads (e.g., low latency vs. high throughput). While you don't need to know the details for this course, being aware that these exist shows a deeper understanding of the Java platform.
*   **Avoid `finalize()`:** To reiterate, never use `finalize()` for new code. If you see it in legacy code, recognize its purpose but be aware of its flaws. The correct pattern for resource management is `try-with-resources`.

**🔗Links:** [[Java Sessions 13 & 14 - Wrapper Classes and String Class]]