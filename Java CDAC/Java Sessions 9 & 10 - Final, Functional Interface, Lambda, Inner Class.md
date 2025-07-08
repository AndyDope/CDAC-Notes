### **Sessions 9 & 10: Final, Functional Interface, Lambda, Inner Class**

Welcome. In this lesson, we explore a diverse set of powerful Java features. We'll start with the `final` keyword, which lets us create constants and prevent changes to classes and methods. Then, we will jump into modern Java features introduced in Java 8: **functional interfaces** and **lambda expressions**, which have revolutionized the way we handle small, single-function tasks. Finally, we'll look at the different types of **inner classes**, which allow you to logically group classes that are only used in one place.

---

#### **1. The `final` Keyword**

The `final` keyword is a modifier that can be applied to variables, methods, and classes. It means "this cannot be changed."

*   **`final` variable:** A constant. Its value cannot be modified after it has been assigned. A `static final` variable is a true, class-level constant (e.g., `public static final double PI = 3.14;`).
    ```java
    final int MAX_ATTEMPTS = 3;
    // MAX_ATTEMPTS = 4; // Compilation Error!
    ```

*   **`final` method:** A method that cannot be **overridden** by a subclass. This is used to guarantee that the behavior of a method will remain the same in all subclasses.
    ```java
    class Parent {
        public final void display() {
            System.out.println("This is a final method.");
        }
    }
    class Child extends Parent {
        // @Override
        // public void display() { ... } // Compilation Error! Cannot override a final method.
    }
    ```

*   **`final` class:** A class that cannot be **extended** (inherited from). This is used for security and to ensure the immutability of a class. The `String` class, for example, is `final`.
    ```java
    final class SecureData { ... }
    // class HackedData extends SecureData { ... } // Compilation Error! Cannot extend a final class.
    ```

> **Quick Question:** Why is the `String` class in Java declared as `final`?
> **Answer:** Primarily for security and reliability. Since strings are used everywhere (filenames, network connections, security credentials), making the `String` class final prevents malicious subclasses from altering its behavior and ensures that strings are immutable, which makes them predictable and thread-safe.

---

#### **2. Functional Interface**

This is a key concept for understanding lambdas.
A **functional interface** is an [[Java Session 8 - Upcasting, Downcasting, Abstract class, Interface#**3. Interface**|interface]] that contains **exactly one abstract method**.

*   It can have any number of `default` or `static` methods, but only one abstract method.
*   The `@FunctionalInterface` annotation is optional but recommended. It tells the compiler to verify that the interface meets the criteria, preventing accidental changes.

**Example:** The `Runnable` interface is a classic functional interface.
```java
@FunctionalInterface
interface Runnable {
    void run(); // The single abstract method
}

@FunctionalInterface
interface Calculator {
    int operate(int a, int b);
}
```

---

#### **3. Lambda Expression (Java 8+)**

A **lambda expression** is a short block of code that takes in parameters and returns a value. It's essentially an anonymous (unnamed) method. Lambdas are used to provide an "on-the-fly" implementation for a functional interface.

**Syntax:** `(parameter_list) -> { method_body }`

*   The `->` operator separates the parameters from the body.
*   If the body is a single expression, you can omit the curly braces `{}` and the `return` keyword.
*   If there is one parameter, you can omit the parentheses `()`.

**How it works:** A lambda expression provides the implementation for the single abstract method of a functional interface.

**Example: Using the `Calculator` interface**
```java
public class LambdaDemo {
    public static void main(String[] args) {
        // Using a lambda expression to provide an implementation for Calculator's 'operate' method
        Calculator addition = (a, b) -> a + b; // Concise syntax for a single expression
        Calculator subtraction = (a, b) -> { return a - b; }; // Full syntax

        int sum = addition.operate(10, 5);       // sum is 15
        int difference = subtraction.operate(10, 5); // difference is 5

        System.out.println("Sum: " + sum);
        System.out.println("Difference: " + difference);
    }
}
```
Lambda expressions dramatically reduce boilerplate code compared to creating anonymous inner classes (which we'll see next).

> **Quick Question:** What is the primary requirement for an interface to be used with a lambda expression?
> **Answer:** It must be a functional interface (have exactly one abstract method).

---

#### **4. Inner Classes**

An inner class is a class defined within another class. They are used to logically group classes that are only used in one place, which increases encapsulation.

##### **a) Member Inner Class (Regular)**
A non-static class defined at the same level as instance variables. It can access all members (including private) of the outer class.
```java
class Outer {
    private int outerVar = 10;
    class Inner {
        void display() { System.out.println("Value of outerVar: " + outerVar); }
    }
}
// To instantiate: Outer outerObj = new Outer(); Outer.Inner innerObj = outerObj.new Inner();
```

##### **b) Static Nested Class**
A `static` class defined within another class. It can only access `static` members of the outer class. It behaves more like a regular top-level class that happens to be namespaced inside another.
```java
class Outer {
    static int staticVar = 20;
    static class Nested {
        void display() { System.out.println("Value of staticVar: " + staticVar); }
    }
}
// To instantiate: Outer.Nested nestedObj = new Outer.Nested();
```

##### **c) Method-Local Inner Class**
A class defined inside a method. It is only visible within that method.
```java
class Outer {
    void myMethod() {
        class MethodLocalInner {
            void display() { System.out.println("Inside method-local inner class."); }
        }
        MethodLocalInner mli = new MethodLocalInner();
        mli.display();
    }
}
```

##### **d) Anonymous Inner Class**
An inner class without a name. It is both declared and instantiated in a single expression. It was the primary way to handle single-use implementations before lambdas.
**Use case:** Creating a one-time-use object of an interface or abstract class.

**Example: Before Lambdas**
```java
// Using an anonymous inner class to implement Runnable
Runnable r = new Runnable() {
    @Override
    public void run() {
        System.out.println("Thread running (anonymous inner class).");
    }
};
new Thread(r).start();
```
**Example: With Lambdas (more concise)**
```java
// Using a lambda expression
Runnable r2 = () -> System.out.println("Thread running (lambda).");
new Thread(r2).start();
```

---

#### **5. `Enum`**
An `enum` is a special data type that enables a variable to be a set of predefined constants. The variable must be equal to one of the values that have been predefined for it.
```java
enum Level {
    LOW,
    MEDIUM,
    HIGH
}

public class EnumDemo {
    public static void main(String[] args) {
        Level myLevel = Level.MEDIUM;
        System.out.println(myLevel); // Output: MEDIUM
    }
}
```
Enums are type-safe and more powerful than using `static final int` constants.

---

### **Topic Summary & Revision**

*   **`final`:** Makes a variable a constant, a method non-overridable, or a class non-extendable.
*   **Functional Interface:** An interface with exactly one abstract method (e.g., `Runnable`).
*   **Lambda Expression:** A concise, anonymous function used to implement a functional interface. Syntax: `(params) -> { body }`.
*   **Inner Classes:** Classes defined within other classes for better encapsulation.
    *   **Member Inner:** Needs an outer object instance.
    *   **Static Nested:** Does not need an outer object instance.
    *   **Anonymous Inner:** A one-time-use, unnamed class, now often replaced by lambdas.
*   **`Enum`:** A type-safe way to define a group of named constants.

---

### **MCQs for Exam Preparation (Tricky)**

1.  **Which of the following is NOT a valid use of the `final` keyword in Java?**
    (A) `public final class MyClass { ... }`
    (B) `public final void myMethod() { ... }`
    (C) `public void myMethod(final int x) { ... }`
    (D) `public final abstract class MyAbstractClass { ... }`
    **Answer:** ||(D) A class cannot be both 'final' and 'abstract'. 'final' means the class cannot be extended, while 'abstract' means the class must be extended to be useful. The two concepts are mutually exclusive.||
<br>

2.  **Given the interface `interface Greeter { String greet(String name); }`, which of the following is a valid lambda expression assignment?**
    (A) `Greeter g = () -> "Hello";`
    (B) `Greeter g = name -> "Hello, " + name;`
    (C) `Greeter g = (String name, int age) -> "Hello, " + name;`
    (D) `Greeter g = (name) => "Hello, " + name;`
    **Answer:** ||(B) This lambda matches the single abstract method's signature: it takes one parameter ('name') and returns a 'String'. (A) is wrong because it takes no parameters. (C) is wrong because it has the wrong number/type of parameters. (D) is wrong because Java uses the '->' operator, not '=>'.||
<br>

3.  **To instantiate a non-static member inner class `Inner` of a class `Outer`, what is the correct syntax?**
    (A) `Outer.Inner obj = new Outer.Inner();`
    (B) `Outer obj = new Outer.Inner();`
    (C) `Outer outer = new Outer(); Outer.Inner inner = outer.new Inner();`
    (D) `Inner obj = new Inner();`
    **Answer:** ||(C) A non-static member inner class is tied to an instance of the outer class. You must first have an object of the outer class to create an object of the inner class. The syntax 'outer.new Inner()' is unique to this situation. (A) is the syntax for a static nested class.||
<br>

4.  **Before Java 8, which type of inner class was most commonly used to provide a short, one-off implementation of an event listener interface?**
    (A) Static nested class
    (B) Method-local inner class
    (C) Member inner class
    (D) Anonymous inner class
    **Answer:** ||(D) Anonymous inner classes were the standard way to handle simple interface implementations, like 'Runnable' or event listeners in Swing/Android, before lambdas provided a much more concise alternative.||
<br>

5.  **A method is declared as `public void processData(final List<String> data)`. What does this mean for the `data` parameter inside the method?**
    (A) The list itself cannot be modified (e.g., no `data.add()` or `data.remove()`).
    (B) The reference `data` cannot be reassigned to point to a different list object.
    (C) Both the reference cannot be changed, and the list cannot be modified.
    (D) The `final` keyword has no effect on reference type parameters.
    **Answer:** ||(B) When 'final' is applied to a reference variable (including parameters), it means the reference itself is a constant. You cannot do 'data = new ArrayList<>();'. However, you are still free to call methods on the object the reference points to, so 'data.add("new item")' is perfectly legal.||

---

### **Bonus Tips**

*   **Viva/Interview Tip:** The lambda expression is a gateway to the **Stream API**, one of the most powerful features in modern Java. Being able to explain that lambdas provide behavior to methods like `filter`, `map`, and `forEach` in the Stream API shows you are up-to-date with modern Java practices.
*   **Exam Tip:** The question about a `final` reference parameter (MCQ #5) is a very common and tricky one. Remember: `final` on a reference protects the **reference**, not the **object**.
*   **Modern Java:** While you should know what an anonymous inner class is, you should almost always **prefer a lambda expression** if the situation allows (i.e., you are implementing a functional interface). It is cleaner, shorter, and expresses the intent more clearly.

**🔗Links:** [[Java Session 11 - Access Modifiers, Packages, Imports]]