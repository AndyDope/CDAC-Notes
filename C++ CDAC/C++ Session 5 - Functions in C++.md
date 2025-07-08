### **Session 5: Functions in C++**

Welcome to Session 5. So far, we've written all our code inside the `main` function. Now, we will learn how to create our own reusable blocks of code called **functions**. Functions are the building blocks of a well-organized and efficient program. They allow us to break down a large problem into smaller, manageable pieces.

---

#### **1. Different Forms of Functions**

A function is a named block of code that performs a specific task. The basic syntax is:
`return_type function_name(parameter_list);`

Functions can be categorized based on whether they accept arguments (input) or return a value (output).

**a) No arguments, no return value:**
The function takes no input and gives no output back. It just performs an action.
```cpp
void sayHello() {
    cout << "Hello, there!";
}
```

**b) With arguments, no return value:**
The function takes input to work with but doesn't return a calculated value.
```cpp
void printSum(int a, int b) {
    cout << "Sum is: " << a + b;
}
```

**c) With arguments, with a return value:**
This is the most common form. The function takes input, processes it, and returns a result.
```cpp
int add(int a, int b) {
    return a + b;
}
```

**d) No arguments, with a return value:**
The function takes no input but generates and returns a value.
```cpp
int getSystemStatusCode() {
    // some logic to get status...
    return 1; 
}
```

> **Quick Question:** If you create a function to calculate the area of a rectangle that takes length and width as input, what would be an appropriate return type for it?
> **Answer:** `int` or `double`, since it needs to return the calculated area.

---

#### **2. Function Prototyping**

The C++ compiler reads your code from top to bottom. If you try to call a function before it has been defined, the compiler won't know it exists and will throw an error.

A **function prototype** (or forward declaration) is a declaration of a function that tells the compiler about its name, return type, and parameters without providing the function's body. This allows you to define your functions *after* the `main` function, which can make your code more readable.

**Example:**
```cpp
#include <iostream>
using namespace std;

// Function Prototype
void displayMessage(string msg); 

int main() {
    displayMessage("Hello from main!"); // This works because of the prototype above
    return 0;
}

// Function Definition
void displayMessage(string msg) {
    cout << msg << endl;
}
```

> **Quick Question:** What are the three essential pieces of information a function prototype provides to the compiler?
> **Answer:** The function's name, its return type, and the data types of its parameters.

---

#### **3. Call by Reference**

By default, C++ passes arguments to functions by **value**. This means the function receives a **copy** of the original variable. Any changes made to the parameter inside the function do **not** affect the original variable outside the function.

**Call by Reference** provides a way for the function to work with the **original** variable. Instead of passing a copy, we pass a *reference* (the variable's memory address). This is highly efficient and allows the function to modify the original data.

**Analogy:**
*   **Call by Value:** You give me a *photocopy* of your notes. I can scribble on it, but your original notes are safe.
*   **Call by Reference:** You give me the *original notebook*. Any changes I make are permanent.

We use an ampersand (`&`) in the parameter list to signify call by reference.

**Example: Swapping two numbers**
```cpp
// This function can modify the original 'x' and 'y' from main
void swap(int &a, int &b) {
    int temp = a;
    a = b;
    b = temp;
}

int main() {
    int x = 10, y = 20;
    cout << "Before: x=" << x << ", y=" << y << endl; // Before: x=10, y=20

    swap(x, y); // Pass the original variables

    cout << "After: x=" << x << ", y=" << y << endl;  // After: x=20, y=10
    return 0;
}
```

> **Quick Question:** What symbol is used in a function's parameter list to indicate that an argument should be passed by reference?
> **Answer:** The ampersand (`&`).

---

#### **4. Inline Functions**

Every time you call a regular function, there is a small performance overhead (the program has to jump to the function's location, execute it, and then jump back). For very small, simple functions that are called many times inside a [[C++ Session 4 - Conditional and Looping Statements#2. Looping Statements (`for`, `while`, `do-while`)|loop]], this overhead can add up.

The `inline` keyword is a **request** to the compiler. It suggests that the compiler replace the function call directly with the function's code. This eliminates the function call overhead.

*   It's only a suggestion; the compiler can ignore it.
*   It's best used for very short, one-line functions.

**Example:**
```cpp
// Requesting the compiler to make this an inline function
inline int cube(int s) {
    return s * s * s;
}

int main() {
    int result = cube(5); // Compiler might replace this with: int result = 5 * 5 * 5;
    cout << result;
    return 0;
}
```
> **Quick Question:** Is the `inline` keyword a command or a suggestion to the compiler?
> **Answer:** It is a suggestion (or request).

---

### **Topic Summary & Revision**

*   **Functions:** Reusable blocks of code that make programs organized and modular. They can take arguments and can return a value.
*   **Function Prototype:** A declaration that informs the compiler about a function's signature before its actual definition, allowing you to call it from anywhere.
*   **Call by Value (Default):** Passes a copy of the argument. The original variable is not affected.
*   **Call by Reference (`&`):** Passes the original variable's memory address, allowing the function to modify the original data. It is efficient as no copy is made.
*   **Inline Functions:** A request to the compiler to replace the function call with its code, avoiding function call overhead. Best for small, frequently used functions.

---

### **#MCQs for Exam Preparation**

1.  **A function prototype must specify which of the following?**
    (A) The function's name and body.
    (B) The function's name, return type, and parameter types.
    (C) Only the function's name.
    (D) The local variables used in the function.
**Answer: (B)**
<br>
2.  **To allow a function to modify the original argument passed to it, the argument should be passed by:**
    (A) Value
    (B) `const`
    (C) Reference
    (D) Pointer (covered later, but Reference is the direct answer here)
**Answer: (C)**
<br>
3.  **What is the main purpose of an `inline` function?**
    (A) To make the function more secure.
    (B) To reduce function call overhead for small functions.
    (C) To allow the function to accept a variable number of arguments.
    (D) To ensure the function is defined in a separate file.
**Answer: (B)**
<br>
4.  **Consider `void myFunction(int x) { x = 100; }` and `int a = 10; myFunction(a);`. What is the value of `a` after the function call?**
    (A) 100
    (B) 10
    (C) 0
    (D) Compile Error
**Answer: (B)** (Because `x` is a copy of `a` - passed by value).
<br>
5.  **A function that does not return any value should have a return type of:**
    (A) `int`
    (B) `null`
    (C) `void`
    (D) `empty`
**Answer: (C)**

---
### **Bonus Tips**

*   **Viva Tip:** Be prepared to clearly explain the difference between **Call by Value** and **Call by Reference**. The photocopy vs. original document analogy is very effective for this.
*   **Exam Tip:** "Call by Reference" is a very important topic for theory, MCQs, and lab exams. The classic `swap` function example is frequently asked. Make sure you understand how to write it correctly using `&`.
*   **Best Practice:** It's generally good practice to place `main()` at the top of your file for readability and use prototypes for all other functions you define below it.

**🔗Links:** [[C++ Sessions 6 & 7 - Memory Management and Pointers|Next Session 6 & 7]]