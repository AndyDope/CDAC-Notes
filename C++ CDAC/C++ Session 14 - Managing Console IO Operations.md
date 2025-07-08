### **Session 14: Managing Console I/O Operations**

Welcome to Session 14. We've been using `cout <<` and `cin >>` since the very first session, but these are just the tip of the iceberg. The C++ I/O system is a powerful, type-safe, and extensible library built around a hierarchy of stream [[C++ Session 8 - OOP Concepts#1. Classes and Objects|classes]]. Today, we'll dive deeper into how this system works and learn how to format our console output professionally.

---

#### **1. Introduction to C++ Streams**

A **stream** is a sequence of bytes flowing from a source to a destination. It's an abstraction that allows us to treat different I/O devices (like the console, files, or network sockets) in a uniform way.

*   **Input Stream:** Extracts (reads) bytes from a source (e.g., keyboard).
*   **Output Stream:** Inserts (writes) bytes to a destination (e.g., screen).

This entire system is defined in the `<iostream>` header we've been including since [[C++ Session 1 - Getting Started|Session 1]].

---

#### **2. C++ Stream Classes and Standard Objects**

The stream library is built on a hierarchy of classes. The most important ones for console I/O are:
*   `istream`: The base class for input operations (like `cin`).
*   `ostream`: The base class for output operations (like `cout`).
*   `iostream`: A class derived via [[C++ Session 10 - Inheritance - extending class#**2. Types of Inheritance**|Multiple Inheritance]] from `istream` and `ostream`, handling both input and output.

C++ provides four predefined stream objects:
*   `cin`: (Console Input) An object of `istream` connected to the standard input device (keyboard).
*   `cout`: (Console Output) An object of `ostream` connected to the standard output device (screen). It is **buffered**, meaning output is collected and sent in chunks.
*   `cerr`: (Console Error) An `ostream` object for unbuffered error output. Output is sent immediately.
*   `clog`: (Console Log) An `ostream` object for buffered error output. Used for logging.

> **Quick Question:** If you need to print an urgent error message that must appear on the screen immediately, even if the program crashes, should you use `cout` or `cerr`?
> **Answer:** `cerr`, because it is unbuffered and writes immediately.

---

#### **3. Unformatted I/O Operations**

These functions read or write raw bytes without considering data types. They are useful for character-by-character or line-by-line input.

*   **`cin.get()`:** Reads a single character, including whitespace (like space, tab, or newline).
*   **`cin.getline(char* buffer, int size)`:** Reads a sequence of characters into a character array (`buffer`) until it encounters a newline character or has read `size-1` characters. It includes spaces in its input.

**Why is this important?** The standard `cin >> my_string;` operator stops reading at the first whitespace character. `getline` is essential for reading full names or sentences.

**Example:**
```cpp
char name[50];
cout << "Enter your full name: ";
cin.getline(name, 50); // Reads the entire line, including spaces
cout << "Hello, " << name << "!" << endl;
```
*   **`cout.put(char ch)`:** Writes a single character to the output stream.
*   **`cout.write(const char* buffer, int size)`:** Writes a specified number of characters from a buffer.

> **Quick Question:** If you want to read a user's full name (e.g., "Rahul Kumar") into a single variable, which function is more appropriate: `cin >>` or `cin.getline()`?
> **Answer:** `cin.getline()`.

---

#### **4. Formatted I/O and Manipulators**

Formatted I/O refers to using the stream insertion (`<<`) and extraction (`>>`) operators. These are powerful because they are overloaded for all basic data types.

**Manipulators** are special functions designed to be used with the `<<` and `>>` operators to modify the state of the stream, thus changing the format of the output (or input). To use manipulators that take arguments (like `setw` and `setprecision`), you must include the **`<iomanip>`** header.

**a) Width, Fill, and Alignment**
*   `setw(n)`: Sets the width for the *next* output operation to `n` characters.
*   `left` / `right`: Sets the alignment of the output within the width. `right` is the default.
*   `setfill(c)`: Sets the character `c` to be used for padding when the output is smaller than the set width.

**Example: Creating a formatted table**
```cpp
#include <iomanip> // Don't forget this header!

cout << left; // Set alignment to left for all subsequent outputs
cout << setfill('.'); // Set the fill character

cout << setw(15) << "Item" << setw(10) << "Price" << endl;
cout << setw(15) << "Apples" << setw(10) << 40 << endl;
cout << setw(15) << "Mangoes" << setw(10) << 120 << endl;

// Output:
// Item...........Price.....
// Apples.........40........
// Mangoes........120.......
```

**b) Floating-Point Precision**
*   `setprecision(n)`: Sets the total number of digits (before and after the decimal) to display.
*   `fixed`: Forces output in fixed-point notation (e.g., 123.45). When used, `setprecision` controls the number of digits *after* the decimal point.
*   `scientific`: Forces output in scientific notation (e.g., 1.2345e+02).

**Example:**
```cpp
double pi = 3.14159265;
cout << "Default: " << pi << endl;                   // 3.14159
cout << setprecision(3) << "Precision 3: " << pi << endl; // 3.14
cout << fixed << setprecision(4) << "Fixed: " << pi << endl; // 3.1416
```

> **Quick Question:** Which header file must you include to use manipulators like `setw` and `setprecision`?
> **Answer:** `<iomanip>`.

---

### **Topic Summary & Revision**

*   **Streams:** A powerful abstraction for handling I/O as a sequence of bytes. Key objects are `cin`, `cout`, `cerr`, and `clog`.
*   **Unformatted I/O:** Functions like `getline()` and `get()` are used to read raw data, including whitespace, which `>>` does not.
*   **Formatted I/O:** Handled by the `<<` and `>>` operators, which are a form of [[C++ Session 11 - Polymorphism#**3. Operator Overloading**|operator overloading]].
*   **Manipulators:** Functions used with I/O operators to control formatting. They can set width (`setw`), alignment (`left`/`right`), precision (`setprecision`), fill characters (`setfill`), and more.
*   **`<iomanip>`:** The header file required for manipulators that take arguments.

---

### **#MCQs for Exam Preparation**

1.  **To read an entire line of text including spaces into a character array, you should use:**
    (A) `cin >>`
    (B) `cin.get()`
    (C) `cin.getline()`
    (D) `cin.read()`
    **Answer: (C)**
<br>
2.  **Which manipulator is used to set the field width for the next output operation?**
    (A) `setprecision()`
    (B) `setw()`
    (C) `width()`
    (D) `setfill()`
    **Answer: (B)**
<br>
3.  **Which header file is required to use the `setprecision()` manipulator?**
    (A) `<iostream>`
    (B) `<string>`
    (C) `<istream>`
    (D) `<iomanip>`
    **Answer: (D)**
<br>
4.  **What is the primary difference between `cerr` and `clog`?**
    (A) `cerr` is for input, `clog` is for output.
    (B) `cerr` is unbuffered, while `clog` is buffered.
    (C) `cerr` can only print strings, `clog` can print numbers.
    (D) There is no difference.
    **Answer: (B)**
<br>
5.  **After using `cout << fixed;`, what does `cout << setprecision(2);` control?**
    (A) The total number of digits to be displayed.
    (B) The number of digits before the decimal point.
    (C) The number of digits after the decimal point.
    (D) It has no effect.
    **Answer: (C)**
	
---

### **Bonus Tips**

*   **Viva/Interview Tip:** Be ready to explain why `cin >> str` fails for full names and what the solution is (`getline`). This is a fundamental C++ I/O question that tests practical knowledge.
*   **Exam Tip:** Manipulators are a very common topic. Expect questions that ask you to write a code snippet to produce a specific, table-like formatted output. Practice using `setw`, `left`, `right`, and `setfill`.
*   **Sticky Manipulators:** Be aware that some manipulators are "sticky" (like `left`, `fixed`, `setfill`) and affect all subsequent output until changed. Others, like `setw()`, are "non-sticky" and only apply to the very next item being inserted into the stream.

**🔗Links:** [[C++ Session 15 - File Handling in C++|Session 15]]