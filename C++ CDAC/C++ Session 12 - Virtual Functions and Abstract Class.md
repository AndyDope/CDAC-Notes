### **Session 12: Virtual Functions and Abstract Class**

Welcome to Session 12. We previously discussed [[C++ Session 11 - Polymorphism#**1. Types of Polymorphism**|compile-time polymorphism]]. Now, we'll explore **run-time polymorphism**, which allows C++ to make decisions about which function to execute *while the program is running*. This is achieved through **virtual functions** and is the key to writing truly flexible and extensible object-oriented code.

---

#### **1. The Problem: Static Binding with Pointers**

Consider a base class pointer pointing to a derived class object. This is a very common scenario in OOP.

```cpp
class Animal {
public:
    void makeSound() { cout << "Animal makes a sound" << endl; }
};

class Dog : public Animal {
public:
    void makeSound() { cout << "Dog barks: Woof!" << endl; }
};

int main() {
    Animal* ptr = new Dog(); // Base class pointer, derived class object
    ptr->makeSound();        // Which function is called?
    delete ptr;
    return 0;
}
```
**Output:**
`Animal makes a sound`

**Why?** By default, C++ uses **static binding**. The compiler looks at the type of the **pointer** (`Animal*`), not the type of the **object** it points to (`Dog`). So, it calls the base class version of the function. This is often not what we want.

---

#### **2. The Solution: `virtual` Functions and Dynamic Binding**

To enable run-time polymorphism (or dynamic binding), we use the `virtual` keyword in the base class.

A **virtual function** is a member function that you expect to be redefined (overridden) in derived classes. When you declare a function as `virtual` in the base class, you are telling the compiler: "Don't decide which version of this function to call at compile time. Wait until run time and check the type of the actual object." ^f129e5

**Example with `virtual`:**

```cpp
class Animal {
public:
    // Mark this function as virtual
    virtual void makeSound() { cout << "Animal makes a sound" << endl; }
    virtual ~Animal() {} // Important: Make destructors virtual too!
};

class Dog : public Animal {
public:
    // This function now overrides the base class version
    void makeSound() override { cout << "Dog barks: Woof!" << endl; }
};

int main() {
    Animal* ptr = new Dog();
    ptr->makeSound(); // The magic happens here
    delete ptr;
    return 0;
}
```
**Output:**
`Dog barks: Woof!`

**Key Point:** When a [[C++ Session 10 - Inheritance - extending class#**1. The Basics of Inheritance**|base class]] destructor is declared `virtual`, it ensures that the correct [[C++ Session 9 - Constructors and Destructor#**4. Destructor**|destructor]] (the derived one, then the base one) is called when you `delete` a derived object through a base class pointer. **This is crucial to prevent memory leaks.**

The `override` keyword (optional but highly recommended) tells the compiler that this function is intended to override a base class virtual function. It will cause a compile error if no such function exists in the base class, preventing typos and bugs.

> **Quick Question:** What keyword do you use in a base class to enable run-time polymorphism for a specific function?
> **Answer:** The `virtual` keyword.

---

#### **3. Pure Virtual Functions and Abstract Classes**

Sometimes, a base class cannot provide a meaningful implementation for a function. For example, what sound does a generic `Animal` make? It's an abstract concept.

A **pure virtual function** is a virtual function that has no implementation in the base class. It acts as a placeholder and forces any non-abstract derived class to provide an implementation.

**Syntax:** `virtual return_type functionName(parameters) = 0;`

An **abstract class** is a class that has at least one pure virtual function.
*   You **cannot** create an object of an abstract class.
*   It is designed to be a contract for its derived classes. Any class that inherits from it *must* implement all of its pure virtual functions, or it too becomes an abstract class. ^3a6ff5

**Example:**
```cpp
// Shape is now an Abstract Class because it has a pure virtual function
class Shape {
public:
    // = 0 makes it a pure virtual function
    virtual void draw() = 0; 
};

class Circle : public Shape {
public:
    // Circle MUST provide an implementation for draw()
    void draw() override { cout << "Drawing a circle." << endl; }
};

int main() {
    // Shape sh; // COMPILE ERROR! Cannot instantiate an abstract class.
    Shape* s_ptr = new Circle();
    s_ptr->draw(); // Outputs: Drawing a circle.
    delete s_ptr;
    return 0;
}
```

> **Quick Question:** What happens if a derived class does not implement all of the pure virtual functions it inherits from its base class?
> **Answer:** The derived class also becomes an abstract class.

---

#### **4. Interfaces**

In C++, an **interface** is created by defining an abstract class that contains **only pure virtual functions** and no data members. It represents a pure contract of behavior without any implementation details. Any class that inherits from this "interface" class must implement all its functions.

---

#### **5. Casting Operators**

C++ provides more specific and safer casting operators than the old C-style cast `(type)expression`.

*   **`static_cast<new_type>(expr)`:**
    *   A compile-time cast. Used for "sensible" or predictable conversions (e.g., `int` to `float`, or casting a derived class [[C++ Sessions 6 & 7 - Memory Management and Pointers#**5. Class Pointers and the `this` Pointer**|pointer]] up to a base class pointer). It's fast but doesn't do run-time checks.
    *   `float f = static_cast<float>(10);`
*   **`dynamic_cast<new_type>(expr)`:**
    *   A run-time cast used specifically for safe downcasting in a polymorphic class hierarchy (classes with at least one virtual function).
    *   It checks if the object is *actually* of the target type. If the cast succeeds, it returns a valid pointer; otherwise, it returns `nullptr`.
    *   `Circle* c = dynamic_cast<Circle*>(shape_ptr); if (c) { ... }`
*   **`const_cast<new_type>(expr)`:**
    *   Used to add or (more commonly) remove the `const` qualifier from a variable. This is the only cast that can do this. Use with extreme caution as it can lead to undefined behavior if you modify a value that was originally `const`.
    *   `const int x = 10; int* p = const_cast<int*>(&x);`
*   **`reinterpret_cast<new_type>(expr)`:**
    *   The most powerful and dangerous cast. It simply reinterprets the bit pattern of one type as another. Used for low-level, non-portable operations, like converting a pointer to an integer.
    *   `long addr = reinterpret_cast<long>(ptr);`

---

### **Topic Summary & Revision**

*   **Run-time Polymorphism:** Enabled by `virtual` functions, it allows the program to decide which overridden function to call at run time based on the object's actual type. ^d52bb2
*   **Virtual Function:** A function in a base class declared with `virtual`, intended to be overridden by derived classes.
*   **Virtual Destructor:** Crucial for preventing memory leaks when deleting a derived object via a base class pointer.
*   **Pure Virtual Function (`= 0`):** A virtual function with no implementation in the base class.
*   **Abstract Class:** A class with at least one pure virtual function. It cannot be instantiated and serves as a contract for derived classes. ^b582b0

---

### **#MCQs for Exam Preparation**

1.  **Run-time polymorphism is achieved using:**
    (A) Function overloading
    (B) Operator overloading
    (C) Templates
    (D) Virtual functions
    **Answer: (D)**
<br>
2.  **What is the syntax for a pure virtual function?**
    (A) `virtual void func() { }`
    (B) `virtual void func() = 0;`
    (C) `static virtual void func();`
    (D) `void func() pure;`
    **Answer: (B)**
<br>
3.  **Which statement is true about an abstract class?**
    (A) You can create objects of an abstract class.
    (B) It must have only pure virtual functions.
    (C) You cannot create an object of an abstract class.
    (D) It cannot have a constructor.
    **Answer: (C)**
<br>
4.  **Why is it important for a base class to have a virtual destructor?**
    (A) To ensure the constructor of the base class is called.
    (B) To allow the class to be abstract.
    (C) To ensure the correct derived class destructor is called when deleting via a base pointer.
    (D) To make the destructor faster.
    **Answer: (C)**
<br>
5.  **Which cast is used for safe downcasting in a polymorphic hierarchy?**
    (A) `static_cast`
    (B) `const_cast`
    (C) `reinterpret_cast`
    (D) `dynamic_cast`
    **Answer: (D)**
---

### **Bonus Tips**

*   **Viva/Interview Tip:** "What is the difference between compile-time and run-time polymorphism?" is a very common question. Use the function overloading vs. virtual function examples. Also, be ready to explain *why* a base class destructor should be virtual.
*   **Exam Tip:** The concept of an abstract class as a "contract" is important. Any question asking how to *force* a derived class to implement a certain method is hinting at pure virtual functions.
*   **Lab Tip:** For the lab ("implement hierarchy of computer printers" using virtual/pure virtual functions), your base `Printer` class should likely be an abstract class. Functions like `print()` or `getTonerLevel()` might be pure virtual because every type of printer does it differently.

**🔗Links:** [[C++ Session 13 - Exception Handling|Session 13]]