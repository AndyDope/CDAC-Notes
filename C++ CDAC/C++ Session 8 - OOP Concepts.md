### **Session 8: OOP Concepts**

Welcome to Session 8. We now shift from procedural programming to the **Object-Oriented Programming (OOP)** paradigm. This is the main feature that distinguishes [[C++ Session 1 - Getting Started#2. The Need for C++ & C++ versus C|C++ from C]]. OOP helps us model real-world problems in our code, leading to programs that are more organized, reusable, and easier to maintain.

---

#### **1. Classes and Objects**

These are the fundamental building blocks of OOP.

**a) Class**
A **class** is a user-defined blueprint or template for creating objects. It bundles together data (called **attributes** or **member variables**) and the functions that operate on that data (called **methods** or **member functions**).

**Analogy:** A class is like the architectural blueprint for a house. It defines the properties (number of rooms, color of walls) and functionalities (open door, turn on lights), but it is not a house itself.

**b) Object**
An **object** is an instance of a class. It is a concrete entity created from the class blueprint, which has its own state (values for its attributes) and behavior.

**Analogy:** An object is the actual house built from the blueprint. You can build many houses (objects) from the same blueprint (class), and each house can have different properties (one is blue, another is green).

**Example:**
```cpp
#include <iostream>
#include <string>
using namespace std;

// This is the CLASS (the blueprint)
class Student {
public: // We'll discuss this next
    // Attributes (Data Members)
    string name;
    int rollNo;

    // Method (Member Function)
    void display() {
        cout << "Name: " << name << ", Roll No: " << rollNo << endl;
    }
};

int main() {
    // This is an OBJECT (an instance of the Student class)
    Student s1; 

    // Accessing and setting the object's attributes
    s1.name = "Anjali";
    s1.rollNo = 101;

    // Calling the object's method
    s1.display(); // Output: Name: Anjali, Roll No: 101

    return 0;
}
```

> **Quick Question:** Using the "**house blueprint**" analogy, what would be an "**object**"?
> **Answer:** An actual house built from that blueprint.

---

#### **2. Access Specifiers (`public`, `private`, `protected`) & Encapsulation**

**Encapsulation** is the bundling of data and the methods that operate on that data into a single unit (the class). A key part of encapsulation is **data hiding**—restricting direct access to an object's data members. This is achieved using access specifiers.

*   `public`: Members are accessible from anywhere outside the class. This is the public "interface" of your object.
*   `private`: Members can only be accessed by other member functions **inside the same class**. This is the default for classes and is used to hide and protect the object's internal state.
*   `protected`: Similar to `private`, but also allows access by derived (child) classes. We'll explore this more in [[C++ Session 10 - Inheritance - extending class|Inheritance]].

**Example with Encapsulation:**
By making `rollNo` private, we can enforce rules (like `rollNo` must be positive) using a public "setter" method.

```cpp
class Student {
private: // Data is now protected
    int rollNo;

public: // Functions to access the data are public
    void setRollNo(int r) {
        if (r > 0) { // We can add validation logic here
            rollNo = r;
        }
    }

    int getRollNo() {
        return rollNo;
    }
};

int main() {
    Student s1;
    // s1.rollNo = 101; // COMPILE ERROR! Cannot access private member.
    s1.setRollNo(101);  // This is the correct way.

    cout << "Roll No is: " << s1.getRollNo() << endl;
    return 0;
}
```

> **Quick Question:** Which access specifier should you use for member variables to achieve good encapsulation?
> **Answer:** `private`.

---

#### **3. The Pillars of OOP**

Your syllabus mentions the core concepts of OOP, which are often called the "four pillars." We've already discussed encapsulation. Here's a brief introduction to the others, which we will detail in upcoming sessions.

*   **Abstraction:** Hiding complex implementation details and showing only the essential features of the object. For example, you know how to use a TV remote (the interface) without needing to know how its internal circuits work (the implementation). Getters and setters are a form of abstraction. ^e9adea
*   **Inheritance:** The ability to create a new class (child class) from an existing class (parent class). The child class inherits the attributes and methods of the parent, allowing for code reuse. We will cover this in detail in **[[C++ Session 10 - Inheritance - extending class|extending class]]**. ^f6a695
*   **Polymorphism:** The ability to present the same interface for differing underlying forms (data types). For example, a `draw()` function could draw a circle, a square, or a triangle depending on the object type. This is covered in **[[C++ Session 11 - Polymorphism|Polymorphism]]** and **[[C++ Session 12 - Virtual Functions and Abstract Class|Virtual Functions and Abstract Class]]**. ^dd9d6a

---

#### **4. Namespaces**

We have seen `using namespace std;` before. A **namespace** is a declarative region that provides a scope to the [[C++ Sessions 2 & 3 - Beginning with C++#2. C++ Tokens|identifiers]] (names of types, functions, variables, etc.) inside it. They are used to organize code into logical groups and to prevent name collisions that can occur in large projects.

**Example:**
```cpp
// Creating our own namespace
namespace MyMath {
    int add(int a, int b) { return a + b; }
}

namespace MyGraphics {
    // Imagine another function also named 'add'
    // There is no collision due to the different namespaces
    void add(Shape s1, Shape s2) { /* ... */ } 
}

int main() {
    // Using the 'add' function from the MyMath namespace
    cout << MyMath::add(5, 3); // Outputs: 8
    
    return 0;
}
```
The `::` is the **Scope Resolution Operator**.

---

### **Topic Summary & Revision**

*   **Class:** A blueprint for creating objects. It contains attributes (data) and methods (functions).
*   **Object:** An instance of a class.
*   **Encapsulation:** Bundling data and methods together and using **access specifiers** (`public`, `private`) to hide and protect the data.
*   **Pillars of OOP:** Encapsulation, Abstraction, Inheritance, and Polymorphism.
*   **Namespaces:** A way to group related code and prevent name conflicts using the scope resolution operator (`::`).

---

### **#MCQs for Exam Preparation**

1.  **Which of the following best describes a "class" in C++?**
    (A) An instance of an object.
    (B) A blueprint or template for creating objects.
    (C) A function that creates memory.
    (D) A variable that holds an address.
    **Answer: (B)**
<br>
2.  **The mechanism of bundling data and functions together into a single unit is called:**
    (A) Inheritance
    (B) Polymorphism
    (C) Abstraction
    (D) Encapsulation
    **Answer: (D)**
<br>
3.  **Which access specifier makes a member accessible only within its own class?**
    (A) `public`
    (B) `private`
    (C) `protected`
    (D) `internal`
    **Answer: (B)**
<br>
4.  **Creating an object from a class is called:**
    (A) Declaration
    (B) Instantiation
    (C) Prototyping
    (D) Inheritance
    **Answer: (B)**
<br>
5.  **Which operator is used to access members of a namespace?**
    (A) `.` (dot operator)
    (B) `->` (arrow operator)
    (C) `::` (scope resolution operator)
    (D) `&` (address-of operator)
    **Answer: (C)**

---

### **Bonus Tips**

*   **Viva/Interview Tip:** "What are the four pillars of OOP?" is one of the most common C++ interview questions. Be able to name them (Encapsulation, Abstraction, Inheritance, Polymorphism) and give a simple one-sentence definition for each. The car or house analogies work very well here.
*   **Lab Tip:** For the lab assignment ("Write a Student class"), remember the principle of encapsulation. Make your data members (`rollNo`, `marks`, etc.) `private` and provide `public` "getter" and "setter" functions to access and modify them. This is a standard and expected practice.
*   **Best Practice:** By default, all members in a `class` are `private`. It's good practice to always explicitly write the `private:` specifier for clarity.

**🔗Links:** [[C++ Session 9 - Constructors and Destructor|Session 9]]