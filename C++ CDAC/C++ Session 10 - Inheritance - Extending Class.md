### **Session 10: Inheritance - Extending Class**

Welcome to Session 10. Inheritance is a powerful mechanism in C++ that allows us to create a new class (the "child") that inherits properties and behaviors from an existing class (the "parent"). This promotes an "is-a" relationship (e.g., a "Car" is-a "Vehicle") and is fundamental to building logical, reusable, and extensible code hierarchies. This is one of the main [[C++ Session 8 - OOP Concepts#3. The Pillars of OOP|pillars of OOP]].

---

#### **1. The Basics of Inheritance**

*   **Base Class (Parent/Superclass):** The class whose properties are inherited.
*   **Derived Class (Child/Subclass):** The class that inherits from the base class. It can add its own new members and methods.

**Syntax:**
`class DerivedClassName : access_mode BaseClassName { ... };`

*   `access_mode` can be `public`, `protected`, or `private`. **`public` inheritance is the most common** and represents a true "is-a" relationship.

**The Role of Access Specifiers in Inheritance**

The `access_mode` in the declaration, combined with the [[C++ Session 8 - OOP Concepts#2. Access Specifiers (`public`, `private`, `protected`) & Encapsulation|access specifiers]] inside the base class, determines how base class members are inherited.

| Base Class Specifier | `public` Inheritance | `protected` Inheritance | `private` Inheritance |
| :--- | :--- | :--- | :--- |
| **`public`** member | Becomes `public` | Becomes `protected` | Becomes `private` |
| **`protected`** member | Becomes `protected`| Becomes `protected` | Becomes `private` |
| **`private`** member | **Not accessible** | **Not accessible** | **Not accessible** |

**Key Takeaway:** `private` members of the base class are never directly accessible by the derived class. `protected` members are designed specifically to be accessible by derived classes but not by the outside world.

> **Quick Question:** If a member is declared as `protected` in a base class, can a derived class access it directly?
> **Answer:** Yes. That is the primary purpose of the `protected` specifier.

---

#### **2. Types of Inheritance**

C++ supports several types of inheritance, allowing for flexible class design.

*   **1. Single Inheritance:** A derived class inherits from only one base class. (`A -> B`)
    ```cpp
    class Vehicle { ... };
    class Car : public Vehicle { ... }; // Single Inheritance
    ```
*   **2. Multilevel Inheritance:** A class is derived from another derived class, forming a chain. (`A -> B -> C`)
    ```cpp
    class Vehicle { ... };
    class Car : public Vehicle { ... };
    class SportsCar : public Car { ... }; // Multilevel Inheritance
    ```
*   **3. Multiple Inheritance:** A derived class inherits from more than one base class. (`A, B -> C`)
    ```cpp
    class Printer { ... };
    class Scanner { ... };
    class MultifunctionPrinter : public Printer, public Scanner { ... }; // Multiple
    ```
*   **4. Hierarchical Inheritance:** Multiple derived classes inherit from a single base class. (`A -> B, A -> C`)
    ```cpp
    class Shape { ... };
    class Circle : public Shape { ... }; // Hierarchical
    class Rectangle : public Shape { ... }; // Hierarchical
    ```
*   **5. Hybrid Inheritance:** A combination of two or more of the above types of inheritance (e.g., combining Hierarchical and Multiple).

> **Quick Question:** You need to model a `Laptop` and a `Desktop` which both share properties of a `Computer`. What type of inheritance is this?
> **Answer:** Hierarchical Inheritance.

---

#### **3. Constructors and Destructors in Inheritance**

The order in which constructors and destructors are called in an inheritance hierarchy is fixed and very important.

*   **Constructor Call Order:** **Base class constructor is called FIRST**, then the derived class constructor.
*   **Destructor Call Order:** The reverse. **Derived class destructor is called FIRST**, then the base class destructor.

**Analogy:** When building a house (Derived), you must first build the foundation (Base). When demolishing it, you tear down the house (Derived) before you remove the foundation (Base).

**Example:**
```cpp
class Base {
public:
    Base() { cout << "Base constructor called." << endl; }
    ~Base() { cout << "Base destructor called." << endl; }
};

class Derived : public Base {
public:
    Derived() { cout << "Derived constructor called." << endl; }
    ~Derived() { cout << "Derived destructor called." << endl; }
};

int main() {
    Derived d;
    return 0;
}
// Output:
// Base constructor called.
// Derived constructor called.
// Derived destructor called.
// Base destructor called.
```

To pass arguments to a base class [[C++ Session 9 - Constructors and Destructor#**1. Constructors**|constructor]], you use the **member initializer list**:
```cpp
// Passing 'name' up to the Base constructor
Derived(string name) : Base(name) { 
    cout << "Derived constructor called." << endl;
}
```

> **Quick Question:** In a multilevel inheritance `A -> B -> C`, what is the order of constructor calls when an object of class `C` is created?
> **Answer:** `A`'s constructor, then `B`'s, then `C`'s.

---

#### **4. The Diamond Problem and Virtual Base Class**

Multiple inheritance can lead to a problem known as the **"Diamond Problem."**

*   **Problem:** Consider `Student -> Test`, `Student -> Sports`, and `Test, Sports -> Result`. The `Result` class will inherit the members of `Student` twice (once via `Test` and once via `Sports`). This causes ambiguity and bloated object size.
*   **Solution:** The `virtual` keyword. By making the inheritance from the top-most base class `virtual`, you ensure that only **one copy** of its members is included in the final derived class.

**Example Solution:**
```cpp
class Student { ... };

// Use 'virtual' keyword here
class Test : virtual public Student { ... }; 
// And here
class Sports : virtual public Student { ... };

// Result now gets only ONE copy of Student's members
class Result : public Test, public Sports { ... }; 
```

---

### **Topic Summary & Revision**

*   **Inheritance:** Creates an "is-a" relationship, allowing a derived class to inherit members from a base class. The most common form is `public` inheritance.
*   **Access Control:** `private` members are never inherited. `protected` members are inherited but remain inaccessible to the outside world.
*   **Types:** Single, Multilevel, Multiple, Hierarchical, and Hybrid.
*   **Constructor/Destructor Order:** Constructors run Base-to-Derived. Destructors run Derived-to-Base.
*   **Virtual Base Class:** Solves the "Diamond Problem" in multiple inheritance by ensuring only one instance of the top-level base class is inherited.

---

### **#MCQs for Exam Preparation**

1.  **If class `B` inherits from class `A`, what is the order of constructor calls when an object of `B` is created?**
    (A) Constructor of B, then constructor of A.
    (B) Constructor of A, then constructor of B.
    (C) Only the constructor of B is called.
    (D) The order is not guaranteed.
    **Answer: (B)**
<br>
2.  **A `protected` member of a base class is accessible by:**
    (A) Only the base class itself.
    (B) The base class and its derived classes.
    (C) Any function in the program.
    (D) Only the `main` function.
    **Answer: (B)**
<br>
3.  **What problem does the `virtual` base class solve?**
    (A) Slow compilation time.
    (B) Ambiguity caused by multiple inheritance (The Diamond Problem).
    (C) Prevents a class from being inherited.
    (D) Allows private members to be inherited.
    **Answer: (B)**
<br>
4.  **A `Professor` inherits from `Person`, and a `Student` also inherits from `Person`. This is an example of:**
    (A) Multiple Inheritance
    (B) Multilevel Inheritance
    (C) Hybrid Inheritance
    (D) Hierarchical Inheritance
    **Answer: (D)**
<br>
5.  **Which members of a base class are never accessible to a derived class?**
    (A) `public` members
    (B) `protected` members
    (C) `private` members
    (D) All members are accessible.
    **Answer: (C)**
<br>
---

### **Bonus Tips**

*   **Viva/Interview Tip:** "Explain the Diamond Problem and how to solve it" is a classic advanced C++ question. Being able to draw the diagram and explain the role of the `virtual` keyword will impress your interviewer.
*   **Exam Tip:** The order of constructor and destructor calls is a very frequent question in exams, both for MCQs and short-answer questions. Remember: **Constructors build from the base up; Destructors tear down from the top (derived) down.**
*   **Lab Tip:** For your lab assignment ("Design a hierarchy of computer printers"), you will use **Hierarchical Inheritance** (`LaserPrinter` and `InkjetPrinter` inheriting from `Printer`). If you were to add a `MultifunctionDevice` that can print and scan, you might use **Multiple Inheritance** (`MultifunctionDevice : public Printer, public Scanner`). The lab also mentions **friend functions**, which are a way to grant a non-member function or another class access to `private` and `protected` members. We will cover this formally in the next session.

**🔗Links:** [[C++ Session 11 - Polymorphism|Session 11]]