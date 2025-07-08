### **Session 11: Polymorphism**

Welcome to Session 11. We will now explore **Polymorphism**, a Greek term meaning "many forms." It is one of the core [[C++ Session 8 - OOP Concepts#3. The Pillars of OOP|pillars of OOP]] and allows us to perform a single action in different ways. In C++, polymorphism lets us create flexible, reusable, and intuitive code, especially when dealing with class hierarchies.

---

#### **1. Types of Polymorphism**

Polymorphism in C++ is broadly divided into two types, based on *when* the decision is made to call a specific function.

*   **1. Compile-time Polymorphism (Static Binding):**
    *   The function call is resolved by the compiler at compile time. It's called "static" because the decision is fixed before the program runs.
    *   This is achieved through:
        *   **Function Overloading**
        *   **Operator Overloading**

*   **2. Run-time Polymorphism (Dynamic Binding):**
    *   The function to be called is decided at run time, based on the type of the object being pointed to.
    *   This is achieved through:
        *   **Virtual Functions** (This is the primary topic of [[C++ Session 12 - Virtual Functions and Abstract Class|Virtual Functions and Abstract Class]]).

**Analogy:**
*   **Compile-time:** You tell your friend, "Call me on my mobile." The number is known and fixed before the call is made.
*   **Run-time:** You call a company's helpline. The call is routed to the "next available agent." You don't know *which* specific agent you'll talk to until the call is actually connected.

> **Quick Question:** If the compiler determines exactly which function to call before the program is run, what type of polymorphism is this?
> **Answer:** Compile-time polymorphism.

---

#### **2. Function Overloading**

We've seen this concept before with [[C++ Session 9 - Constructors and Destructor|constructor overloading]]. Function overloading allows you to define two or more functions with the **same name** but with **different parameters**. The parameters can differ in:
*   Number of arguments.
*   Type of arguments.
*   Order of arguments.

**Important:** Overloading is **NOT** based on the function's return type.

**Example:**
```cpp
// A function to add two integers
int add(int a, int b) {
    return a + b;
}

// An overloaded function to add two doubles
double add(double a, double b) {
    return a + b;
}

int main() {
    cout << add(5, 10) << endl;      // Calls the integer version
    cout << add(3.5, 7.2) << endl;   // Calls the double version
    return 0;
}
```

> **Quick Question:** Can you have two functions `int getVal()` and `double getVal()` in the same scope? Why or why not?
> **Answer:** No, because function overloading cannot be based on the return type alone. The compiler wouldn't know which one to call.

---

#### **3. Operator Overloading**

Operator overloading allows you to give special meaning to existing operators for your user-defined types (classes). This makes objects of your classes behave more intuitively, just like built-in types.

**Analogy:** The `+` operator knows how to add two integers (`5 + 2`). Operator overloading is like *teaching* the `+` operator how to add two `ComplexNumber` objects or two `Matrix` objects.

**Syntax:** `return_type operator_symbol(parameters);`

**Example: Overloading `+` for a `Complex` class**
```cpp
class Complex {
public:
    int real, imag;
    Complex(int r = 0, int i = 0) { real = r; imag = i; }

    // Overloading the '+' operator as a member function
    Complex operator+(const Complex &obj) {
        Complex result;
        result.real = this->real + obj.real;
        result.imag = this->imag + obj.imag;
        return result;
    }
};

int main() {
    Complex c1(10, 5);
    Complex c2(2, 4);
    Complex c3 = c1 + c2; // This now works! Calls the overloaded operator+
    cout << c3.real << " + i" << c3.imag << endl; // 12 + i9
    return 0;
}
```
**Note:** Some operators cannot be overloaded, like `.` (member access), `::` (scope resolution), `sizeof`, and `?:` (ternary operator).

> **Quick Question:** To allow the expression `obj1 * obj2` for objects of your class, what function would you need to define?
> **Answer:** `operator*`.

---

#### **4. Friend Functions**

A `friend` function of a class is a function that is **not a member** of the class but is given permission to access the class's `private` and `protected` members.

**Why use it?** Sometimes a function needs to operate on two different objects, and making it a member of one class feels unnatural. Operator overloading is a classic use case. For example, `Complex c3 = c1 + c2;` could also be implemented with a friend function.

**Syntax:**
1.  **Declare** the function prototype inside the class, prefixed with the `friend` keyword.
2.  **Define** the function outside the class, without the `friend` keyword or the `ClassName::` scope.

**Example: `operator+` as a friend function**
```cpp
class Complex {
private:
    int real, imag;
public:
    Complex(int r=0, int i=0) { real = r; imag = i; }
    // Friend function declaration
    friend Complex operator+(const Complex &c1, const Complex &c2);
    void display() { cout << real << " + i" << imag; }
};

// Definition of the friend function
Complex operator+(const Complex &c1, const Complex &c2) {
    // It can access private members of c1 and c2
    return Complex(c1.real + c2.real, c1.imag + c2.imag);
}
```

> **Quick Question:** Does a friend function have the `this` pointer?
> **Answer:** No, because it is not a member of the class. The [[C++ Sessions 6 & 7 - Memory Management and Pointers#**5. Class Pointers and the `this` Pointer**|'this' pointer]] only exists in non-static member functions.

---

#### **5. Constant Functions (`const` Member Functions)**

A `const` member function is a function that guarantees it will not modify any member variables of the object. It treats the object as read-only.

**Why use it?**
*   **Safety:** It prevents accidental modification of data by "getter" or display functions.
*   **Flexibility:** It is the only way to call a member function on a `const` object.

**Syntax:** The `const` keyword is placed after the parameter list.
`return_type functionName(parameters) const;`

**Example:**
```cpp
class Account {
    double balance;
public:
    Account(double b) : balance(b) {}
    
    // This function PROMISES not to change 'balance'
    double getBalance() const {
        // balance = 0; // COMPILE ERROR! Cannot modify member in a const function.
        return balance;
    }
};

int main() {
    const Account acc(5000.0); // A constant, read-only account
    cout << "Balance is: " << acc.getBalance(); // This is allowed
    // acc.deposit(100); // This would be an error if deposit() is not const
    return 0;
}
```

---

### **Topic Summary & Revision**

*   **Polymorphism:** "One name, many forms." It has two types: compile-time and run-time.
*   **Compile-time Polymorphism:** Resolved at compile time.
    *   **Function Overloading:** Same function name, different parameters. Not based on return type.
    *   **Operator Overloading:** Giving special meaning to operators for user-defined types.
*   **Friend Function:** A non-member function granted access to a class's `private`/`protected` members.
*   **`const` Member Function:** A member function that cannot modify the object's state. It is declared with `const` at the end.

---

### **#MCQs for Exam Preparation**

1.  **Function overloading is an example of:**
    (A) Run-time polymorphism
    (B) Inheritance
    (C) Compile-time polymorphism
    (D) Encapsulation
    **Answer: (C)**
<br>
2.  **Which of the following operators cannot be overloaded?**
    (A) `+`
    (B) `[]`
    (C) `::`
    (D) `++`
    **Answer: (C)** (The scope resolution operator).
<br>
3.  **A `friend` function of a class can access:**
    (A) Only public members of the class.
    (B) Public and protected members of the class.
    (C) Public, protected, and private members of the class.
    (D) Only members of its own class.
    **Answer: (C)**
<br>
4.  **What does the `const` keyword at the end of a member function declaration signify? `void display() const;`**
    (A) The function returns a constant value.
    (B) The function can only be called once.
    (C) The function cannot modify any member variables of the object.
    (D) The function must be defined inline.
    **Answer: (C)**
<br>
5.  **Which of the following is a valid C++ function overload for `void func(int a, double b);`?**
    (A) `int func(int a, double b);`
    (B) `void func(int x, double y);`
    (C) `void func(double a, int b);`
    (D) `void func(int a, double b) const;`
    **Answer: (C)** (The order of parameter types is different. A and B have the same signature, and D just adds a const qualifier which is part of overloading but C is a clearer example of type difference).

---

### **Bonus Tips**

*   **Viva/Interview Tip:** A common question is "When should an overloaded operator be a member function vs. a friend function?" A good rule of thumb: If the operator needs to modify the state of the left-hand object (like `+=`, `++`), make it a member function. If it needs to treat both operands symmetrically (like `+`, `*`) or if the left-hand operand is not a class object (like `cout << myObject`), make it a friend function.
*   **Exam Tip:** Remember the list of operators that *cannot* be overloaded (`::`, `.`, `.*`, `sizeof`, `?:`). This is a very common MCQ or short-answer question.
*   **Lab Tip:** For your lab assignment ("Assignments to overload =, \==, +, ++, --, <<, >> and [ ]operators"), the `<<` and `>>` operators for `cout` and `cin` are almost always implemented as **friend functions**. The syntax is `friend ostream& operator<<(ostream &out, const MyClass &obj);`.

**🔗Links:** [[C++ Session 12 - Virtual Functions and Abstract Class|Session 12]]