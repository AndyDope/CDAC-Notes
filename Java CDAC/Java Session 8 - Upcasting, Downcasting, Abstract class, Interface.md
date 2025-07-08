### **Session 8: Upcasting, Downcasting, Abstract class, Interface**

Welcome to Session 8. We've established that [[Java Session 7 - Inheritance, Association, Aggregation and Composition#**1. Inheritance "is-a" Relationship**|inheritance]] creates an "is-a" relationship, which enables [[Java Session 4 - Object Oriented Programming Concepts#d) Polymorphism|polymorphism]]. Today, we'll explore how to work with objects through their parent-class references using **upcasting** and **downcasting**. Then, we will unlock the full power of abstraction by learning about **abstract classes** and **interfaces**, which allow us to define contracts for what a class *must* do, without specifying *how* it must do it.

---

#### **1. Upcasting and Downcasting a Reference Variable**

These concepts are central to using polymorphism effectively.

##### **a) Upcasting**
*   **Definition:** Casting a reference from a subclass type to a superclass type.
*   **Safety:** It is always safe and happens **implicitly**. You don't need to write an explicit cast.
*   **Usefulness:** It allows you to write generic code. You can have an array of `Vehicle` references that can hold `Car`, `Truck`, and `Bicycle` objects.

```java
class Animal {
    public void makeSound() { System.out.println("Generic animal sound"); }
}
class Dog extends Animal {
    @Override
    public void makeSound() { System.out.println("Woof"); }
    public void fetch() { System.out.println("Fetching ball"); }
}

// Upcasting Example
Dog myDog = new Dog();
Animal myAnimal = myDog; // Implicit upcast: a Dog 'is-an' Animal

// Runtime polymorphism in action!
// The JVM knows the *actual object* is a Dog, so it calls the Dog's method.
myAnimal.makeSound(); // Output: Woof

// However, you cannot call methods specific to the subclass using the superclass reference.
// myAnimal.fetch(); // Compilation Error! The Animal class doesn't have a fetch() method.
```

##### **b) Downcasting**
*   **Definition:** Casting a reference from a superclass type back down to a subclass type.
*   **Safety:** It is **unsafe** and can fail at runtime if the object is not actually an instance of the target subclass. It must be done **explicitly**.
*   **Usefulness:** It allows you to access the specific methods of the subclass after you've determined the object's true type.

To safely downcast, you should first check the object's type using the `instanceof` operator.

```java
// Continuing from the previous example, myAnimal holds a Dog object.

if (myAnimal instanceof Dog) {
    // It's safe to downcast now.
    Dog d = (Dog) myAnimal; // Explicit downcast

    // Now we can call Dog-specific methods.
    d.fetch(); // Output: Fetching ball
}
```
Attempting to downcast an object to a type it is not will result in a `ClassCastException`.

> **Quick Question:** Why is upcasting always safe, while downcasting is potentially unsafe?
> **Answer:** Upcasting is safe because a subclass object always "is-a" superclass object and has all its methods. Downcasting is unsafe because a superclass reference might be pointing to a different subclass (or just the superclass itself), which doesn't have the specific methods of the target subclass.

---

#### **2. Abstract Class and Abstract Methods**

An **abstract class** is a class that cannot be instantiated. It is designed to be a blueprint for other classes to extend. It can have a mix of regular methods with implementations and **abstract methods**.

An **abstract method** is a method that is declared without an implementation (it has no body, just a signature followed by a semicolon).
*   **Keywords:** `abstract`
*   **Rule:** If a class has one or more abstract methods, the class itself **must** be declared `abstract`.
*   **Contract:** Any non-abstract subclass that extends an abstract class **must** provide an implementation (override) for all of its inherited abstract methods.

**When to use it:** Use an abstract class when you want to provide some common, implemented functionality for a group of related classes, but also force those subclasses to provide their own unique implementation for certain other methods.

**Example:**
```java
// Abstract blueprint for any shape
abstract class Shape {
    int x, y;

    // A regular, implemented method
    void moveTo(int newX, int newY) {
        this.x = newX;
        this.y = newY;
        System.out.println("Moved to " + x + ", " + y);
    }

    // An abstract method - a contract for all subclasses
    // Every shape must know how to draw itself, but we don't know how here.
    abstract void draw();
}

class Circle extends Shape {
    // Circle MUST implement the draw() method
    @Override
    void draw() {
        System.out.println("Drawing a circle at " + x + ", " + y);
    }
}

class Rectangle extends Shape {
    // Rectangle MUST also implement the draw() method
    @Override
    void draw() {
        System.out.println("Drawing a rectangle at " + x + ", " + y);
    }
}
```

> **Quick Question:** Can you create an object of an abstract class, like `new Shape()`?
> **Answer:** No. An abstract class cannot be instantiated directly.

---

#### **3. Interface**

An **interface** is a purely abstract template. It can only contain `public abstract` methods (before Java 8) and `public static final` constants. Think of it as a 100% abstract class.

*   **Keyword:** `interface`
*   **Contract:** An interface defines a contract of behaviors. Any class that **implements** an interface must provide an implementation for all of its methods.
*   **Multiple Inheritance:** A class can `implement` multiple interfaces. This is how Java solves the multiple inheritance problem.

**When to use it:** Use an interface when you want to define a role or a capability that different, unrelated classes can share. For example, many different objects can be "flyable" (`Bird`, `Airplane`, `Kite`).

**Example:**
```java
interface Flyable {
    // All variables in an interface are public static final by default
    int MAX_ALTITUDE = 40000;

    // All methods are public abstract by default
    void fly();
    void land();
}

class Bird implements Flyable {
    @Override
    public void fly() { System.out.println("Bird is flapping its wings to fly."); }
    @Override
    public void land() { System.out.println("Bird is landing on a branch."); }
}

class Airplane implements Flyable {
    @Override
    public void fly() { System.out.println("Airplane is using its engines to fly."); }
    @Override
    public void land() { System.out.println("Airplane is landing on a runway."); }
}
```
A class can both extend another class and implement interfaces: `class Seaplane extends Airplane implements Swimmable { ... }`

---

### **Topic Summary & Revision**

| Feature | Abstract Class | Interface |
| :--- | :--- | :--- |
| **Keyword** | `abstract class` | `interface` |
| **Inheritance** | A class `extends` one abstract class. | A class `implements` many interfaces. |
| **Methods** | Can have both abstract and non-abstract (implemented) methods. | All methods are implicitly `public abstract` (before Java 8). |
| **Fields** | Can have any type of field (static, final, non-final, etc.). | Fields are implicitly `public static final` (constants). |
| **Constructors** | Has constructors (called by subclass constructors). | Does not have constructors. |
| **Purpose** | To provide a common base for a group of closely related objects ("is-a"). | To define a role or capability that can be shared by unrelated classes. |

*   **Upcasting:** Implicitly casting a subclass reference to a superclass reference.
*   **Downcasting:** Explicitly casting a superclass reference to a subclass reference, checked with `instanceof`.

---

### **MCQs for Exam Preparation (Tricky)**

1.  **Given `class B extends A {}` and `class C extends A {}`, what is the result of this code?**
```java
A a = new B();
C c = (C) a;
```
(A) The code compiles and runs successfully.
(B) The code fails to compile.
(C) The code compiles but throws a `ClassCastException` at runtime.
(D) The code compiles but throws a `NullPointerException` at runtime.
**Answer:** ||(C) The code compiles because, syntactically, an object of type 'A' 'could' be a 'C'. However, at runtime, the JVM knows the actual object stored in 'a' is a 'B'. Since a 'B' is not a 'C', the downcast is invalid and a 'ClassCastException' is thrown.||
<br>

2.  **Which statement about abstract classes and interfaces in Java is TRUE?**
    (A) An abstract class can be instantiated if it has no abstract methods.
    (B) An interface can contain a method with a full implementation (a method body).
    (C) A class can extend multiple abstract classes.
    (D) An abstract class can have a constructor, but an interface cannot.
    **Answer:** ||(D) An abstract class needs a constructor to initialize its fields and to be called by subclass constructors via 'super()'. An interface cannot be instantiated and has no fields to initialize, so it cannot have a constructor. Note: Since Java 8, interfaces 'can' have implemented methods ('default' and 'static' methods), making (B) a trickier statement, but in the classic sense, (D) is the most fundamentally correct distinction.||
<br>

3.  **A programmer wants to define a common capability, like `Serializable`, that can be applied to many unrelated classes (e.g., `Employee`, `CarData`, `GameScore`). Which is the most appropriate tool for this?**
    (A) An abstract class `Serializable` that all other classes extend.
    (B) An interface `Serializable` that all other classes implement.
    (C) A static utility class with serialization methods.
    (D) A final class `Serializable`.
    **Answer:** ||(B) An interface is perfect for defining a role or capability ('can be serialized') that is not tied to a specific class hierarchy. Since a class can implement multiple interfaces, this allows for maximum flexibility. Using an abstract class (A) would be too restrictive as a class can only extend one parent.||
<br>

4.  **A class `MyClass` is declared as `public abstract class MyClass { ... }`. Which of the following is guaranteed to be true?**
    (A) `MyClass` must contain at least one `abstract` method.
    (B) You cannot declare a reference variable of type `MyClass`, e.g., `MyClass obj;`.
    (C) Any non-abstract subclass of `MyClass` must implement all abstract methods inherited from `MyClass`.
    (D) `MyClass` cannot have any static methods.
    **Answer:** ||(C) This is the core contract of an abstract class. A concrete (non-abstract) subclass is not allowed to be incomplete; it must provide implementations for all abstract methods it inherits. A class can be 'abstract' even with no abstract methods (A is false). You can declare a reference variable (B is false). Abstract classes can have static methods (D is false).||
<br>

5.  **What is the primary purpose of the `instanceof` operator?**
    (A) To check if an object's class is an instance of the `Object` class.
    (B) To create a new instance of a class.
    (C) To safely determine an object's type before attempting a potentially unsafe downcast.
    (D) To compare if two reference variables point to the same instance.
    **Answer:** ||(C) The 'instanceof' operator is a runtime type-checking mechanism. Its main use case is to prevent 'ClassCastException' by verifying that an object "is-a" member of a certain class hierarchy before you try to cast it.||

---

### **Bonus Tips**

*   **Viva/Interview Tip:** The "When to use an abstract class vs. an interface?" question is a classic. A great answer is: **"Use an abstract class for an 'is-a' relationship when you want to share common code or fields. Use an interface to define a 'can-do' capability or a role that can be shared by unrelated classes."**
*   **Exam Tip:** Be very careful with casting questions. Always trace what the *actual* object type is. The compiler only checks for syntactic possibility, but the JVM checks for runtime reality.
*   **Design Tip:** "Program to an interface, not an implementation." This is a famous design principle. It means your code should depend on interfaces or abstract classes (like `List` or `Shape`) rather than concrete classes (like `ArrayList` or `Circle`). This makes your code more flexible and easier to change later. For example: `List<String> names = new ArrayList<>();` is better than `ArrayList<String> names = new ArrayList<>();`.

**🔗Links:** [[Java Sessions 9 & 10 - Final, Functional Interface, Lambda, Inner Class]]