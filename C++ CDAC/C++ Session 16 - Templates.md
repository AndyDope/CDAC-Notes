### **Session 16: Templates**

Welcome to Session 16. In our programming journey so far, if we wanted to write a function to swap two integers and another to swap two doubles, we would need to write two separate functions. This leads to code duplication. Templates are C++'s powerful solution to this problem, allowing us to write **generic**, type-independent code.

This concept, known as **generic programming**, is a cornerstone of modern C++, and it's what makes the Standard Template Library (STL) possible, which we will cover next.

---

#### **1. Introduction to Templates**

A **template** is a blueprint or a formula for creating a generic class or a function. It allows you to define a function or a class that can work with different data types without rewriting the entire code for each type.

The magic happens at **compile-time**. When the compiler sees you using a template with a specific type (like `int` or `string`), it automatically generates the necessary version of the function or class for that type. This process is called **template instantiation**.

**Analogy:**
Think of a cookie cutter. The cookie cutter is the **template**. You can use the same cutter (template) with different kinds of dough (data types like `int`, `double`, `string`) to create perfectly shaped cookies (functions/classes). The cutter itself isn't a cookie; it's a tool to *make* cookies.

The two keywords you will use are:
*   `template`: To declare a template.
*   `typename` or `class`: To specify a generic type placeholder. `typename` is more modern and often preferred, but they are interchangeable in this context.

---

#### **2. Function Templates**

A function template is a blueprint for a generic function. You define the logic once, and it can be applied to any data type.

**Syntax:**
```cpp
template <typename T>
T functionName(T parameter1, T parameter2, ...) {
    // Function body using type T
}
```
Here, `T` is a placeholder for a data type that will be specified when the function is called.

**Example: A generic `max` function**
```cpp
#include <iostream>
#include <string>
using namespace std;

// 1. Define the function template
template <typename T>
T findMax(T a, T b) {
    return (a > b) ? a : b;
}

int main() {
    // 2. Use the template with different data types
    
    // Compiler instantiates findMax(int, int)
    cout << "Max of 10, 20 is: " << findMax(10, 20) << endl; 

    // Compiler instantiates findMax(double, double)
    cout << "Max of 5.5, 3.3 is: " << findMax(5.5, 3.3) << endl;

    // Compiler instantiates findMax(char, char)
    cout << "Max of 'a', 'g' is: " << findMax('a', 'g') << endl;
    
    // This would fail to compile because the '>' operator is not
    // defined for custom objects like a Student class by default.
    // The operations inside the template must be valid for the type.

    return 0;
}
```

> **Quick Question:** What is the process called when the compiler generates a specific version of a template function (e.g., for `int`) from the generic template definition?
> **Answer:** Template instantiation.

---

#### **3. Class Templates**

Just like functions, you can create generic classes. This is extremely useful for creating data structures that can hold any type of data, like a list, stack, or queue.

**Syntax:**
```cpp
template <typename T>
class MyClassName {
private:
    T memberVariable;
public:
    // Member functions using type T
    void setValue(T value);
    T getValue();
};
```

When you define the member functions outside the class declaration, you must restate the template prefix.

**Example: A generic `Box` class**
```cpp
#include <iostream>
#include <string>
using namespace std;

// 1. Define the class template
template <typename T>
class Box {
private:
    T content;
public:
    void setContent(T newContent);
    T getContent();
};

// 2. Define member functions outside the class
template <typename T>
void Box<T>::setContent(T newContent) {
    content = newContent;
}

template <typename T>
T Box<T>::getContent() {
    return content;
}

int main() {
    // 3. Create objects (instantiate the class) for specific types
    Box<int> intBox;
    intBox.setContent(123);
    cout << "Integer box contains: " << intBox.getContent() << endl;

    Box<string> stringBox;
    stringBox.setContent("Hello C++");
    cout << "String box contains: " << stringBox.getContent() << endl;

    return 0;
}
```
Notice the syntax `Box<int>` and `Box<string>`. You must explicitly specify the data type in angle brackets when creating an object from a class template. This is different from function templates, where the compiler can often deduce the type from the arguments.

> **Quick Question:** If you have a class template `template <typename T> class Storage;`, how would you declare an object named `myStore` that can store `double` values?
> **Answer:** `Storage<double> myStore;`

---

### **Topic Summary & Revision**

*   **Generic Programming:** Templates enable writing code that works with any data type, reducing code duplication. ^115c3b
*   **Keywords:** The `template` keyword begins a template definition. `typename` or `class` are used to declare a placeholder type (e.g., `T`).
*   **Function Templates:** Blueprints for functions. The compiler deduces the type from the arguments at the call site.
*   **Class Templates:** Blueprints for classes. You must explicitly specify the type in angle brackets (`<>`) when creating an object.
*   **Instantiation:** The process where the compiler generates the actual code for a specific type from a template at compile-time. ^956979

---

### **#MCQs for Exam Preparation**

1.  **What is the primary purpose of templates in C++?**
    (A) To handle run-time errors.
    (B) To allow for generic programming.
    (C) To improve the speed of I/O operations.
    (D) To create derived classes.
    **Answer: (B)**
<br>
2.  **Which keyword is used to start the definition of a template?**
    (A) `generic`
    (B) `type`
    (C) `template`
    (D) `class`
    **Answer: (C)**
<br>
3.  **The process of creating a type-specific class or function from a template is called:**
    (A) Inheritance
    (B) Instantiation
    (C) Polymorphism
    (D) Encapsulation
    **Answer: (B)**
<br>
4.  **How do you create an object named `myStack` of a class template `Stack<T>` that will hold characters?**
    (A) `Stack myStack<char>;`
    (B) `Stack<char> myStack;`
    (C) `Stack myStack(char);`
    (D) `char<Stack> myStack;`
    **Answer: (B)**
<br>
5.  **Consider the function template: `template <typename T> void print(T val)`. How does the compiler know which type to use when you call `print(42)`?**
    (A) It defaults to `int`.
    (B) It deduces the type from the function argument.
    (C) You must explicitly state the type, like `print<int>(42)`.
    (D) It generates a run-time error.
    **Answer: (B)** (While explicit specification `print<int>(42)` is possible, the compiler deduces it automatically from the argument `42` being an integer).

---

### **Bonus Tips**

*   **Viva/Interview Tip:** Templates are a form of **compile-time polymorphism**. This is a great term to use. Unlike [[C++ Session 12 - Virtual Functions and Abstract Class#**2. The Solution `virtual` Functions and Dynamic Binding**|run-time polymorphism]] (which uses virtual functions), template resolution happens entirely during compilation. Also, mention that the **Standard Template Library (STL)** is the most prominent and powerful application of templates in C++.
*   **Exam Tip:** Pay close attention to syntax. Questions often test the correct syntax for defining a template (`template <typename T>`), defining a template member function outside the class (`template <typename T> void MyClass<T>::func()`), and instantiating a template class object (`MyClass<int> obj;`).
*   **Lab Tip:** A very common and frustrating error occurs when you separate template definitions into a `.h` (declaration) and `.cpp` (definition) file like you do with regular classes. For most compilers, the **entire template definition (both declaration and implementation) must be in the header file**. This is because the compiler needs the full definition to be able to instantiate the template for any given type when it processes the file including the header.

**🔗Links:** [[C++ Sessions 17 & 18 - STL and RTTI|Next Sessions 17 & 18]]