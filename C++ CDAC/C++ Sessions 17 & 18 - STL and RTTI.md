### **Sessions 17 & 18: STL and RTTI**

Welcome to our final sessions on C++. Building directly on our last session on [[C++ Session 16 - Templates|Templates]], we now explore their most powerful application: the **Standard Template Library (STL)**. The STL provides a rich collection of pre-built, highly efficient, and generic data structures and algorithms.

We will also cover **Run-Time Type Information (RTTI)**, a mechanism that allows a program to determine the type of an object during execution, which is particularly useful in polymorphic scenarios.

---

#### **1. Introduction to the C++ Standard Library & STL**

The **C++ Standard Library** is a vast collection of classes and functions that are part of the C++ standard. It provides tools for strings, I/O streams, memory management, and much more.

The **Standard Template Library (STL)** is a core *part* of the C++ Standard Library. It is a set of C++ template classes that provide common data structures and algorithms. The STL is famous for its efficiency and generic nature. ^06b372

The STL has three main components:
1.  **Containers:** Generic data structures that store collections of objects (e.g., a dynamic array or a key-value dictionary).
2.  **Algorithms:** Generic functions that perform operations on containers (e.g., sorting, searching, copying).
3.  **Iterators:** "Smart pointers" that provide a uniform way to access elements in a container, acting as a bridge between containers and algorithms.

**Analogy:**
*   **Containers** are like different types of storage shelves (a bookshelf for sequential access, a filing cabinet with labels for quick lookup).
*   **Algorithms** are the tasks you want to perform (sort all the books alphabetically, find a specific file).
*   **Iterators** are like your hands or a bookmark; they point to a specific item on a shelf, allowing algorithms to work with any type of shelf.

---

#### **2. Working with Core STL Containers**

Let's look at some of the most common containers you'll use. These are defined in their own header files.

##### **`vector` - The Dynamic Array**
A `std::vector` is a sequence container that behaves like a dynamic array. It can grow or shrink in size automatically.
*   **Header:** `<vector>`
*   **Use when:** You need fast, random access to elements via an index (like a regular array) but also need the flexibility to add or remove elements.

**Example:**
```cpp
#include <iostream>
#include <vector>

int main() {
    std::vector<int> scores; // A vector to hold integers

    scores.push_back(95); // Add element to the end
    scores.push_back(88);
    scores.push_back(100);

    std::cout << "The first score is: " << scores[0] << std::endl;
    std::cout << "The vector size is: " << scores.size() << std::endl;
    
    // Looping through a vector using an iterator (common pattern)
    for(auto it = scores.begin(); it != scores.end(); ++it) {
        std::cout << *it << " ";
    }
    std::cout << std::endl;

    return 0;
}
```

> **Quick Question:** What is the main advantage of a `vector` over a standard C-style array?
> **Answer:** Its ability to automatically manage its size (grow and shrink).

##### **`stack` - Last-In, First-Out (LIFO)**
A `std::stack` is a container adapter that provides a **LIFO** (Last-In, First-Out) data structure.
*   **Header:** `<stack>`
*   **Use when:** You need to model a process where the last item added is the first one to be removed. Think of a stack of plates or a browser's "Back" button history.

**Example:**
```cpp
#include <iostream>
#include <stack>

int main() {
    std::stack<std::string> browser_history;

    browser_history.push("google.com");
    browser_history.push("cdac.in");
    browser_history.push("know-it.com");

    std::cout << "Currently on page: " << browser_history.top() << std::endl; // Look at top element

    browser_history.pop(); // "Go back"

    std::cout << "After clicking back: " << browser_history.top() << std::endl;

    return 0;
}
```

> **Quick Question:** Which function do you use to access the top element of a `stack` without removing it?
> **Answer:** `top()`.

##### **`queue` - First-In, First-Out (FIFO)**
A `std::queue` is another container adapter, providing a **FIFO** (First-In, First-Out) data structure.
*   **Header:** `<queue>`
*   **Use when:** You need to process items in the order they were received. Think of a line of people waiting for a ticket.

**Example:**
```cpp
#include <iostream>
#include <queue>

int main() {
    std::queue<std::string> ticket_line;

    ticket_line.push("Person A");
    ticket_line.push("Person B");
    ticket_line.push("Person C");

    std::cout << "Now serving: " << ticket_line.front() << std::endl; // Access the front element
    ticket_line.pop(); // Serve the person
    std::cout << "Next in line: " << ticket_line.front() << std::endl;

    return 0;
}
```

> **Quick Question:** If you `push` items A, B, and C into a `queue` in that order, which item will be returned by the first call to `front()`?
> **Answer:** Item A.

##### **`map` - Key-Value Pairs**
A `std::map` is an associative container that stores elements as **key-value pairs**, sorted by key.
*   **Header:** `<map>`
*   **Use when:** You need to look up a value based on a unique key. Think of a dictionary (key=word, value=definition) or a phone book (key=name, value=number).

**Example:**
```cpp
#include <iostream>
#include <map>
#include <string>

int main() {
    std::map<std::string, int> student_marks;

    // Insert elements using square brackets
    student_marks["Rohan"] = 92;
    student_marks["Priya"] = 98;
    
    // Insert using the insert function
    student_marks.insert(std::make_pair("Amit", 85));

    std::cout << "Priya's marks: " << student_marks["Priya"] << std::endl;

    return 0;
}
```

---

#### **3. Introduction to RTTI (Run-Time Type Information)**

**RTTI** is a mechanism that allows you to discover the dynamic type of an object during the program's execution (at runtime). This is primarily used in the context of [[C++ Session 11 - Polymorphism|polymorphism]], where you might have a base class pointer pointing to a derived class object and need to know the actual type of the object it's pointing to.

RTTI is provided through two main operators:
1.  **`typeid` operator:** Returns an object containing information about the type of an expression. You need to include the `<typeinfo>` header. ^802f96
2.  **`dynamic_cast` operator:** Used for safe downcasting in a class hierarchy. It safely converts a pointer from a base class to a derived class, returning `nullptr` if the cast is not possible. We saw this in [[C++ Session 12 - Virtual Functions and Abstract Class#**5. Casting Operators**|Casting Operators]].

**Example using `typeid`:**
```cpp
#include <iostream>
#include <typeinfo> // Required for typeid

class Base {
public:
    virtual ~Base() {} // Virtual destructor is needed for RTTI to work correctly with polymorphism
};
class Derived : public Base {};

int main() {
    Base* b_ptr = new Derived();

    // Check the dynamic type at runtime
    if (typeid(*b_ptr) == typeid(Derived)) {
        std::cout << "b_ptr points to a Derived object." << std::endl;
    }
    
    // The .name() member gives an implementation-defined name of the type
    std::cout << "Type name: " << typeid(*b_ptr).name() << std::endl;

    delete b_ptr;
    return 0;
}
```

> **Quick Question:** When is RTTI information available: at compile-time or at run-time?
> **Answer:** At run-time.

---

### **Topic Summary & Revision**

*   **STL:** A library of generic **Containers**, **Algorithms**, and **Iterators** built using [[C++ Session 16 - Templates|Templates]].
*   **Core Containers:**
    *   **`vector`:** A dynamic array for fast random access. Header: `<vector>`.
    *   **`stack`:** A LIFO data structure. Header: `<stack>`.
    *   **`queue`:** A FIFO data structure. Header: `<queue>`.
    *   **`map`:** A sorted collection of key-value pairs. Header: `<map>`.
*   **RTTI:** Run-Time Type Information allows you to identify an object's type during execution.
*   **RTTI Operators:** `typeid` (for type identification) and `dynamic_cast` (for safe downcasting). Requires the `<typeinfo>` header for `typeid`.

---

### **#MCQs for Exam Preparation**

1.  **Which STL container is most suitable for implementing a "undo" feature in a text editor?**
    (A) `std::queue`
    (B) `std::vector`
    (C) `std::stack`
    (D) `std::map`
    **Answer: (C)** (The last action performed is the first one to be undone - LIFO).
<br>
2.  **To store a list of student roll numbers and their corresponding names, which container is the most appropriate?**
    (A) `std::vector<string>`
    (B) `std::queue<int>`
    (C) `std::map<int, string>`
    (D) `std::stack<string>`
    **Answer: (C)** (A map is perfect for key-value pairs like roll number -> name).
<br>
3.  **The `typeid` operator is used for:**
    (A) Compile-time type checking.
    (B) Creating new data types.
    (C) Allocating memory for a type.
    (D) Run-time type identification.
    **Answer: (D)**
<br>
4.  **Which header file must be included to use `std::vector`?**
    (A) `<iostream>`
    (B) `<stl>`
    (C) `<vector>`
    (D) `<container>`
    **Answer: (C)**
<br>
5.  **Which function is used to add an element to the back of both a `std::queue` and a `std::vector`?**
    (A) `add()`
    (B) `push_back()` for `vector` and `push()` for `queue`.
    (C) `insert()`
    (D) `push()`
    **Answer: (B)** (`push_back` is for `vector`, while `push` is the convention for `stack` and `queue`).

---

### **Bonus Tips**

*   **Viva/Interview Tip:** A very common interview question is "When would you use a `vector` vs. a `list`?". Although `list` is not on your syllabus, know that a `vector` provides fast random access (`O(1)`), but slow insertion/deletion in the middle (`O(n)`). A `list` (doubly-linked list) provides slow random access (`O(n)`) but fast insertion/deletion anywhere (`O(1)`). Knowing the performance trade-offs of containers is a sign of a good programmer.
*   **Exam Tip:** Be prepared to write short code snippets that use the basic functions of these containers: `push_back`, `pop`, `push`, `top`, `front`, and accessing map elements with `[]`.
*   **RTTI Caution:** While RTTI is a useful tool, overusing it can be a sign of poor design. Often, a problem that seems to require `typeid` can be solved more elegantly using [[C++ Session 12 - Virtual Functions and Abstract Class#**2. The Solution `virtual` Functions and Dynamic Binding**|virtual functions]]. Use RTTI as a last resort, not a first choice.

#### 🎊This concludes the topics in our syllabus for C++.

---

- Go through a complete overview of the complete syllabus in one go **🔗[[C++ Overview]]**.
- Or try some **#MCQs** based on the complete syllabus and test your knowledge **🔗[[C++ MCQs|C++ MCQs]]**.