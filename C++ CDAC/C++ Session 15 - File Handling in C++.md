### **Session 15: File Handling in C++**

Welcome to Session 15. So far, all our data has been transient—it disappears when the program ends. To store data permanently, we need to use files. C++ provides a powerful set of file I/O classes that work just like the console [[C++ Session 14 - Managing Console IO Operations#**2. C++ Stream Classes and Standard Objects**|streams]] we just learned about, making file handling intuitive and consistent.

---

#### **1. Definition of a File**

A **file** is a collection of related data stored on a secondary storage device, like a hard disk or SSD. From the perspective of our program, we interact with files through file streams, which are very similar to the console streams (`cin` and `cout`).

The core header file for all file operations is **`<fstream>`**.

---

#### **2. File Stream Classes**

The `<fstream>` header provides three main classes for file handling:

*   **`ofstream` (output file stream):** Derived from `ostream`. It is used to create files and **write** data to them.
*   **`ifstream` (input file stream):** Derived from `istream`. It is used to **read** data from existing files.
*   **`fstream`:** Derived from `iostream`. It can be used for both **reading and writing** to the same file.

**Analogy:**
*   `ofstream` is like your pen, used only for writing on paper.
*   `ifstream` is like your eyes, used only for reading the paper.
*   `fstream` is like a pencil with an eraser—you can both write and read/modify.

> **Quick Question:** If you need to write a log of events from your program into a file named `log.txt`, which file stream class would you use?
> **Answer:** `ofstream`.

---

#### **3. Writing to a File (`ofstream`)**

The process involves three steps:
1.  Create an `ofstream` object.
2.  Open the file using the object's `open()` method or directly in the [[C++ Session 9 - Constructors and Destructor#**1. Constructors**|constructor]].
3.  Write to the file using the stream insertion operator (`<<`), just like with `cout`.
4.  Close the file using the `close()` method to save the changes.

**Example: Writing to a file**
```cpp
#include <iostream>
#include <fstream> // Must include this header!
#include <string>
using namespace std;

int main() {
    // 1. Create an ofstream object and open the file
    ofstream outFile("mydata.txt"); 

    // Check if the file opened successfully
    if (!outFile.is_open()) {
        cerr << "Error opening file for writing!" << endl;
        return 1;
    }

    // 2. Write to the file
    string name = "Ravi";
    int age = 25;
    outFile << "Name: " << name << endl;
    outFile << "Age: " << age << endl;

    // 3. Close the file
    outFile.close();

    cout << "Data written to file successfully." << endl;
    return 0;
}
```
*   If `mydata.txt` does not exist, it will be created.
*   If it exists, its contents will be **overwritten** by default.

> **Quick Question:** What function should you call on a file stream object to ensure all data is written and the file is properly saved?
> **Answer:** The `close()` method.

---

#### **4. Reading from a File (`ifstream`)**

The process is symmetrical to writing:
1.  Create an `ifstream` object.
2.  Open the file.
3.  Read from the file using the stream extraction operator (`>>`) or other methods like `getline()`.
4.  Close the file.

**Example: Reading from `mydata.txt`**
```cpp
#include <iostream>
#include <fstream>
#include <string>
using namespace std;

int main() {
    // 1. Create an ifstream object and open the file
    ifstream inFile("mydata.txt");

    if (!inFile.is_open()) {
        cerr << "Error opening file for reading!" << endl;
        return 1;
    }

    // 2. Read from the file
    string line;
    cout << "Reading from file:" << endl;
    
    // Read the file line by line until the end
    while (getline(inFile, line)) {
        cout << line << endl;
    }

    // 3. Close the file
    inFile.close();
    
    return 0;
}
```
*   `getline(inFile, line)` is used here to read entire lines, just as we did with `cin`.

> **Quick Question:** How can you check if a file was opened successfully after creating a file stream object?
> **Answer:** By using the `is_open()` method (e.g., `if (myFile.is_open()) { ... }`).

---

#### **5. File Modes**

When opening a file, you can specify a *file mode* to control its behavior. You can combine multiple modes using the `|` (bitwise OR) operator.

| Mode | Description |
| :--- | :--- |
| `ios::in` | Open for reading (default for `ifstream`). |
| `ios::out` | Open for writing (default for `ofstream`). |
| `ios::app`| **Append mode.** All output is added to the end of the file. |
| `ios::trunc`| **Truncate mode.** If the file exists, its contents are discarded. This is the default behavior for `ofstream` if `app` is not specified. |
| `ios::ate` | "At end." Opens the file and moves the control to the end of the file. |
| `ios::binary` | Opens the file in binary mode (instead of text mode). |

**Example: Appending to a file**
To add new data to a file without deleting the old data, use `ios::app`.

```cpp
// Open the file in output and append mode
ofstream outFile("mydata.txt", ios::out | ios::app); 
// or simply: ofstream outFile("mydata.txt", ios::app);

outFile << "This is new data appended to the file." << endl;
outFile.close();
```

---

### **Topic Summary & Revision**

*   **`<fstream>`:** The header file required for all C++ file I/O operations.
*   **Core Classes:**
    *   `ofstream`: For writing to files.
    *   `ifstream`: For reading from files.
    *   `fstream`: For both reading and writing.
*   **Basic Operations:**
    1.  Create a stream object and open the file (`myFile.open()` or in the constructor).
    2.  Check if the file is open (`myFile.is_open()`).
    3.  Perform read/write operations using `<<`, `>>`, or `getline()`.
    4.  Close the file (`myFile.close()`).
*   **File Modes:** Special flags like `ios::app` (append) and `ios::binary` that control how the file is opened and used.

---

### **#MCQs for Exam Preparation**

1.  **Which header file is essential for file handling in C++?**
    (A) `<iostream>`
    (B) `<string>`
    (C) `<file>`
    (D) `<fstream>`
    **Answer: (D)**
<br>
2.  **To read data from a file named `data.txt`, you would typically create an object of which class?**
    (A) `ofstream`
    (B) `ifstream`
    (C) `iostream`
    (D) `fstream`
    **Answer: (B)**
<br>
3.  **By default, opening a file with an `ofstream` object will:**
    (A) Append new data to the end of the file.
    (B) Ask the user for permission to write.
    (C) Overwrite the existing contents of the file.
    (D) Result in an error if the file already exists.
    **Answer: (C)** (This is due to the default `ios::trunc` mode).
<br>
4.  **Which file mode is used to add new data to the end of an existing file without deleting its original content?**
    (A) `ios::in`
    (B) `ios::ate`
    (C) `ios::app`
    (D) `ios::out`
    **Answer: (C)**
<br>
5.  **What is the purpose of the `is_open()` function?**
    (A) To open a file that is currently closed.
    (B) To check if a file has been successfully opened.
    (C) To check if a file is readable.
    (D) To close an open file.
    **Answer: (B)**

---

### **Bonus Tips**

*   **Viva/Interview Tip:** A key concept is **RAII (Resource Acquisition Is Initialization)**. File stream objects in C++ follow RAII. If you create a file stream object on the stack (e.g., `ofstream myFile("a.txt");`), its [[C++ Session 9 - Constructors and Destructor#4. Destructor|destructor]] will automatically call `close()` when the object goes out of scope. This is a safe and modern way to handle files, as it ensures they are closed even if an [[C++ Session 13 - Exception Handling|exception]] is thrown.
*   **Exam Tip:** Be prepared for questions that ask you to write a complete program to read data about a student (name, roll, marks) from a file and display it, or vice-versa. Master the `while (getline(inFile, line))` loop for reading.
*   **Lab Tip:** Always, always check if a file was opened successfully using `is_open()`. Attempting to read from or write to a file that failed to open will not crash your program, but it will put the stream into a "fail state" where all subsequent I/O operations will be ignored silently, which can be very difficult to debug.

**🔗Links:** [[C++ Session 16 - Templates|Session 16]]