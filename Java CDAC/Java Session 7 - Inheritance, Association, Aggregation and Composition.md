### **Session 7: Inheritance, Association, Aggregation and Composition**

Welcome to Session 7. We have already introduced [[Java Session 4 - Object Oriented Programming Concepts#c) Inheritance|Inheritance]] as the "is-a" relationship. Today, we will explore its different forms and contrast it with another fundamental type of relationship: the "has-a" relationship, which is crucial for building complex objects from simpler ones. Understanding the difference between "is-a" and "has-a" is vital for designing robust and logical software.

---

#### **1. Inheritance: "is-a" Relationship**

Inheritance is a mechanism for creating a new class (subclass) based on an existing class (superclass). The subclass inherits the public and protected fields and methods of the superclass, promoting code reuse.

**Keyword:** `extends`

##### **a) Single Inheritance**
A class inherits from only one other class. Java supports single inheritance for classes.
```java
class Animal { ... }
class Dog extends Animal { ... } // Dog is-an Animal
```

##### **b) Multilevel Inheritance**
A class inherits from a subclass, forming a chain of inheritance.
```java
class Animal { ... }
class Dog extends Animal { ... }       // Dog is-an Animal
class Puppy extends Dog { ... }      // Puppy is-a Dog
```
Here, `Puppy` inherits from both `Dog` and `Animal`.

##### **c) Hierarchical Inheritance**
Multiple subclasses inherit from a single superclass.
```java
class Vehicle { ... }
class Car extends Vehicle { ... }      // Car is-a Vehicle
class Bicycle extends Vehicle { ... }  // Bicycle is-a Vehicle
```
**Important Note:** Java **does not support multiple inheritance** for classes (a class cannot `extend` more than one other class). This is to avoid the "Diamond Problem," where ambiguity arises if two parent classes have a method with the same name. This problem is solved in Java using interfaces, which we will see later.

> **Quick Question:** Why would `class Child extends Parent1, Parent2` be invalid in Java?
> **Answer:** Because Java does not support multiple inheritance for classes to prevent the complexity and ambiguity of the Diamond Problem.

---

#### **2. Association: The "has-a" Relationship**

While inheritance models an "is-a" relationship, **association** models a relationship where one object uses or has a relationship with another object. It's the "has-a" relationship. It is implemented by having an instance of one class as a field in another class.

**Analogy:**
*   **Inheritance (is-a):** A `Car` **is a** `Vehicle`.
*   **Association (has-a):** A `Car` **has an** `Engine`.

Association is a broad category that is further refined into two more specific types: Aggregation and Composition.

---

#### **3. Aggregation**

Aggregation is a specialized form of Association that represents a **"whole-part"** relationship where the "part" can exist independently of the "whole".

*   It is a **weak** "has-a" relationship.
*   The lifecycle of the part is not tied to the lifecycle of the whole. If the whole is destroyed, the part can still exist.

**Example:** A `Department` has `Professor`s.
A department is composed of professors. However, if the department is shut down, the professors don't cease to exist; they can join another department or university.

```java
class Professor {
    String name;
    Professor(String name) { this.name = name; }
}

class Department {
    String name;
    private List<Professor> professors; // Department has-a list of Professors

    Department(String name, List<Professor> professors) {
        this.name = name;
        this.professors = professors;
    }
}

// In main method:
Professor p1 = new Professor("Dr. Smith");
Professor p2 = new Professor("Dr. Jones");
List<Professor> profList = new ArrayList<>();
profList.add(p1);
profList.add(p2);

Department cse = new Department("CSE", profList);

// Now, if 'cse' department is dissolved (cse = null), the objects 'p1' and 'p2' still exist.
```

> **Quick Question:** What is the key characteristic of an aggregation relationship regarding the lifecycle of its parts?
> **Answer:** The part can exist independently of the whole.

---

#### **4. Composition**

Composition is a stricter form of Aggregation. It also represents a "whole-part" relationship, but here, the "part" **cannot exist without the "whole"**.

*   It is a **strong** "has-a" relationship.
*   The lifecycle of the part is managed by the whole. If the whole is destroyed, the part is also destroyed.
*   The "part" object is typically created inside the "whole" object.

**Example:** A `House` has `Room`s.
A house is composed of rooms. If you demolish the house, the rooms within it cease to exist. You cannot have a living room without a house.

```java
class Room {
    int area;
    Room(int area) { this.area = area; }
}

class House {
    // The House creates and owns its Rooms.
    private Room livingRoom;
    private Room kitchen;

    public House() {
        // The parts (Rooms) are created inside the whole (House).
        this.livingRoom = new Room(250);
        this.kitchen = new Room(150);
    }
}

// In main method:
House myHouse = new House();

// When 'myHouse' is garbage collected, its 'livingRoom' and 'kitchen' objects,
// which are not accessible from anywhere else, will also be eligible for garbage collection.
```

---

### **Topic Summary & Revision**

| Concept | Relationship | Keywords/Implementation | Lifecycle | Example |
| :--- | :--- | :--- | :--- | :--- |
| **Inheritance**| "is-a" | `extends` | N/A | `Car` is a `Vehicle` |
| **Association**| "uses-a" | Field (instance variable) | Independent | `Driver` uses a `Car` |
| **Aggregation**| "has-a" (weak)| Field (instance variable) | Part can outlive the whole | `Department` has `Professor`s |
| **Composition**| "part-of" (strong)| Field (instance variable) | Part is destroyed with whole | `House` is composed of `Room`s |

---

### **MCQs for Exam Preparation (Tricky)**

1.  **Which of the following relationships is best modeled using inheritance?**
    (A) A `Library` and its `Book`s.
    (B) An `Employee` and their `Address`.
    (C) A `Rectangle` and a `Square`.
    (D) A `Car` and its `Tire`s.
    **Answer:** ||(C) A 'Square' 'is-a' specialized form of a 'Rectangle'. The others are all 'has-a' relationships: a Library has Books, an Employee has an Address, and a Car has Tires.||
<br>

2.  **A `University` class contains a `List` of `Student` objects. If the `University` object is destroyed, the `Student` objects should continue to exist because they might transfer to another university. Which relationship does this describe?**
    (A) Inheritance
    (B) Composition
    (C) Aggregation
    (D) Polymorphism
    **Answer:** ||(C) Aggregation. This is a classic 'whole-part' relationship ('University'-'Student'), but the parts ('Student's) have lifecycles independent of the whole. This is the definition of Aggregation.||
<br>

3.  **To enforce a Composition relationship between `Order` (the whole) and `LineItem` (the part), what is the best practice for creating `LineItem` objects?**
    (A) The `LineItem` objects are created outside the `Order` class and passed to its constructor.
    (B) The `LineItem` objects are created within the `Order` class, for example, in its constructor or a method like `addLineItem()`.
    (C) The `Order` class inherits from the `LineItem` class.
    (D) Use a static factory method to create both `Order` and `LineItem` objects.
    **Answer:** ||(B) In Composition, the 'whole' object is responsible for the creation and lifecycle of its 'parts'. Therefore, the 'Order' object should be the one to create its 'LineItem' instances, making it a strong, inseparable relationship. Option (A) describes Aggregation.||
<br>

4.  **What is a key reason Java designers chose to disallow multiple inheritance for classes?**
    (A) To improve runtime performance significantly.
    (B) To simplify the language and avoid the "Diamond Problem" of ambiguity.
    (C) To reduce the memory footprint of objects.
    (D) To enforce that all classes must ultimately inherit from the `Object` class.
    **Answer:** ||(B) The primary motivation was to avoid the ambiguity and complexity that arises when a class inherits two methods with the same signature from two different parent classes (the Diamond Problem). This keeps the language simpler and more robust.||
<br>

5.  **If `class B extends A` and `class C extends B`, which of the following statements is FALSE?**
    (A) This is an example of multilevel inheritance.
    (B) An object of type `C` is also an instance of `B` and `A`.
    (C) Class `C` can access `private` members of class `A`.
    (D) An object of type `C` can be stored in a reference variable of type `A`.
    **Answer:** ||(C) Inheritance never grants access to 'private' members of a superclass. Private members are accessible only within the class in which they are declared.||

---

### **Bonus Tips**

*   **Viva/Interview Tip:** The **"is-a" vs. "has-a"** distinction is the most important OOP design concept. Be ready to give clear examples. Inheritance (`is-a`) is often overused by beginners. A good rule of thumb: **"Favor Composition over Inheritance."** This means you should prefer to build complex objects out of simpler ones (`has-a`) rather than creating deep and rigid inheritance hierarchies (`is-a`). This leads to more flexible and maintainable designs.
*   **Exam Tip:** Look for keywords in the question. If you see "part of" and "cannot exist without," think **Composition**. If you see "has" and "can exist independently," think **Aggregation**.
*   **Lab Tip:** When designing your classes, always ask: "What is the relationship between these two entities?" Is it `is-a` or `has-a`? For example, for an `Employee` and a `Project`, an employee *is not* a project. An employee *works on* a project. This is an Association. This simple question will guide your design and prevent you from making logical errors.

**🔗Links:** [[Java Session 8 - Upcasting, Downcasting, Abstract class, Interface]]