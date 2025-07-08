### **Conditional and Looping Statements**

This session is crucial. We'll learn how to control the "flow" of our program. Instead of running code line-by-line from top to bottom, we'll learn to make decisions and repeat actions. We'll also cover arrays, our first data structure for storing collections of data.

---

#### **1. Conditional Statements (`if`, `else if`, `switch`)**

Conditional statements allow your program to execute different blocks of code based on whether a [[C++ Sessions 2 & 3 - Beginning with C++#5. Operators|condition]] is `true` or `false`.

**a) `if`, `else if`, `else`**

This is the most fundamental decision-making structure.

*   `if`: Executes a block of code if its condition is true.
*   `else if`: If the first `if` is false, this condition is checked.
*   `else`: If all preceding conditions are false, this block is executed.

**Example: Grading System**
```cpp
#include <iostream>
using namespace std;

int main() {
    int score = 85;

    if (score >= 90) { // Uses a relational operator
        cout << "Grade is A";
    } else if (score >= 80) {
        cout << "Grade is B"; // This block will be executed
    } else if (score >= 70) {
        cout << "Grade is C";
    } else {
        cout << "Grade is F";
    }

    return 0;
}
```

**b) `switch` statement**

A `switch` statement is an alternative to `if-else if-else` when you are checking a **single variable** against a list of [[C++ Sessions 2 & 3 - Beginning with C++#2. C++ Tokens|constant]] integer or character values.

*   `case`: Checks if the variable matches this value.
*   `break`: **Crucial!** It stops execution within the `switch` block.
*   `default`: Runs if no other case matches.

**Example: Menu Selection**
```cpp
int choice = 2;

switch (choice) {
    case 1:
        cout << "You chose Option 1.";
        break;
    case 2:
        cout << "You chose Option 2.";
        break;
    default:
        cout << "Invalid choice.";
        break;
}
```

> **Quick Question:** What happens in a `switch` statement if you forget to add a `break` statement after a `case`?
> **Answer:** The code will "fall through" and execute the code in the next `case` block(s) until it hits a `break` or the end of the `switch`.

---

#### **2. Looping Statements (`for`, `while`, `do-while`)**

Loops are used to execute a block of code repeatedly as long as a certain condition is met.

**a) `for` loop**

Ideal when you know **exactly how many times** you want to iterate.
**Structure:** `for` ([[C++ Sessions 2 & 3 - Beginning with C++#3. Initialization of Variables|initialization]]; `condition`; `update`)

```cpp
// This loop will run 5 times (for i = 0, 1, 2, 3, 4)
for (int i = 0; i < 5; i++) {
    cout << "Iteration number: " << i << endl;
}
```

**b) `while` loop**

Best when you don't know the number of iterations beforehand. The condition is checked **before** executing the loop body.

```cpp
int num = 1;
while (num <= 5) { // The condition
    cout << "Value of num: " << num << endl;
    num++; // Don't forget the update!
}
```

**c) `do-while` loop**

The condition is checked **after** the loop body. Guarantees the loop will execute **at least once**.

```cpp
int choice;
do {
    cout << "Enter 0 to exit: ";
    cin >> choice;
} while (choice != 0); // Condition is checked at the end
```

> **Quick Question:** Which loop structure guarantees that its body will be executed at least one time?
> **Answer:** The `do-while` loop.

---

#### **3. Jump Statements (`break`, `continue`, `return`)**

Jump statements change the normal flow of control.

*   `break`: Immediately **terminates** the innermost loop or `switch` statement.
*   `continue`: Skips the rest of the current iteration and **jumps to the next iteration** of the loop.
*   `return`: Immediately **exits the entire function**, returning a value if specified. (See [[C++ Session 1 - Getting Started#4. Writing Your First C++ Program (Hello, World!)|return in main]])

**Example:**
```cpp
for (int i = 1; i <= 10; i++) {
    if (i == 3) {
        continue; // Skip the rest of this iteration
    }
    if (i == 8) {
        break; // Exit the loop entirely
    }
    cout << i << " "; // Output: 1 2 4 5 6 7
}
```

> **Quick Question:** In a loop, what is the difference between `break` and `continue`?
> **Answer:** `break` exits the loop entirely, while `continue` just skips the current iteration and moves to the next one.

---

#### **4. Arrays**

An array stores a fixed-size collection of elements of the **same data type** in **contiguous memory locations**.

**Analogy:** An array is like a street of houses. The street has a name (`arrayName`), and each house has an address number (the `index`), starting from 0.

**a) Declaration and Initialization**

```cpp
// Declaration: an array named 'marks' that can hold 5 integers.
int marks[5]; 

// Initialization
marks[0] = 80; // Assign value to the first element (index 0)

// Combined Declaration and Initialization
int scores[5] = {98, 87, 92, 79, 85};
```
The last element's index is always `size - 1`.

**b) 1-D and 2-D Arrays**

*   **1-D Array:** A single list of elements (`scores` above).
*   **2-D Array:** An "array of arrays," representing a grid or a matrix.

**Example: 2-D Array (3x3 Matrix)**
```cpp
int matrix[3][3] = {
    {1, 2, 3},  // Row 0
    {4, 5, 6},  // Row 1
    {7, 8, 9}   // Row 2
};

// Access element in Row 1, Column 2
cout << matrix[1][2]; // Outputs: 6
```

> **Quick Question:** If you have an array declared as `int arr[10];`, what is the index of the very last element?
> **Answer:** The index is `9`.

---

### **Topic Summary & Revision**

*   **Conditionals:** Use `if-else if-else` for complex conditions. Use `switch` for checking a single variable against multiple constant values.
*   **Loops:** Use `for` for known iteration counts. Use `while` for unknown counts. Use `do-while` to ensure at least one execution.
*   **Jump Statements:** `break` exits a loop/switch, `continue` skips an iteration, and `return` exits a function.
*   **Arrays:** Fixed-size, same-type element collections. Accessed via zero-based index. 2-D arrays represent grids.

---

### **#MCQs for Exam Preparation**

1.  **If you forget the `break` statement in a `switch` case, what will happen?**
    (A) A compile-time error will occur.
    (B) The program will exit immediately.
    (C) Execution will "fall through" to the next case.
    (D) The `default` case will always be executed.
    <br>
    **Answer: (C)**

2.  **Which loop is most suitable for iterating through an array of a known size?**
    (A) `while`
    (B) `for`
    (C) `do-while`
    (D) `if-else`
    <br>
    **Answer: (B)**

3.  **What is the primary difference between a `while` loop and a `do-while` loop?**
    (A) A `do-while` loop is faster.
    (B) A `do-while` loop's body is guaranteed to execute at least once.
    (C) A `while` loop can only use integer conditions.
    (D) There is no difference.
    <br>
    **Answer: (B)**

4.  **Given `int arr[] = {10, 20, 30, 40};`, what does `arr[2]` refer to?**
    (A) 20
    (B) 30
    (C) 40
    (D) An error, the index is out of bounds.
    <br>
    **Answer: (B)**

5.  **Inside a `for` loop, which statement will cause the program to skip the current iteration and move to the next one?**
    (A) `break;`
    (B) `exit;`
    (C) `return;`
    (D) `continue;`
    <br>
    **Answer: (D)**

---

### **Bonus Tips**

*   **Exam Tip:** Be very careful with **"off-by-one" errors**. In a loop `for (int i = 0; i < 5; i++)`, the loop runs 5 times, but the last value of `i` is 4. This is a common mistake.
*   **Viva Tip:** A common question is, "When would you use a `switch` over an `if-else` chain?" Answer: "When checking a single variable against a series of discrete, constant integral or character values, as it can be more readable and sometimes more efficient."
*   **Lab Tip:** Master the use of nested `for` loops to process 2-D arrays (matrices). This is a fundamental pattern.

**🔗Links:** [[C++ Session 5 - Functions in C++|Next Session 5]]