### **Session 9: Constructors and Destructor**

In the last session, we created [[C++ Session 8 - OOP Concepts#**1. Classes and Objects**|objects]] and then manually set their member values. C++ provides a more elegant and robust way to initialize objects the moment they are created. These special methods are called **constructors**. Their counterpart, **destructors**, handle the cleanup when an object is destroyed.

---

#### **1. Constructors**

A **constructor** is a special member function that is automatically called when an object of a class is created (instantiated). Its primary job is to initialize the object's data members.

**Key Properties:**
*   It has the **exact same name** as the class.
*   It has **no return type**, not even `void`.
*   It is usually `public`.

**a) Default Constructor**
A constructor that takes no arguments is called the default constructor. If you don't define any constructor, the compiler provides a default one for you that does nothing.

```cpp
class Cube {
public:
    int side;
    // This is a default constructor
    Cube() {
        side = 10; // Initialize 'side' to a default value
        cout << "Default constructor called." << endl;
    }
};

int main() {
    Cube c1; // c1 is created, default constructor is called automatically
    cout << "Side is: " << c1.side; // Outputs: Side is: 10
    return 0;
}
```

**b) Parameterized Constructor**
A constructor that accepts arguments. This is the most common type, as it allows you to initialize an object with specific values at the time of its creation. ^e7e6cf

```cpp
class Rectangle {
public:
    int length, breadth;
    // This is a parameterized constructor
    Rectangle(int l, int b) {
        length = l;
        breadth = b;
        cout << "Parameterized constructor called." << endl;
    }
};

int main() {
    Rectangle r1(10, 5); // r1 is created and initialized in one step
    cout << "Length: " << r1.length; // Outputs: Length: 10
    return 0;
}
```

**c) Multiple Constructors (Constructor Overloading)**
A class can have multiple constructors with different parameter lists. This is a form of function overloading, a type of **[[C++ Session 11 - Polymorphism|Polymorphism]]**. The compiler chooses the correct constructor based on the arguments provided during object creation.

```cpp
class Box {
public:
    int volume;
    // Default constructor
    Box() { volume = 1; } 
    // Parameterized constructor
    Box(int s) { volume = s * s * s; }
};

int main() {
    Box b1;         // Calls the default constructor. b1.volume is 1.
    Box b2(5);      // Calls the parameterized constructor. b2.volume is 125.
}
```
> **Quick Question:** What are the two main rules for a function to be a constructor?
> **Answer:** 1. It must have the same name as the class. 2. It must have no return type.

---

#### **2. Copy Constructor**

A **copy constructor** is a special constructor that creates a new object as a **copy of an existing object**.

**Signature:** `ClassName(const ClassName &other_object)`
*   `const`: Ensures the original object `other_object` is not modified.
*   `&`: It's crucial to pass the object by **[[C++ Session 5 - Functions in C++#3. Call by Reference|reference]]** to avoid an infinite loop of the compiler trying to make copies to pass to the copy constructor.

If you don't provide one, the compiler creates a default copy constructor that performs a "shallow copy" (member-wise copy).

```cpp
class Point {
public:
    int x, y;
    // Parameterized constructor
    Point(int x1, int y1) { x = x1; y = y1; }

    // Explicit Copy Constructor
    Point(const Point &p) {
        x = p.x;
        y = p.y;
        cout << "Copy constructor called!" << endl;
    }
};

int main() {
    Point p1(10, 20);   // Calls parameterized constructor
    Point p2 = p1;      // Calls copy constructor
    // Point p3(p1);    // Also calls copy constructor (alternative syntax)

    cout << "p2.x = " << p2.x << endl; // p2.x = 10
    return 0;
}
```

---

#### **3. Dynamic Initialization of Objects**

This concept combines parameterized constructors with [[C++ Sessions 6 & 7 - Memory Management and Pointers#3. Dynamic Memory Allocation: `new` and `delete`|dynamic memory allocation]]. It means initializing objects at runtime by passing values to the constructor when allocating memory on the heap.

```cpp
#include <iostream>
using namespace std;

class Circle {
public:
    double radius;
    Circle(double r) { radius = r; }
    double getArea() { return 3.14 * radius * radius; }
};

int main() {
    double r;
    cout << "Enter radius: ";
    cin >> r;

    // Dynamically create a Circle object on the heap and initialize it
    Circle *c_ptr = new Circle(r);

    cout << "Area is: " << c_ptr->getArea();

    delete c_ptr; // Don't forget to free the memory
    return 0;
}
```

> **Quick Question:** Which operator is used to create and initialize an object on the heap in one step?
> **Answer:** The `new` operator, followed by the class name and constructor arguments.

---

#### **4. Destructor**

A **destructor** is a special member function that is automatically called just before an object is destroyed. Its primary purpose is to **release resources** that the object may have acquired during its lifetime (e.g., memory allocated on the heap, open files, database connections).

**Key Properties:**
*   It has the **exact same name** as the class, prefixed with a **tilde (`~`)**.
*   It has **no return type**.
*   It takes **no arguments**. A class can only have one destructor.

**Example:**
```cpp
class ResourceHolder {
private:
    int *data;
public:
    ResourceHolder() {
        data = new int[100]; // Allocate memory in the constructor
        cout << "Resource allocated." << endl;
    }

    // Destructor to free the allocated memory
    ~ResourceHolder() {
        delete[] data; // Crucial cleanup step
        cout << "Resource freed." << endl;
    }
};

int main() {
    {
        ResourceHolder rh; // Object created, constructor called
    } // rh goes out of scope here, destructor is called automatically

    return 0; // Output will show "Resource allocated." then "Resource freed."
}
```

> **Quick Question:** What is the main symbol that distinguishes a destructor's name from a constructor's name?
> **Answer:** The tilde (`~`) prefix.

---

### **Topic Summary & Revision**

*   **Constructor:** Initializes an object when it's created. Has the same name as the class and no return type.
*   **Types of Constructors:**
    *   **Default:** No arguments.
    *   **Parameterized:** Takes arguments for initialization.
    *   **Copy:** Initializes an object from another existing object.
*   **Destructor:** Cleans up resources before an object is destroyed. Has the class name prefixed with a tilde (`~`), no return type, and no parameters.
*   **Life Cycle:** Constructor is called at the "birth" of an object. Destructor is called at its "death".

---

### **#MCQs for Exam Preparation**

1.  **Which of the following statements is true about constructors?**
    (A) They can have any name.
    (B) They must have a `void` return type.
    (C) They are called automatically when an object is created.
    (D) A class can have only one constructor.
    **Answer: (C)**
<br>
2.  **A constructor that takes no arguments is called:**
    (A) A parameterized constructor
    (B) A copy constructor
    (C) A default constructor
    (D) A friend constructor
    **Answer: (C)**
<br>
3.  **What is the correct signature for a copy constructor for a class named `Car`?**
    (A) `Car(Car other)`
    (B) `void Car(Car &other)`
    (C) `Car(const Car &other)`
    (D) `~Car(Car &other)`
    **Answer: (C)**
<br>
4.  **What is the primary role of a destructor?**
    (A) To create a copy of an object.
    (B) To initialize the data members of an object.
    (C) To free resources allocated by an object.
    (D) To return the object's memory address.
    **Answer: (C)**
<br>
5.  **How many destructors can a class have?**
    (A) 0
    (B) 1
    (C) 2
    (D) As many as needed (overloaded).
    **Answer: (B)**

---

### **Bonus Tips**

*   **Viva/Interview Tip:** A very common question is, "When do you need to write your own copy constructor?" The answer is: "When your class manages a resource, like raw [[C++ Sessions 6 & 7 - Memory Management and Pointers|memory pointers]]. The default (shallow) copy will only copy the pointer, not the data it points to, leading to two objects pointing to the same memory, which is dangerous."
*   **The Rule of Three:** This is a classic C++ rule of thumb. It states that if you need to explicitly declare any of the following for your class, you almost certainly need to declare all three:
    1.  Copy Constructor
    2.  Copy Assignment Operator (we will see this later)
    3.  Destructor
    This is because all three are usually needed when your class is managing a resource.
*   **Lab Tip:** Forgetting to write a destructor that calls `delete` for memory allocated with `new` in the constructor is the most common cause of **memory leaks** in C++ programs. Always match your `new` with a `delete` in the destructor.

**🔗Links:** [[C++ Session 10 - Inheritance - Extending Class|Session 10]]