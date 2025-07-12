# Beginning with C++

---

### 1. C++ Program Structure

A standard C++ program follows a predictable structure. This template is the foundation for most of your lab programs.

**Links:** [[C++ Session 1 - Getting Started|Getting Started]]

**Code: `Structure.cpp`**
```cpp
#include <iostream>

// Optional: This line allows us to use names like 'cout' directly
using namespace std; 

int main() {
    // Variable declaration and initialization
    int num = 10; 

    // Using the variable in an output statement
    cout << "The number is: " << num;

    return 0; 
}
```

**Key Additions:**
- `using namespace std;`: The `std` in `std::cout` refers to the **standard namespace**. A namespace is a container to prevent name conflicts. This line lets us use names like `cout` directly, which is convenient for small programs.
- `int num = 10;`: This is a **variable declaration**. It creates a memory location named `num` to hold an integer and initializes it with the value `10`.

---

### 2. C++ Tokens

A **token** is the smallest individual unit in a program that is meaningful to the compiler.

> **Analogy:** In the English sentence "She reads a book.", the tokens are "She", "reads", "a", "book", and ".".

**Main Token Types:**

| Token Type        | Description                             | Example                        |
| :---------------- | :-------------------------------------- | :----------------------------- |
| **Keywords**      | Reserved words with special meaning.    | `int`, `return`, `using`, `for`  |
| **Identifiers**   | Names given to variables, functions etc.| `main`, `num`, `calculateArea`   |
| **Constants**     | Fixed values that do not change.        | `10`, `3.14`, `"Hello"`        |
| **Strings**       | A sequence of characters.               | `"Hello, World!"`              |
| **Operators**     | Symbols that perform operations.        | `+`, `-`, `=`, `<<`            |
| **Special Symbols**| Punctuation like brackets, parens etc.  | `{ }`, `( )`, `;`              |

---

### 3. Initialization of Variables

Initialization means giving a variable its first value.

1.  **C-like Initialization (`=`):** The most common and readable method.
    ```cpp
    int a = 10;
    string name = "Ravi";
    ```
2.  **Brace Initialization (`{}`):** A more modern and safer method (from C++11). It prevents "narrowing conversions" (e.g., `int x = 5.5;` is an error with braces).
    ```cpp
    int b {20}; // a.k.a uniform initialization
    int c{};    // initializes to zero for numeric types
    ```

---

### 4. Constant and Static Members

These keywords modify the behavior of variables.

#### `const` (Constant)
The `const` keyword makes a variable **read-only**. Its value cannot be changed after initialization.

```cpp
const double PI = 3.14159;
// PI = 4.0; // COMPILE ERROR!
```

#### `static`
The `static` keyword gives a variable a lifetime that spans the entire program run.
- **Inside a function:** The variable is initialized only once and retains its value between calls.
- **Inside a class:** Creates a single variable that is **shared among all objects** of that class.

> **Analogy for `static` in a class:** In a `Car` class, `color` is unique to each car object. A `static int car_count;` variable would be a single counter shared by all cars.

---

### 5. Operators

Operators are symbols that perform operations on variables and values.

-   **Arithmetic:** `+` (add), `-` (subtract), `*` (multiply), `/` (divide), `%` (modulo/remainder).
    -   `int rem = 10 % 3; // rem will be 1`
-   **Relational:** `==` (is equal to), `!=` (not equal to), `>` (greater than), `<` (less than), `>=`, `<=`.
    -   Result in `true` or `false`.
    -   `bool isEqual = (5 == 5); // isEqual will be true`
-   **Logical:** `&&` (AND), `||` (OR), `!` (NOT). Used to combine conditions.
    -   `if (age > 18 && hasVoterId == true) { ... }`
-   **Assignment:** `=` (assigns a value).
-   **Unary:** Works on a single operand.
    -   `++` (increment), `--` (decrement), `&` (address-of).
    -   `int a = 5; a++; // a is now 6`
-   **Ternary Operator (`? :`)**: A shorthand for an if-else statement.
    -   **Syntax:** `condition ? value_if_true : value_if_false;`
    -   `int max_val = (a > b) ? a : b; // max_val gets the greater of a or b`

---
## Revision & Exam Prep

### Summary
- **Program Structure:** `#include`, `using namespace std;`, `int main() { ... }`, `return 0;`.
- **Tokens:** The smallest units: keywords, identifiers, constants, etc.
- **Initialization:** Giving a variable a value using `=` or `{}`.
- **`const`:** Creates a read-only variable.
- **`static`:** Creates a variable that persists or is shared among class objects.
- **Operators:** Symbols for arithmetic (`+`, `%`), comparison (`==`, `>`), logic (`&&`), and the ternary (`? :`) for compact if-else.

### #MCQs
1.  **Role of `using namespace std;`?**
    - [ ] Includes a library.
    - [x] **Allows using names from `std` namespace without the `std::` prefix.**
    - [ ] Declares a variable named `std`.

2.  **Which is NOT a C++ keyword?**
    - [ ] `int`
    - [ ] `static`
    - [x] **`main` (it's an identifier)**
    - [ ] `const`

3.  **A `const` variable must be...**
    - [ ] An integer.
    - [x] **Initialized at the time of declaration.**
    - [ ] A global variable.

4.  **Value of `result`: `int a = 5, b = 10; int result = (a > b) ? a : b;`?**
    - [ ] 5
    - [x] **10**
    - [ ] `true`

5.  **Which is a Logical Operator?**
    - [ ] `%`
    - [ ] `==`
    - [x] **`&&`**
    - [ ] `++`

6.  **`int value{};` results in `value` being:**
    - [ ] Uninitialized
    - [x] **Initialized to zero**
    - [ ] A compile error

**🔗Links:** [[C++ Session 4 - Conditional and Looping Statements|Next Session 4]]