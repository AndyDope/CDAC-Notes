### **Session 4: Object Oriented Programming Concepts**

Welcome to Session 4. We've laid the groundwork, and now we arrive at the central theme of this course. While you've encountered these concepts in C++, we will now see how Java implements them. Java was designed from the ground up as an Object-Oriented language, making its approach clean and consistent.

---

#### **1. Introduction to OOP**

Object-Oriented Programming (OOP) is a programming paradigm based on the concept of "objects". Instead of structuring a program as a set of functions, OOP structures it as a collection of interacting objects. This model helps in managing complexity, improving reusability, and creating more maintainable code.

**Analogy: Building a Car**
*   **Procedural Approach (like C):** You would write a series of functions: `assembleEngine()`, `attachWheels()`, `installSeats()`. The data (screws, metal sheets) and the functions are separate.
*   **OOP Approach (like Java):** You first design blueprints (Classes) for each component: an `Engine` class, a `Wheel` class, a `Seat` class. Each blueprint defines what a component *is* (its data, like horsepower or tire pressure) and what it *does* (its methods, like `start()` or `rotate()`). Then you create actual objects from these blueprints and assemble them.

---

#### **2. Classes and Objects**

This is the fundamental pair in OOP.

*   **Class:** A blueprint or template for creating objects. It defines a set of properties (called **fields** or **instance variables**) and behaviors (called **methods**). A class does not occupy any memory itself.
*   **Object:** An instance of a class. It is a concrete entity created from the class blueprint and resides in memory. Each object has its own state (the values of its fields).

**Example:**
```java
// Blueprint for a Dog (The Class)
class Dog {
    // Fields (state)
    String breed;
    int age;
    String color;

    // Methods (behavior)
    void bark() {
        System.out.println("Woof! Woof!");
    }

    void sleep() {
        System.out.println("Zzz...");
    }
}
```

To use this blueprint, we must create objects. The `new` keyword is used to instantiate a class.

```java
public class DogPark {
    public static void main(String[] args) {
        // Create an object (instance) of the Dog class
        Dog myDog = new Dog();

        // Set the state of this specific object
        myDog.breed = "Golden Retriever";
        myDog.age = 3;
        myDog.color = "Golden";

        // Call its methods
        System.out.println("My dog is a " + myDog.age + " year old " + myDog.breed);
        myDog.bark(); // Output: Woof! Woof!

        // Create another, completely separate object
        Dog neighborDog = new Dog();
        neighborDog.breed = "German Shepherd";
        neighborDog.age = 5;

        System.out.println("Neighbor's dog is a " + neighborDog.age + " year old " + neighborDog.breed);
        neighborDog.sleep(); // Output: Zzz...
    }
}
```

> **Quick Question:** If `Dog` is the class, what is `myDog`?
> **Answer:** `myDog` is an object, or an instance, of the `Dog` class.

---

#### **3. OOP Principles**

These are the four pillars that define an Object-Oriented language.

##### **a) Encapsulation**
*   **Definition:** The bundling of data (fields) and the methods that operate on that data into a single unit (the class). It also involves restricting direct access to an object's data, which is known as **data hiding**.
*   **Implementation:** Achieved by making the class fields `private` and providing `public` methods (getters and setters) to access and modify them.
*   **Benefit:** Protects the integrity of an object's data. The class maintains full control over its state.

```java
public class Employee {
    private double salary; // Data is hidden

    // Public getter to access the data
    public double getSalary() {
        return salary;
    }

    // Public setter to modify the data with validation
    public void setSalary(double newSalary) {
        if (newSalary > 0) {
            this.salary = newSalary;
        }
    }
}
```
Here, you cannot set a negative salary because the `setSalary` method protects the `salary` field.

##### **b) Abstraction**
*   **Definition:** Hiding the complex implementation details and showing only the essential features of the object. It focuses on the "what" an object does, not "how" it does it.
*   **Implementation:** Achieved using **abstract classes** and **interfaces** (which we will cover in [[Java Session 8 - Upcasting, Downcasting, Abstract class, Interface|a later session]]).
*   **Benefit:** Simplifies complex systems. You don't need to know how a car's engine works to drive it; you just need to know how to use the steering wheel and pedals (the interface).

##### **c) Inheritance**
*   **Definition:** The mechanism by which one class (the **subclass** or **child class**) acquires the properties and behaviors of another class (the **superclass** or **parent class**). It establishes an "is-a" relationship.
*   **Implementation:** Using the `extends` keyword.
*   **Benefit:** Promotes code reuse and establishes a natural hierarchy between classes.

```java
// Superclass
class Vehicle {
    void drive() {
        System.out.println("Driving a vehicle.");
    }
}

// Subclass
// A Car 'is-a' Vehicle
class Car extends Vehicle {
    // Car inherits the drive() method
}
```

##### **d) Polymorphism**
*   **Definition:** The ability of an object to take on many forms. In practice, it means a single interface (like a method name) can represent different underlying actions.
*   **Types in Java:**
    1.  **Compile-time Polymorphism (Method Overloading):** Having multiple methods with the same name but different parameters in the same class. The compiler decides which one to call based on the arguments.
    2.  **Runtime Polymorphism (Method Overriding):** A subclass provides a specific implementation for a method that is already defined in its superclass. The decision on which method to run is made at runtime.

**Example of Overriding:**
```java
class Animal {
    public void makeSound() {
        System.out.println("Animal makes a sound");
    }
}

class Cat extends Animal {
    @Override // Annotation to indicate overriding
    public void makeSound() {
        System.out.println("Meow");
    }
}
```

---

### **Topic Summary & Revision**

*   **Class:** A blueprint. Defines fields (data) and methods (behavior).
*   **Object:** An instance of a class, created with the `new` keyword.
*   **Encapsulation:** Bundling data and methods. Use `private` fields and `public` getters/setters for data hiding.
*   **Abstraction:** Hiding implementation complexity. Focus on the "what," not the "how."
*   **Inheritance:** An "is-a" relationship using the `extends` keyword for code reuse.
*   **Polymorphism:** "Many forms." Achieved through method **overloading** (compile-time) and method **overriding** (runtime).

---

### **MCQs for Exam Preparation (Tricky)**

1.  **A class `SecureData` has a private field `private String data;`. A developer wants to allow other classes to read this data but *not* modify it. How should this be implemented according to proper encapsulation principles?**
    (A) Make the `data` field public.
    (B) Provide a public `getData()` method and a private `setData()` method.
    (C) Provide a public `getData()` method and no `setData()` method.
    (D) Provide both a public `getData()` and a public `setData()` method.
    **Answer:** ||(C) This pattern is known as creating a 'read-only' property. The public getter allows access, while the absence of a public setter prevents modification from outside the class, thus enforcing the requirement.||
<br>

2.  **Which OOP principle is best illustrated by the ability to use a single reference variable of type `Vehicle` to refer to objects of type `Car`, `Truck`, or `Motorcycle`?**
    (A) Encapsulation
    (B) Inheritance
    (C) Polymorphism
    (D) Abstraction
    **Answer:** ||(C) Polymorphism. This is a classic example of runtime polymorphism, where a single type ('Vehicle') can represent objects of different subclasses. While inheritance (B) is required for this to work, the principle being demonstrated is polymorphism itself.||
<br>

3.  **Consider the relationship between a `Car` and its `Engine`. Which OOP concept best models this "has-a" relationship?**
    (A) Inheritance (`Car extends Engine`)
    (B) Association/Composition (a `Car` class has a field of type `Engine`)
    (C) Abstraction
    (D) Polymorphism
    **Answer:** ||(B) A Car 'has-an' Engine, it is not a type of Engine. This is a 'has-a' relationship, which is modeled by having an instance of one class as a field in another (Composition/Aggregation). Inheritance ('is-a') would be incorrect. This is a crucial distinction.||
<br>

4.  **What is the primary goal of Abstraction in OOP?**
    (A) To reuse code from existing classes.
    (B) To bundle data and methods together.
    (C) To hide internal complexity from the user and expose only necessary functionality.
    (D) To allow a method to behave differently based on the object that calls it.
    **Answer:** ||(C) Abstraction is all about managing complexity by hiding unnecessary details. Code reuse is the goal of Inheritance (A), bundling is Encapsulation (B), and different behavior is Polymorphism (D).||
<br>

5.  **Which statement is true about a Class in Java?**
    (A) A class is a tangible entity that occupies memory on the heap.
    (B) A class can have multiple objects, and each object shares the same instance variables.
    (C) A class is a logical template from which objects with their own state and behavior are created.
    (D) A class must have at least one private field to be considered properly designed.
    **Answer:** ||(C) A class is a logical blueprint; it does not occupy memory itself (A is wrong). Objects are created from it, and each object gets its own copy of instance variables (B is wrong). While encapsulation is good practice, a class is not required to have private fields (D is wrong).||

---

### **Bonus Tips**

*   **Viva/Interview Tip:** The **"is-a" vs. "has-a"** relationship (MCQ #3) is a cornerstone of OOP design interviews. "is-a" implies **Inheritance** (`Car` is-a `Vehicle`). "has-a" implies **Composition/Association** (`Car` has-a `Engine`). Getting this wrong is a major red flag.
*   **Exam Tip:** Be able to clearly distinguish between the four main principles. Questions will often describe a scenario and ask you which principle it demonstrates. Use keyword associations: Encapsulation -> `private`/getters/setters; Inheritance -> `extends`/"is-a"; Polymorphism -> overloading/overriding; Abstraction -> hiding complexity/"interface."
*   **Lab Tip:** Start practicing encapsulation immediately. Make all your class fields `private` by default. Only make them non-private if you have a very specific and justifiable reason. Then, add public getters and setters as needed. This is a critical habit for writing robust code.

**🔗Links:** [[Java Session 5 - Static, Reference variables and methods]]