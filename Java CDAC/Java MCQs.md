This page contains a comprehensive set of Multiple Choice Questions, organized by topic, to help you prepare for your exams. The questions range from moderate to difficult to test your in-depth understanding.

Practice these questions to solidify your understanding of Java concepts. For best results, attempt to answer them before checking the key.

**🔗 Back to [[Core Java Overview]]**

---

### **Topic 1: Introduction & Basic Programming Concepts (Sessions 1-3)**

1.  What is the result of compiling and running the following Java code?
    ```java
    public class Test {
        public static void main(String... args) {
            int a = 5;
            int b = 2;
            double c = a / b;
            System.out.println(c);
        }
    }
    ```
    - [ ] 2.5
    - [x] 2.0
    - [ ] 2
    - [ ] Compilation Error

<br>


2.  Which of the following `main` method signatures is NOT a valid entry point for a Java application?
    - [ ] `public static void main(String[] a)`
    - [ ] `final public static void main(String... arguments)`
    - [x] `public static int main(String[] args)`
    - [ ] `static public void main(String[] args)`

<br>

3.  Examine this `switch` statement. What will be the output?
    ```java
    int code = 2;
    switch (code) {
        case 1:
            System.out.print("A");
        case 2:
            System.out.print("B");
        case 3:
            System.out.print("C");
            break;
        case 4:
            System.out.print("D");
    }
    ```
    - [ ] B
    - [x] BC
    - [ ] BCD
    - [ ] ABC

<br>

4.  What is the result of this code snippet?
    ```java
    byte a = 50;
    a = a * 2; // Line 2
    System.out.println(a);
    ```
    - [ ] 100
    - [ ] The code runs, but prints a garbage value due to overflow.
    - [ ] A runtime exception is thrown.
    - [x] The code fails to compile at Line 2.

<br>

5.  If a Java source file is named `MyApplication.java`, which of the following is true?
    - [ ] It must contain a class named `MyApplication`, and this class must be `public`.
    - [ ] It can contain any number of `public` classes.
    - [x] If it contains a `public` class, that class must be named `MyApplication`.
    - [ ] It must contain only one class, named `MyApplication`.

<br>

**Answer Key (Topic 1):**
1.  **B**: In the expression `a / b`, both operands are integers. Therefore, Java performs integer division, which truncates the result (`5 / 2` becomes `2`). This integer `2` is then promoted to a double `2.0` when assigned to `c`.
2.  **C**: A valid `main` method must have a return type of `void`. Returning an `int` or any other type makes it an invalid entry point for the JVM. The other options are all valid syntactical variations.
3.  **B**: The `switch` statement will jump to `case 2` and print "B". Since there is no `break` statement in `case 2`, execution will "fall through" to `case 3`, print "C", and then hit the `break`, exiting the switch.
4.  **D**: The expression `a * 2` involves a `byte` and an `int` literal (`2`). Due to arithmetic promotion rules, `a` is promoted to an `int`. The result of the multiplication is an `int`. You cannot assign an `int` back to a `byte` variable without an explicit cast (`a = (byte) (a * 2);`), so this causes a compilation error.
5.  **C**: A Java source file can contain at most one `public` class. If such a class exists, its name must match the filename. It can also contain any number of non-public (default-access) classes.

---

### **Topic 2: Core OOP Concepts (Sessions 4-6)**

1.  Consider the following code. What is its output?
    ```java
    class Bulb {
        static boolean on = false;
        Bulb() {
            on = !on;
        }
    }
    public class Test {
        public static void main(String[] args) {
            Bulb b1 = new Bulb();
            Bulb b2 = new Bulb();
            System.out.println(Bulb.on);
        }
    }
    ```
    - [ ] true
    - [x] false
    - [ ] It prints `true` or `false` unpredictably.
    - [ ] Compilation Error

<br>

2.  A class `Product` has only one constructor defined: `public Product(String name)`. Which statement is true?
    - [ ] The compiler will provide a default no-argument constructor.
    - [ ] `Product p = new Product();` will compile successfully.
    - [x] A subclass of `Product` must explicitly call `super(someName)` in its constructor.
    - [ ] `Product` cannot be extended.

<br>

3.  What is the output of this code?
    ```java
    class Value {
        public int i = 15;
    }
    public class Test {
        public static void main(String args[]) {
            Test t = new Test();
            t.first();
        }
        public void first() {
            int i = 5;
            Value v = new Value();
            v.i = 25;
            second(v, i);
            System.out.println(v.i);
        }
        public void second(Value v, int i) {
            i = 0;
            v.i = 20;
            Value val = new Value();
            v = val;
            System.out.println(v.i + " " + i);
        }
    }
    ```
    - [ ] 15 0
    - [ ] 20 0
    - [ ] 25 0
    - [x] The output is `15 0` followed by `20` on the next line.

<br>

4.  Which principle is best demonstrated by hiding the internal state of an object and requiring all interaction to be performed through an object's methods?
    - [ ] Inheritance
    - [ ] Polymorphism
    - [x] Encapsulation
    - [ ] Abstraction

<br>

5.  Where are the variables `emp` and `id` stored?
    ```java
    public class Test {
        public void process() {
            Employee emp = new Employee(); // Line 1
            int id = 101;                  // Line 2
        }
    }
    ```
    - [ ] Both `emp` and `id` are on the Heap.
    - [ ] `emp` is on the Stack, `id` is on the Heap.
    - [x] Both are on the Stack, but `emp` holds a reference to an object on the Heap.
    - [ ] `id` is on the Stack, `emp` is on the Heap.

<br>

**Answer Key (Topic 2):**
1.  **B**: `on` is a `static` variable, so there is only one copy shared by all `Bulb` objects. Initial value is `false`. `new Bulb()` flips it to `true`. `new Bulb()` again flips it back to `false`. The final value is `false`.
2.  **C**: Because a constructor was provided, the compiler will not create a default one. Any subclass constructor, by default, tries to call `super()`. Since the `Product` class does not have a no-argument constructor, the subclass must explicitly call `super("some-name")` to satisfy the parent's constructor requirement.
3.  **D**: The `second` method prints first. It receives a copy of the reference `v`. `v.i = 20` changes the original object. `v = val` reassigns the local reference `v` to a new object whose `i` is 15. Then it prints `15 0`. The `first` method then continues. Its `v` still points to the original object, whose `i` was changed to 20. So it prints `20`. The output is `15 0` then `20`.
4.  **C**: This is the definition of Encapsulation, specifically data hiding. It protects an object from unwanted access.
5.  **C**: Local variables (`emp` and `id`) are always stored on the Stack. `id` is a primitive, so its value is on the stack. `emp` is a reference variable, so the variable itself is on the stack, but it holds a memory address that *points* to the `Employee` object, which lives on the Heap.

---

### **Topic 3: Advanced OOP & Design (Sessions 7-8)**

1.  A `Car` "has-a" relationship with an `Engine`, where the `Engine` is created as part of the `Car` and cannot exist without it. This is best modeled as:
    - [ ] Inheritance
    - [ ] Aggregation
    - [ ] Association
    - [x] Composition

<br>

2.  An interface can contain:
    - [ ] `private` instance fields and `protected` methods.
    - [ ] A constructor and instance initialization blocks.
    - [x] `static`, `default`, and `private` methods (in modern Java).
    - [ ] Only `public abstract` methods and `public` instance fields.

<br>

3.  Consider the hierarchy `class C extends B`, `class B extends A`. What is the result of this code?
    ```java
    A a = new B();
    B b = (B) a;
    C c = (C) b;
    ```
    - [ ] The code compiles and runs without error.
    - [ ] The code fails to compile.
    - [x] The code compiles but throws a `ClassCastException` at the last line.
    - [ ] The code compiles but throws a `NullPointerException`.

<br>

4.  Which statement is true about an `abstract` class?
    - [ ] An abstract class must contain at least one abstract method.
    - [ ] An abstract class cannot have a constructor.
    - [x] A class can be declared `abstract` even if it has no abstract methods.
    - [ ] A class can extend multiple abstract classes.

<br>

5.  What is the main purpose of upcasting (e.g., `Vehicle v = new Car()`)?
    - [ ] To gain access to the specific methods of the subclass (`Car`).
    - [x] To achieve polymorphism by allowing code to work with objects of a general supertype.
    - [ ] To save memory because superclass references are smaller.
    - [ ] To prevent the object from being garbage collected.

<br>

**Answer Key (Topic 3):**
1.  **D**: Composition is the strong "has-a" or "part-of" relationship where the lifecycle of the part is tied to the whole.
2.  **C**: Since Java 8 and 9, interfaces have become more powerful. They can have `static` methods (utility functions), `default` methods (for backward compatibility), and even `private` methods (to share code between default methods). They still cannot have instance fields or constructors.
3.  **C**: The object `a` is, at runtime, an instance of `B`. Downcasting it to `B` is fine. However, a `B` is not an instance of `C` (`C` is a subclass of `B`, not the other way around). Therefore, trying to downcast `b` (which points to a `B` object) to `C` will fail with a `ClassCastException`.
4.  **C**: A class can be declared `abstract` to prevent its instantiation, even if it provides a full implementation for all its methods. This is often done for base classes in a framework that are not meant to be used directly.
5.  **B**: Upcasting is the cornerstone of polymorphism. It allows you to write flexible methods that can operate on any object that "is-a" `Vehicle`, without needing to know the specific subtype at compile time.

---

### **Topic 4: Keywords, Modern Java & Inner Classes (Sessions 9-10)**

1.  A method is declared as `public void process(final List<String> list)`. What is true about the `list` parameter inside the method?
    - [x] The `list` reference cannot be changed to point to a new list.
    - [ ] The contents of the `list` cannot be changed (e.g., `list.add()` is not allowed).
    - [ ] Both the reference and the contents are immutable.
    - [ ] The `final` keyword is ignored for reference type parameters.

<br>

2.  Which statement about a `static` nested class is correct?
    - [ ] It can directly access instance (non-static) members of its outer class.
    - [ ] An instance of it can only be created from within an instance of the outer class.
    - [x] It behaves like a regular top-level class but is namespaced inside another class for grouping.
    - [ ] It cannot be declared `private`.

<br>

3.  Which of these is NOT a functional interface?
    - [ ] `interface Runner { void run(); }`
    - [x] `interface Calculator { int calc(int x, int y); int calc(int x); }`
    - [ ] `interface Predicate<T> { boolean test(T t); }`
    - [ ] `interface Task extends Runnable { }`

<br>

4.  A `final` class can...
    - [ ] not be instantiated.
    - [ ] have methods that are overridden.
    - [x] not be extended.
    - [ ] only contain `final` methods.

<br>

5.  What is the modern, most concise way to implement a `Runnable`?
    - [ ] A `public` top-level class that implements `Runnable`.
    - [ ] A static nested class that implements `Runnable`.
    - [ ] An anonymous inner class.
    - [x] A lambda expression.

<br>

**Answer Key (Topic 4):**
1.  **A**: The `final` keyword on a reference variable (parameter or local) makes the *reference* constant. This means you cannot reassign `list` to point to a different object (e.g., `list = new ArrayList<>()`). However, you are still free to modify the object that the reference points to (e.g., `list.add("item")`).
2.  **C**: A `static` nested class is not tied to an instance of the outer class. It's essentially a top-level class that is just declared inside another. It can only access `static` members of the outer class.
3.  **B**: A functional interface must have *exactly one* abstract method. `Calculator` has two abstract methods with different signatures, so it is not a functional interface and cannot be used with a lambda. `Task` inherits the single abstract `run()` method from `Runnable`, so it is a functional interface.
4.  **C**: The sole purpose of declaring a class `final` is to prevent inheritance (subclassing). The `String` class is a prime example.
5.  **D**: Since `Runnable` is a functional interface, a lambda expression (`() -> { ... }`) is the most modern and concise syntax for providing its implementation, avoiding the boilerplate of inner classes.

---
Excellent. Let's continue with the MCQ sections for the remaining topics, maintaining the same format and difficulty.

---

### **Topic 5: Code Organization & Memory Management (Sessions 11-12)**

1.  A method in a class is declared without any access modifier. Which statement is true?
    - [ ] It can be accessed by any class in the same project.
    - [x] It can be accessed by any class in the same package.
    - [ ] It can be accessed only by subclasses of its class, regardless of package.
    - [ ] It is implicitly `private`.

<br>

2.  What is the output of this code snippet, and why?
    ```java
    class Resource {
        Resource() { System.out.print("R"); }
        void cleanup() { System.out.print("C"); }
    }
    public class Test {
        public static void main(String[] args) {
            new Resource().cleanup();
            System.gc();
        }
    }
    ```
    - [ ] RC, and the `finalize()` method of `Resource` will be called.
    - [x] RC, but there's no guarantee the object will be garbage collected.
    - [ ] R, because `cleanup()` causes an error.
    - [ ] The code fails to compile.

<br>

3.  Class `A` is in `package com.p1`. Class `B` is in `package com.p2`. What is the minimum change required to allow a method in class `B` to access a `protected` method in class `A`?
    - [x] Class `B` must extend class `A`.
    - [ ] Class `A` must be imported into class `B`.
    - [ ] The method in class `B` must create an instance of `A`.
    - [ ] It is not possible.

<br>

4.  Consider the code `Object obj = new Object();`. When is the memory allocated for `obj` on the heap eligible for garbage collection?
    - [ ] As soon as `new Object()` is executed.
    - [x] When the reference `obj` goes out of scope.
    - [ ] Immediately after `System.gc()` is called.
    - [ ] Never, because it is an `Object`.

<br>

5.  What is true about constructor chaining using `this()`?
    - [ ] It can be placed anywhere inside a constructor.
    - [ ] It can be used to call a constructor of the superclass.
    - [x] It must be the very first statement in a constructor.
    - [ ] A constructor can make multiple `this()` calls to chain to several constructors.

<br>

**Answer Key (Topic 5):**
1.  **B**: No access modifier means "default" or "package-private" access. The member is accessible to any other class in the same package but not outside of it.
2.  **B**: The code will print "RC" because an object is created and its `cleanup` method is called. The `new Resource()` object becomes eligible for GC immediately after `cleanup()` returns, as there are no references to it. However, `System.gc()` is only a *suggestion* and does not guarantee that the GC will run or that the object will be collected before the program terminates.
3.  **A**: The `protected` modifier allows access within the same package OR to subclasses in different packages. Since `A` and `B` are in different packages, the only way for `B` to access `A`'s protected members is through inheritance.
4.  **B**: The object on the heap is "reachable" as long as there is an active reference to it (`obj`). When that reference variable goes out of scope (e.g., the method it was declared in finishes), the object becomes unreachable and thus eligible for garbage collection.
5.  **C**: A call to `this()` (or `super()`) must be the first statement in a constructor's body. This ensures that the object is properly initialized from a single, clear path.

---

### **Topic 6: Standard Library Essentials (`String`, `Wrapper`, `IO`) (Sessions 13-14 & 17)**

1.  What is the output of the following code?
    ```java
    String s1 = "abc";
    String s2 = "abc";
    String s3 = new String("abc");
    System.out.println((s1 == s2) + " " + (s1 == s3));
    ```
    - [ ] true true
    - [x] true false
    - [ ] false true
    - [ ] false false

<br>

2.  A class `Config` implements `Serializable` and has a field `private transient Connection dbConnection;`. What does this imply?
    - [ ] The `dbConnection` object will be serialized, but its data will be encrypted.
    - [ ] An attempt to serialize a `Config` object will fail if `dbConnection` is not null.
    - [x] The `dbConnection` field will be excluded from the serialization process.
    - [ ] The `transient` keyword forces the `dbConnection` to be closed before serialization.

<br>

3.  What is the result of this code?
    ```java
    StringBuilder sb = new StringBuilder("test");
    String s = "test";
    System.out.println(s.equals(sb));
    ```
    - [ ] true
    - [x] false
    - [ ] The code fails to compile.
    - [ ] A runtime exception is thrown.

<br>

4.  You need to read a binary file containing raw image data. Which class is the most fundamental and appropriate starting point for this task?
    - [ ] `FileReader`
    - [ ] `BufferedReader`
    - [ ] `ObjectInputStream`
    - [x] `FileInputStream`

<br>

5.  What is the value of `i` after this code executes?
    ```java
    Integer i = new Integer(10);
    Integer j = new Integer(10);
    if (i == j) {
        i++;
    } else {
        j++;
    }
    // What is the value of 'i' here?
    ```
    - [x] 10
    - [ ] 11
    - [ ] 12
    - [ ] The code is invalid.

<br>

**Answer Key (Topic 6):**
1.  **B**: `s1` and `s2` both refer to the same object from the String Constant Pool. `s3` is created with the `new` keyword, which explicitly creates a new object on the heap, bypassing the pool. Therefore, `s1 == s2` is true (same object), but `s1 == s3` is false (different objects).
2.  **C**: The `transient` keyword marks a field to be ignored by the serialization mechanism. This is commonly used for fields that are not serializable (like database connections) or for sensitive data that should not be persisted.
3.  **B**: The `equals()` method in the `String` class is implemented to check if the other object is also a `String` and has the same character sequence. Since `sb` is a `StringBuilder`, not a `String`, `s.equals(sb)` will return `false`.
4.  **D**: `FileInputStream` is a byte stream, which is the correct tool for reading raw binary data. `FileReader` and `BufferedReader` are character streams and would corrupt the image data. `ObjectInputStream` is for deserializing Java objects.
5.  **A**: The `if (i == j)` comparison checks for reference equality. Since `i` and `j` are two distinct objects created with `new`, the condition is false. The `else` block executes, incrementing `j` to 11. The value of `i` remains unchanged at 10.

---

### **Topic 7: Collections & Maps (Sessions 18-26)**

1.  You have a `List<Employee>`. To sort this list based on employee salary, what is the most flexible approach?
    - [ ] Ensure the `Employee` class implements `Comparable` and defines the salary comparison in its `compareTo` method.
    - [x] Create a separate class that implements `Comparator<Employee>` to compare salaries, and pass an instance of it to `Collections.sort()`.
    - [ ] Put the employees in a `TreeSet`.
    - [ ] Manually implement a bubble sort algorithm.

<br>

2.  You add an object `k` to a `HashSet`. You then modify the state of `k` in a way that changes its hash code. What is the likely result of calling `set.contains(k)`?
    - [ ] `true`, because the object is still in the set.
    - [x] `false`, because the set will look in the wrong "bucket" based on the new hash code.
    - [ ] A `ConcurrentModificationException` is thrown.
    - [ ] The behavior is undefined.

<br>

3.  Which collection guarantees that elements are processed in a strict FIFO (First-In, First-Out) order?
    - [ ] `Stack`
    - [ ] `ArrayList`
    - [x] `Queue`
    - [ ] `HashSet`

<br>

4.  What is the purpose of the `Map.entrySet()` method?
    - [ ] To get a `Set` of all keys in the map.
    - [ ] To get a `Collection` of all values in the map.
    - [x] To get a `Set` of key-value pairs (`Map.Entry` objects), which is the most efficient way to iterate over both keys and values.
    - [ ] To check if the map is empty.

<br>

5.  What is the output of the following stream pipeline?
    ```java
    long count = Stream.of("a", "b", "c")
                       .map(s -> s.toUpperCase())
                       .peek(System.out::print)
                       .count();
    ```
    - [x] ABC
    - [ ] abc
    - [ ] 3
    - [ ] ABC3

<br>

**Answer Key (Topic 7):**
1.  **B**: Using a `Comparator` is the most flexible approach because it decouples the sorting logic from the `Employee` class itself. This allows you to define many different ways to sort employees (by salary, by name, by ID, etc.) without modifying the `Employee` class.
2.  **B**: This is a critical rule: **never modify an object in a way that changes its hash code while it is stored in a hash-based collection (`HashSet`, `HashMap`).** The set uses the original hash code to determine the object's location. When you call `contains(k)`, it will calculate the *new* hash code and look in a different location, failing to find the object even though it is present.
3.  **C**: `Queue` is the interface specifically designed for FIFO processing. A `Stack` is LIFO (Last-In, First-Out).
4.  **C**: Iterating over the `entrySet` is more efficient than getting the `keySet` and then calling `get(key)` for each key, as the latter involves a second hash lookup for every element.
5.  **A**: The terminal operation is `count()`, which triggers the stream processing. The `peek()` intermediate operation is a debugging tool that performs an action on each element as it flows through the stream. It will print "A", "B", and "C". The `count()` method itself returns the count (`3`), but this value is not printed. So the only visible output is "ABC".

---

### **Topic 8: Concurrency & Advanced Topics (Sessions 27-30)**

1.  Thread A calls `object.wait()`. What must be true for this call to be legal?
    - [x] Thread A must hold the intrinsic lock for `object`.
    - [ ] The `object` must be an instance of the `Thread` class.
    - [ ] No other thread can be running in the system.
    - [ ] Thread A must have the highest priority.

<br>

2.  A developer uses the Reflection API to find and call a private method. Which of the following is a primary consequence of this action?
    - [ ] It improves performance by bypassing security checks.
    - [x] It breaks encapsulation, making the code brittle and harder to maintain.
    - [ ] It creates a new thread to execute the private method.
    - [ ] It is only possible if the class is not `final`.

<br>

3.  What is a key difference between `Thread.sleep()` and `object.wait()`?
    - [ ] `sleep()` releases the object's lock, while `wait()` does not.
    - [ ] `wait()` releases the object's lock, while `sleep()` does not.
    - [ ] `sleep()` is an instance method, while `wait()` is a static method.
    - [ ] `wait()` is deprecated, and `sleep()` should be used for all pauses.

<br>

4.  A method signature is `public <T extends Number & Runnable> void execute(T task)`. Which of the following object types can be legally passed to this method?
    - [ ] An object of a class `class MyTask implements Runnable {}`
    - [ ] An object of type `Integer`.
    - [x] An object of a class `class MyNumTask extends Number implements Runnable {}`
    - [ ] An object of a class `class MyTask extends Thread {}`

<br>

5.  What is the state of two threads, A and B, in a classic deadlock?
    - [ ] Both threads are in the `RUNNABLE` state, competing for the CPU.
    - [ ] Both threads are in the `TERMINATED` state.
    - [x] Both threads are in the `BLOCKED` or `WAITING` state, each waiting for a lock held by the other.
    - [ ] Thread A is `BLOCKED`, and Thread B is `WAITING`.

<br>

**Answer Key (Topic 8):**
1.  **A**: A thread must own the monitor (the lock) of an object before it can call `wait()`, `notify()`, or `notifyAll()` on it. This is why these methods must be called from within a `synchronized` block or method.
2.  **B**: Reflection is a powerful tool for frameworks but a dangerous one for application code. By bypassing the `private` access modifier, you are making your code dependent on the internal implementation details of another class, which can change without notice, causing your code to break.
3.  **B**: This is a critical distinction. `Thread.sleep()` pauses the thread but keeps all of its held locks. `object.wait()` is designed for inter-thread coordination and *releases the lock* on `object` so another thread can acquire it to change the condition and call `notify()`.
4.  **C**: This is a complex generic declaration. The type `T` must be a subclass of `Number` AND implement the `Runnable` interface. `Integer` (B) does not implement `Runnable`. `MyTask` (A) does not extend `Number`. `MyTask` (D) does not extend `Number` (it extends `Thread`). Only (C) satisfies both bounds.
5.  **C**: This is the definition of deadlock. The threads are not runnable because they cannot proceed. They are waiting for a condition (the release of a lock) that can never be met because the thread that can meet the condition is itself waiting.

---
