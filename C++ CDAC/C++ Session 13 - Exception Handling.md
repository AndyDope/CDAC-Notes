### **Session 13: Exception Handling**

Welcome to Session 13. So far, our programs have assumed a "happy path" where everything works correctly. But in the real world, errors happen: users enter invalid input, files can't be found, network connections drop. **Exception handling** is a powerful, structured mechanism for responding to these run-time errors in a way that prevents your program from crashing.

---

#### **1. Exception Handling Introduction**

An **exception** is an unexpected event or error that occurs during the execution of a program.

*   **Traditional Error Handling:** In C, you might handle errors by returning a special error code (like -1 or `NULL`) from a function and then using an `if` statement to check for it. This can make the code cluttered and hard to read, as error-checking logic is mixed with normal program flow.
*   **C++ Exception Handling:** C++ provides a formal system using three keywords: `try`, `throw`, and `catch`. This separates the error-handling code from the main logic, leading to cleaner and more robust programs.

**Analogy:** Imagine a factory assembly line (your normal program flow). If a machine breaks down (an exception), you don't just let the whole line crash. You hit a big red button (`throw`) that stops the line and sends a signal to a specific repair station (`catch`) designed to handle that particular breakdown.

---

#### **2. The `try`, `throw`, and `catch` Blocks**

This is the core mechanism of C++ exception handling.

*   **`try` block:** You place the code that might generate an exception inside a `try` block. This is the code you are "trying" to execute. ^ebcd58
*   **`throw` keyword:** When an error occurs inside the `try` block, you signal it by using the `throw` keyword, followed by a value (an error code, a string, or an [[C++ Session 8 - OOP Concepts#1. Classes and Objects|object]]). This value carries information about the error. ^f8febc
*   **`catch` block:** The `catch` block immediately follows the `try` block. It is the "exception handler." It specifies the type of exception it can catch. If the type of the `throw`n value matches the type in the `catch` block, that block is executed.

**Example: Division by Zero**
```cpp
#include <iostream>
using namespace std;

double divide(int a, int b) {
    if (b == 0) {
        // Throw an exception because division by zero is not allowed.
        throw "Error: Division by zero!"; 
    }
    return static_cast<double>(a) / b;
}

int main() {
    try {
        double result = divide(10, 0); // This line will cause an exception
        cout << "The result is: " << result << endl; // This line will be skipped
    } catch (const char* msg) { // Catches a C-style string literal
        cout << "Exception caught: " << msg << endl;
    }
    cout << "Program continues after handling the exception." << endl;
    return 0;
}
```

> **Quick Question:** Which block contains the code that might cause an error, and which block contains the code that handles it?
> **Answer:** The `try` block contains the code that might cause the error, and the `catch` block handles it.

---

#### **3. Catching Multiple Exceptions and Re-throwing**

A `try` block can be followed by multiple `catch` blocks to handle different types of exceptions. The order matters: they are checked sequentially, so you should catch more specific exception types before more general ones.

*   **`catch(...)`:** The "catch-all" block uses an ellipsis (`...`) and will catch any type of exception. It should always be placed last.
*   **Re-throwing:** Inside a `catch` block, you can use the `throw;` statement (with no argument) to re-throw the *same* exception. This allows a handler to perform some local cleanup (e.g., log the error) and then pass the exception up to a higher-level handler.

**Example:**
```cpp
void processData() {
    try {
        // ... some code ...
        if (bad_input) throw string("Bad input string");
        if (math_error) throw 101; // Throw an integer error code
    }
    catch (const string& s) { // Specific catch for string
        cout << "Inner catch (string): " << s << endl;
        throw; // Re-throw the exception to be handled by main
    }
    catch (int errCode) { // Specific catch for int
        cout << "Inner catch (int): Error code " << errCode << endl;
    }
}

int main() {
    try {
        processData();
    }
    catch (const string& s) { // Catches the re-thrown exception
        cout << "Main caught re-thrown exception: " << s << endl;
    }
    catch (...) { // Catch-all block
        cout << "Main caught an unknown exception." << endl;
    }
}
```

> **Quick Question:** If you have `catch(Base&)` and `catch(Derived&)` handlers, which one should come first?
> **Answer:** The `catch(Derived&)` block should come first, as it is more specific.

---

#### **4. Custom Exception Classes**

Throwing basic types like `int` or `const char*` is okay, but it's much better practice to define your own exception classes. This allows you to bundle more detailed information about the error. A common practice is to inherit from the standard `std::exception` class.

**Benefits:**
*   More organized and descriptive.
*   Can carry more data about the error state.
*   Fits nicely into the [[C++ Session 10 - Inheritance - extending class|inheritance]] hierarchy.

**Example:**
```cpp
#include <exception> // Required for std::exception

// Custom exception class
class MyException : public std::exception {
public:
    // Override the what() method from std::exception
    const char* what() const noexcept override {
        return "Something bad happened in my application!";
    }
};

int main() {
    try {
        throw MyException();
    }
    catch (const std::exception& e) { // Catch by reference to the base class
        cout << e.what() << endl; // Calls the overridden what() method
    }
}
```

---

#### **5. Specifying Exceptions (`noexcept`)**

In modern C++, you can specify whether a function is allowed to throw exceptions using the `noexcept` specifier.
*   `noexcept` is a promise that the function will **not** throw any exceptions.
*   This allows the compiler to perform significant optimizations, as it doesn't need to generate cleanup code for exception handling.
*   If a function marked `noexcept` *does* try to let an exception escape, the program will terminate immediately by calling `std::terminate`.

**Example:**
```cpp
// This function promises not to throw.
void my_safe_function() noexcept {
    // ... code that doesn't throw ...
}
```

---

### **Topic Summary & Revision**

*   **Exceptions:** A mechanism to handle run-time errors in a structured way.
*   **Core Keywords:** `try` (code to monitor), `throw` (signals an error), `catch` (handles the error).
*   **Multiple Handlers:** You can have multiple `catch` blocks to handle different exception types. A `catch(...)` block will catch any exception and must be last.
*   **Re-throwing:** A `catch` block can use `throw;` to pass the exception to a higher-level handler.
*   **Custom Exceptions:** It's best practice to create your own exception classes, often by inheriting from `std::exception`, to provide more meaningful error information.
*   **`noexcept`:** A specifier that promises a function will not throw, allowing for compiler optimizations.

---

### **#MCQs for Exam Preparation**

1.  **Which keyword is used to signal that an error has occurred?**
    (A) `try`
    (B) `catch`
    (C) `throw`
    (D) `exception`
    **Answer: (C)**
<br>
2.  **A `try` block can be followed by:**
    (A) Only one `catch` block.
    (B) Multiple `catch` blocks.
    (C) Only a `throw` statement.
    (D) Only a `finally` block.
    **Answer: (B)**
<br>
3.  **The "catch-all" handler is denoted by:**
    (A) `catch(all)`
    (B) `catch(void*)`
    (C) `catch()`
    (D) `catch(...)`
    **Answer: (D)**
<br>
4.  **In modern C++, what is the best way to declare that a function will not throw any exceptions?**
    (A) `void my_func() throw();` (Deprecated)
    (B) `void my_func() noexcept;`
    (C) `void my_func() const;`
    (D) By adding a comment `// no exceptions here`.
    **Answer: (B)**
<br>
5.  **What is a major benefit of creating a custom exception class inheriting from `std::exception`?**
    (A) It makes the program run faster.
    (B) It allows you to override the `what()` method to provide a descriptive error message.
    (C) It automatically frees all allocated memory.
    (D) It is the only way to throw an exception.
    **Answer: (B)**

---

### **Bonus Tips**

*   **Viva/Interview Tip:** A key question is, "When should you use exceptions?" Answer: For *exceptional*, synchronous, run-time errors that prevent a function from fulfilling its purpose (e.g., can't open a required file, division by zero). Don't use them for normal flow control (like exiting a loop).
*   **RAII (Resource Acquisition Is Initialization):** This is a fundamental C++ concept closely related to exceptions. It means that you should acquire a resource in an [[C++ Session 9 - Constructors and Destructor|object's constructor]] and release it in the [[C++ Session 9 - Constructors and Destructor#4. Destructor|destructor]]. This guarantees that the resource is released even if an exception is thrown, as destructors are automatically called during stack unwinding.
*   **Lab Tip:** For the custom exception class lab, make sure your class inherits from `public std::exception`. In your `main`, `catch` the exception using `catch(const std::exception& e)` and print the message using `e.what()`. This demonstrates polymorphic exception handling.

**🔗Links:** [[C++ Session 14 - Managing Console IO Operations|Session 14]]