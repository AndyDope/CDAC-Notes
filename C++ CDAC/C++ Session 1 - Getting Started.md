# Getting Started
---

### 1. Installation and Setup Development Environment

To write and run a C++ program, you need two main tools:

1.  **A Text Editor or IDE (Integrated Development Environment):** This is where you will write your human-readable code.
    *   **Examples:** VS Code, Code::Blocks, Dev-C++.
2.  **A Compiler:** This is a special program that translates your C++ code into machine code (an `.exe` file).
    *   **Popular Compiler:** `g++` (from the GNU Compiler Collection).

**Recommended Setup for PG-DAC:**
*   **Editor:** Visual Studio Code (VS Code)
*   **Compiler Suite:** MinGW-w64 (Provides `g++` on Windows)

> **Analogy:** The text editor is your **notebook** for writing a recipe. The compiler is the **translator** who converts the recipe into instructions a robot chef can understand.

---

### 2. The Need for C++ & C++ versus C

C++ was created by Bjarne Stroustrup to add **Object-Oriented Programming (OOP)** features to the C language. The goal was to manage the growing complexity of large software projects without sacrificing C's performance.

**C++ is a superset of C:** Almost any valid C program is also a valid C++ program.

#### Key Differences: C vs. C++

| Feature          | C                               | C++                                                   |
| :--------------- | :------------------------------ | :---------------------------------------------------- |
| **Paradigm**     | Procedural                      | Multi-paradigm (Procedural & **Object-Oriented**) |
| **Core Concept** | Functions & `struct`            | **Objects & Classes**                                 |
| **Data Security**| Less secure, data is exposed    | More secure via **Encapsulation** (data hiding)       |
| **Overloading**  | Not supported                   | **Function & Operator Overloading** are supported     |
| **Memory Mgmt**  | `malloc()`, `calloc()`, `free()`| **`new`** and **`delete`** operators                  |

---

### 3. Key Features of C++

-   **Object-Oriented:** The most important feature. Models real-world problems using classes and objects.
-   **Machine Independent (Portable):** Write once, compile anywhere (Windows, Linux, macOS).
-   **Mid-level Language:** Combines high-level features (classes) with low-level control (pointers).
-   **Rich Library Support:** The **Standard Template Library (STL)** provides powerful, ready-to-use data structures and algorithms.
-   **Fast and Powerful:** Compiled nature makes it ideal for performance-critical applications (e.g., game engines, operating systems).

---

### 4. Writing Your First C++ Program (`Hello, World!`)

The fundamental structure for a simple C++ program.

**Code: `HelloWorld.cpp`**
```cpp
// 1. Preprocessor Directive
#include <iostream>

// 2. Main Function - The entry point of the program
int main() {
    // 3. Statement to print text to the console
    std::cout << "Hello, World!";

    // 4. Return Statement
    return 0;
}
```
#### Code Breakdown:
1.  `#include <iostream>`: Includes the **i**nput/**o**utput **stream** library, necessary for `std::cout`.
2.  `int main()`: The **main function** where program execution begins. `int` signifies it returns an integer.
3.  `std::cout << "Hello, World!";`:
    *   `std::cout`: The standard output stream (the console).
    *   `<<`: The **stream insertion operator**. It "inserts" the data into the output stream.
    *   `;`: The semicolon terminates the statement.
4.  `return 0;`: Returns `0` to the operating system, indicating **successful execution**.

---
## Revision & Exam Prep

### Summary
- **Environment:** You need a **compiler (g++)** and an **editor (VS Code)**.
- **Core Idea:** C++ adds **OOP** to C for better organization and complexity management.
- **First Program:** `#include <iostream>`, `int main()`, `std::cout`, and `return 0;` are the essential building blocks.

### #MCQs
1.  **Who created C++?**
    - [ ] Dennis Ritchie
    - [ ] **Bjarne Stroustrup**
    - [ ] James Gosling

2.  **Purpose of `<iostream>`?**
    - [ ] Math functions
	- [ ] **Input and output operations**
    - [ ] String handling

3.  **Which is NOT a core OOP feature?**
    - [ ] Encapsulation
    - [ ] Inheritance
    - [ ] **Procedural execution**

4.  **Program execution begins where?**
    - [ ] `start()`
    - [ ] **`main()`**
    - [ ] `begin()`

5.  **What does `return 0;` signify?**
    - [ ] An error occurred
    - [ ] **Successful execution**
    - [ ] No value returned

6.  **Which operator is used for output with `cout`?**
    - [ ] `>>`
    - [ ] **`<<`**
    - [ ] `->`

**🔗Links:** [[C++ Sessions 2 & 3 - Beginning with C++|Next Session 2 & 3]]
