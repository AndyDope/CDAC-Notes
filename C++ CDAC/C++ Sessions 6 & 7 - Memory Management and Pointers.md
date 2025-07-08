### **Sessions 6 & 7: Memory Management and Pointers**

In these sessions, we will go beyond creating variables that automatically disappear. We will learn to manually control memory, which is essential for building complex, high-performance applications. The key to this control is the **pointer**.

---

#### **1. Introduction to Memory Management (Stack vs. Heap)**

When your program runs, it uses two main areas of memory:

1.  **The Stack:** This is where local variables (like `int x = 10;` inside `main`) are stored. It's very fast and memory is managed **automatically**. When a function ends, all its local variables on the stack are destroyed. It has a limited size.
2.  **The Heap:** This is a large pool of memory available to the programmer for dynamic allocation. Memory on the heap is **not managed automatically**. You must manually request it and, crucially, you must manually release it when you're done. This is where we use pointers.

**Analogy:** The **Stack** is like a small, clean desk for your current task. When you finish the task, you wipe the desk clean. The **Heap** is like a massive warehouse where you can request a storage space of any size. But if you don't tell the manager when you're done with the space, it remains occupied forever.

---

#### **2. Pointers in C++**

A **pointer** is a special variable that does not store a value directly, but instead stores the **memory address** of another variable.

**a) Declaration and Initialization**

*   **Declaration:** You declare a pointer using the asterisk (`*`). `data_type *pointer_name;`
*   **Address-of Operator (`&`):** To get the memory address of a variable, you use the ampersand (`&`). This is different from the [[C++ Session 5 - Functions in C++#3. Call by Reference|call by reference `&`]], but the concept is related (both deal with addresses).
*   **Dereference Operator (`*`):** To access the value *at the address* a pointer is holding, you use the asterisk (`*`) again.

**Example:**
```cpp
int var = 20;            // A normal integer variable

// 1. Declaration
int *ptr;                // 'ptr' is a pointer that can hold the address of an integer

// 2. Initialization (ptr now holds the address of var)
ptr = &var;

cout << "Value of var: " << var << endl;        // Outputs 20
cout << "Address of var: " << &var << endl;      // Outputs a memory address (e.g., 0x7ffc...)
cout << "Value of ptr: " << ptr << endl;        // Outputs the same memory address (0x7ffc...)
cout << "Value at the address ptr points to: " << *ptr << endl; // Outputs 20
```

> **Quick Question:** What are the two distinct uses of the asterisk (`*`) symbol in the context of pointers?
> **Answer:** 1. To declare a pointer variable (e.g., `int *p;`). 2. To dereference a pointer to get the value it points to (e.g., `cout << *p;`).

---

#### **3. Dynamic Memory Allocation: `new` and `delete`**

This is how we manually manage the Heap.

*   **`new` operator:** Allocates memory on the Heap and returns a pointer (the address) to that memory.
*   **`delete` operator:** Frees up the memory on the Heap that was allocated with `new`. If you forget to `delete`, you create a **memory leak**.

**Example:**
```cpp
// Allocate an integer on the heap
int *p_num = new int; 
*p_num = 100; // Assign a value to the allocated memory

cout << "Value is: " << *p_num << endl; // Outputs 100

// VERY IMPORTANT: Free the memory when done
delete p_num; 
p_num = nullptr; // Good practice: point to nothing to avoid errors
```

**Allocating an Array:**
```cpp
int *p_arr = new int[5]; // Allocate an array of 5 integers on the heap
p_arr[0] = 10;
// ...
delete[] p_arr; // Use delete[] with square brackets for arrays!
```

> **Quick Question:** What is the term for when you allocate memory with `new` but forget to free it with `delete`?
> **Answer:** A memory leak.

---

#### **4. Comparison: `new`/`delete` vs. `malloc`/`free`**

You might have heard of `malloc` and `free` from C. C++'s `new` and `delete` are superior for C++ programming.

| Feature               | `new` / `delete` (C++)                                 | `malloc` / `free` (C)                                |
| :-------------------- | :----------------------------------------------------- | :--------------------------------------------------- |
| **Type**              | Operators                                              | Functions (`<cstdlib>`)                              |
| **Type Safety**       | **Type-safe.** `new int` returns `int*`. No casting needed. | **Not type-safe.** `malloc` returns `void*`. Needs casting. |
| **Constructor/Destructor** | **Calls constructor/destructor** for objects.      | Does **not** know about or call constructors/destructors. |
| **Array Allocation**  | `new int[10]` knows the size. `delete[]` is used.      | Must manually calculate size: `malloc(10 * sizeof(int))`. |
| **Overloading**       | Can be overloaded.                                     | Cannot be overloaded.                                |

**Key Takeaway:** In C++, **always prefer `new` and `delete`** over `malloc` and `free`.

---

#### **5. Class Pointers and the `this` Pointer**

**a) Class Pointer and Arrow Operator (`->`)**

You can create objects on the heap using pointers. To access the members (variables or functions) of an object through a pointer, you use the **arrow operator (`->`)** instead of the dot operator (`.`).

```cpp
class Student {
public:
    int rollNo;
    void display() { cout << "Roll No: " << rollNo << endl; }
};

int main() {
    // Create a Student object on the heap
    Student *stud_ptr = new Student();
    
    stud_ptr->rollNo = 101; // Use -> to access members via pointer
    stud_ptr->display();    // Use -> to call methods via pointer

    delete stud_ptr;
    return 0;
}
```

**b) The `this` pointer**

The `this` pointer is a special, implicit pointer that exists **inside every non-static member function of a class**. It points to the **specific object** that called the function. It's primarily used to resolve ambiguity when a parameter has the same name as a member variable.

```cpp
class Employee {
public:
    string name;
    // 'name' is a parameter, also a member variable.
    void setName(string name) {
        // 'this->name' refers to the member variable
        // 'name' refers to the parameter
        this->name = name; 
    }
};
```

> **Quick Question:** If `p` is a pointer to an object, what is the operator used to call one of its methods, `doSomething()`?
> **Answer:** The arrow operator (`->`), as in `p->doSomething();`.

---

#### **6. `enum` and `typedef`**

These are helper tools for writing cleaner, more readable code.

*   **`enum` (Enumeration):** Creates a user-defined type with a set of named integer constants. It makes code more readable than using raw numbers.
    ```cpp
    enum Day { MON, TUE, WED, THU, FRI, SAT, SUN }; // MON=0, TUE=1, etc.
    Day today = WED;
    if (today == WED) { cout << "It's Midweek!"; }
    ```
*   **`typedef`:** Creates an alias or a simpler name for an existing data type. It is useful for simplifying complex type names.
    ```cpp
    typedef unsigned long long int ULLI; // 'ULLI' is now an alias
    ULLI very_large_number = 18446744073709551615ULL;
    ```

---

### **Topic Summary & Revision**

*   **Memory:** **Stack** is for automatic, local variables. **Heap** is for manual, dynamic allocation.
*   **Pointers:** Variables that store memory addresses. Use `&` to get an address and `*` to get the value at an address.
*   **Dynamic Allocation:** Use `new` to allocate on the Heap and `delete` to free it. Use `new[]` and `delete[]` for arrays. Forgetting `delete` causes a **memory leak**.
*   **C++ vs C Memory:** `new`/`delete` are type-safe and call constructors/destructors, making them superior to `malloc`/`free` in C++.
*   **Object Pointers:** Use the arrow operator (`->`) to access members of an object through a pointer.
*   **`this` Pointer:** Inside a member function, `this` points to the object instance that made the call. It's used to resolve name conflicts.

---

### **#MCQs for Exam Preparation**

1.  **Which operator is used to get the memory address of a variable?**
    (A) `*`
    (B) `&`
    (C) `->`
    (D) `.`
    **Answer: (B)**
<br>
2.  **Memory allocated using the `new` operator is stored in:**
    (A) The Stack
    (B) The Heap
    (C) The CPU Registers
    (D) A static variable
    **Answer: (B)**
<br>
3.  **What is the correct way to free an array `p_arr` allocated as `int *p_arr = new int[20];`?**
    (A) `delete p_arr;`
    (B) `delete[] p_arr;`
    (C) `free(p_arr);`
    (D) The memory is freed automatically.
    **Answer: (B)**
<br>
4.  **A key advantage of `new` over `malloc` in C++ is:**
    (A) It is a shorter keyword.
    (B) It does not require a header file.
    (C) It automatically calls constructors for objects.
    (D) It is faster.
    **Answer: (C)**
<br>
5.  **If `student_ptr` is a pointer to a Student object, how do you access its `roll_no` member?**
    (A) `student_ptr.roll_no`
    (B) `*student_ptr.roll_no`
    (C) `&student_ptr->roll_no`
    (D) `student_ptr->roll_no`
    **Answer: (D)**
<br>
6.  **The `this` pointer is available in:**
    (A) All functions in a C++ program.
    (B) The `main` function only.
    (C) Non-static member functions of a class.
    (D) Static member functions of a class.
    **Answer: (C)**
---

### **Bonus Tips**

*   **Viva/Interview Tip:** Be prepared to explain "memory leak," "dangling pointer" (a pointer that points to memory that has already been freed), and "null pointer." A null pointer (`nullptr` in modern C++) is a pointer that is intentionally set to point to nothing.
*   **Exam Tip:** The `new`/`delete` vs `malloc`/`free` comparison is a classic theory question. Memorize the key differences in the table.
*   **Lab Tip:** The most common error in this section is forgetting to use `delete` or using `delete` on a pointer that wasn't allocated with `new`. Another common bug is using `.` when you should be using `->`. Be extra careful with these in your lab assignments.

**🔗Links:** [[C++ Session 8 - OOP Concepts|Next Session 8]]