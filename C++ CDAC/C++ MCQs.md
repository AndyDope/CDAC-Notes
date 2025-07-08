This page contains a comprehensive set of Multiple Choice Questions, organized by topic, to help you prepare for your exams. The questions range from moderate to difficult to test your in-depth understanding.

### **MCQs**

Practice these questions to solidify your understanding of C++ concepts. For best results, attempt to answer them before checking the key.

**🔗 Back to [[C++ Overview]]**

---

### **Topic 1: Getting Started & Beginning with C++ (Sessions 1-3)**

1.  What will be the output of the following C++ code?
    ```cpp
    #include <iostream>
    int main() {
        int a = 5, b = 5;
        int result = ++a * b++;
        std::cout << result << ", " << a << ", " << b;
        return 0;
    }
    ```
   - [ ] 30, 6, 6
   - [ ] 25, 6, 6
   - [ ] 36, 6, 6
   - [ ] The behavior is undefined due to order of evaluation.
<br>
2.  Consider the declarations: `const int *ptr;` and `int * const ptr;`. Which statement is true?
   - [ ] The first declares `ptr` as a constant pointer to an integer. The second declares `ptr` as a pointer to a constant integer.
   - [ ] Both declarations are syntactically incorrect.
   - [ ] The first declares `ptr` as a pointer to a constant integer. The second declares `ptr` as a constant pointer to an integer.
   - [ ] Both declare a constant pointer to a constant integer.
<br>
3.  What is the primary role of a `static` local variable inside a function?
   - [ ] It is accessible by other functions in the same file.
   - [ ] Its memory is allocated on the heap instead of the stack.
   - [ ] It is initialized only once and retains its value across multiple function calls.
   - [ ] It can only be used inside static member functions.
<br>
4.  Which of the following is true about a `const` member function?
- [ ] It can only be called on `const` objects.
- [ ] It can modify non-static data members of the class.
- [ ] It cannot call any other non-const member functions of the class.
- [ ] It must return a `const` value.
<br>
5.  What is the output of the following code snippet, assuming a 64-bit system where pointers are 8 bytes?
    ```cpp
    #include <iostream>
    class Empty {};
    int main() {
        char *str = "hello";
        Empty e;
        std::cout << sizeof(str) << ", " << sizeof(e);
        return 0;
    }
    ```
- [ ] 6, 0
- [ ] 8, 1
- [ ] 6, 1
- [ ] 8, 0
<br>
6.  If `int x = 10;`, `int y = 15;`, what is the value of the expression: `x > y ? x : y`?
- [ ] 10
- [ ] 15
- [ ] 0
- [ ] 1
<br>
7.  A static data member of a class is...
- [ ] Initialized for each object of the class.
- [ ] Initialized when the first object of its class is created.
- [ ] Shared among all objects of its class.
- [ ] Accessible only through `const` member functions.
<br>
8.  In C++, a "token" refers to:
- [ ] A special variable that stores security credentials.
- [ ] The smallest individual unit of a program, like a keyword or an operator.
- [ ] A function that returns an integer code.
- [ ] The return type of the `main` function.

<br>

**Answer Key (Topic 1):**
1.  **D**: The order of evaluation of function arguments is unspecified. The compiler is free to evaluate `result`, `a`, and `b` in any order for the `cout` statement, and the modification of `b` and its use in the multiplication in the same expression can lead to undefined behavior in some contexts, although `result` will be `30`. The key issue is the unspecified evaluation order of arguments.
2.  **C**: Read from right to left. `const int *ptr` (`ptr` is a pointer to an `int` which is `const`). `int * const ptr` (`ptr` is a `const` pointer to an `int`).
3.  **C**: `static` gives a variable static storage duration, meaning it lives for the entire program execution and is initialized only once.
4.  **C**: A `const` member function promises not to change the object's state, so it cannot call a non-`const` function which might change the state.
5.  **B**: `sizeof(str)` gives the size of the pointer variable itself, which is 8 bytes on a 64-bit system. `sizeof` an empty class is non-zero (typically 1 byte) to ensure that two different objects have distinct memory addresses.
6.  **B**: This is the ternary operator. Since `10 > 15` is false, the expression evaluates to the third operand, `y`, which is 15.
7.  **C**: Static members belong to the class, not to any single object, so they are shared.
8.  **B**: This is the definition of a token in a programming language's grammar.

---

### **Topic 2: Control Flow, Functions, and Arrays (Sessions 4-5)**

1.  What is the output of this code?
    ```cpp
    #include <iostream>
    void change(int &x, int y) {
        x = 20;
        y = 20;
    }
    int main() {
        int a = 10, b = 10;
        change(a, b);
        std::cout << a << ", " << b;
        return 0;
    }
    ```
- [ ] 10, 10
- [ ] 20, 10
- [ ] 20, 20
- [ ] 10, 20
<br>
2.  What does the `continue` statement do inside a loop?
- [ ] Exits the loop immediately.
- [ ] Deletes the current value of the loop iterator.
- [ ] Skips the rest of the current iteration and proceeds to the next one.
- [ ] Pauses the loop until a key is pressed.
<br>
3.  Under which circumstance will a C++ compiler most likely ignore a request to make a function `inline`?
- [ ] The function is very short (one line).
- [ ] The function contains a loop or is recursive.
- [ ] The function is declared in a header file.
- [ ] The function returns `void`.
<br>
4.  If an array is declared as `int arr[5];`, what does `arr` represent in an expression like `cout << arr;`?
- [ ] The value of the first element, `arr[0]`.
- [ ] The size of the array in bytes.
- [ ] The memory address of the first element of the array.
- [ ] This will result in a compile-time error.
<br>
5.  What is the output of the following `switch` statement?
    ```cpp
    #include <iostream>
    int main() {
        int i = 2;
        switch (i) {
            case 1: std::cout << "A";
            case 2: std::cout << "B";
            case 3: std::cout << "C"; break;
            default: std::cout << "D";
        }
        return 0;
    }
    ```
- [ ] B
- [ ] BC
- [ ] BCD
- [ ] D
<br>
6.  Which of the following function declarations is a valid example of function overloading for `void func(int x);`?
- [ ] `int func(int y);`
- [ ] `void func(int &x);`
- [ ] `void func(const int x);`
- [ ] `void func(double x);`
<br>
7.  How are command-line arguments `(e.g., ./my_program arg1 arg2)` passed to the `main` function?
- [ ] Through a `std::vector<string>`
- [ ] Through `int argc` (argument count) and `char *argv[]` (argument vector)
- [ ] Through the standard input stream `cin`
- [ ] They are stored in a global array named `ARGS`
<br>
8.  What happens when you pass a 2D array to a function in C++?
- [ ] You only need to specify the number of rows.
- [ ] You only need to specify the number of columns.
- [ ] You must specify both the number of rows and columns.
- [ ] You must specify the number of columns, but the number of rows is optional.

<br>

**Answer Key (Topic 2):**
1.  **B**: `a` is passed by reference, so the change inside the function affects the original variable. `b` is passed by value, so the change is only made to a local copy.
2.  **C**: This is the definition of the `continue` statement's behavior.
3.  **B**: Inlining is a hint. Compilers will likely ignore it for complex functions (with loops, recursion, etc.) because the potential code bloat outweighs the benefit of removing the function call overhead.
4.  **C**: An array's name "decays" into a pointer to its first element in most expression contexts.
5.  **B**: The `switch` statement jumps to `case 2`. Since there is no `break` statement there, it "falls through" to `case 3`, executing its statement and then stopping at the `break`.
6.  **D**: Function overloading requires the function name to be the same but the parameter list to be different in type or number. Changing only the return type (`A`) or the pass-by-value/reference (`B`, `C`) does not constitute a valid overload.
7.  **B**: This is the standard mechanism in C and C++ for handling command-line arguments.
8.  **D**: To calculate the address of an element `arr[i][j]`, the compiler needs to know the size of a row, which is determined by the number of columns. The number of rows is not needed for this calculation.

---

### **Topic 3: Pointers & Memory Management (Sessions 6-7)**

1.  If you allocate memory as `int *arr = new int[10];`, what is the correct way to deallocate it?
- [ ] `delete arr;`
- [ ] `delete arr[10];`
- [ ] `delete [] arr;`
- [ ] The memory is deallocated automatically when `arr` goes out of scope.
<br>
2.  What is the primary difference between memory allocation using `new` in C++ and `malloc()` in C?
- [ ] `new` can only allocate memory for objects, while `malloc()` can only allocate for primitive types.
- [ ] `new` is a function, while `malloc()` is an operator.
- [ ] `new` automatically calls the object's constructor, while `malloc()` does not.
- [ ] `new` allocates memory from the stack, while `malloc()` allocates from the heap.
<br>
3.  What is a "dangling pointer"?
- [ ] A pointer that has not been initialized and points to a random memory location.
- [ ] A pointer that points to a memory location that has already been deallocated (`deleted`).
- [ ] A pointer with the value `NULL` or `nullptr`.
- [ ] A `void*` pointer that has not been cast to a specific type.
<br>
4.  Consider the code: `int x = 10; int *p = &x; int **q = &p;`. How would you access the value of `x` using the pointer `q`?
- [ ] `*q`
- [ ] `&q`
- [ ] `**q`
- [ ] `*q*`
<br>
5.  What is the purpose of the `this` pointer?
- [ ] It points to the next object in an array of objects.
- [ ] It is a global pointer that points to the currently executing function.
- [ ] It is a pointer to the base class object within a derived class.
- [ ] It is a keyword that refers to the specific object instance on which a member function is called.
<br>
6.  Executing `delete this;` inside a class member function is...
- [ ] Always safe and a standard practice for self-destruction.
- [ ] A compile-time error.
- [ ] Legal, but extremely dangerous and should only be done if the object was allocated on the heap and you know exactly what you are doing.
- [ ] The only correct way to call an object's destructor.
<br>
7.  What is the most likely outcome of the following code?
    ```cpp
    void func() {
        int* ptr = new int(5);
    } // func ends here
    ```
- [ ] A segmentation fault.
- [ ] A compile-time error.
- [ ] A memory leak.
- [ ] The integer 5 is successfully deallocated.
<br>
8.  Pointer arithmetic in C++ is scaled by what?
- [ ] The size of an `int`.
- [ ] The size of a `char`.
- [ ] The size of the data type the pointer points to.
- [ ] It is always scaled by 1 byte.

<br>

**Answer Key (Topic 3):**
1.  **C**: When allocating an array with `new[]`, you must use `delete[]` to ensure the destructors for all elements are called (if applicable) and the entire block of memory is freed correctly. Using `delete` is undefined behavior.
2.  **C**: This is the key difference. `new` is type-aware and part of the object creation lifecycle, while `malloc` is just a raw memory allocator.
3.  **B**: This is the definition of a dangling pointer. Accessing it leads to undefined behavior.
4.  **C**: `q` points to `p`. `*q` dereferences `q` to get `p`. `**q` dereferences `p` to get the value of `x`.
5.  **D**: The `this` pointer provides a way for member functions to access the object's own data members and address.
6.  **C**: It's legal syntax, but after `delete this;`, the object's memory is deallocated. Accessing any member (including finishing the current function) is undefined behavior. It's a very advanced and risky technique.
7.  **C**: The memory for the integer is allocated on the heap, but the pointer `ptr` which holds its address is a local variable. When `func` ends, `ptr` is destroyed, and the address is lost, making it impossible to `delete` the allocated memory.
8.  **C**: If `p` is an `int*`, `p + 1` moves the pointer forward by `sizeof(int)` bytes.

---

### **Topic 4: OOP, Constructors & Destructors (Sessions 8-9)**

1.  If a class has a user-defined destructor, what other special member function should you almost always define, according to the "Rule of Three"?
- [ ] A default constructor.
- [ ] A static member function.
- [ ] A copy constructor and a copy assignment operator.
- [ ] A friend function.
<br>
2.  What is the order of constructor and destructor calls for the following code?
    ```cpp
    class MyClass { /*...*/ };
    int main() {
        MyClass obj1;
        MyClass obj2;
        return 0;
    }
    ```
- [ ] obj1-ctor, obj2-ctor, obj1-dtor, obj2-dtor
- [ ] obj1-ctor, obj2-ctor, obj2-dtor, obj1-dtor
- [ ] obj1-ctor, obj1-dtor, obj2-ctor, obj2-dtor
- [ ] The order is not guaranteed.
<br>
3.  What is the purpose of the `explicit` keyword when applied to a constructor?
- [ ] It prevents the compiler from automatically generating a default constructor.
- [ ] It makes the constructor private.
- [ ] It prevents the compiler from using the constructor for implicit type conversions.
- [ ] It ensures the constructor is inlined.
<br>
4.  If a class `MyClass` contains a pointer data member that is allocated with `new` in the constructor, what is the problem with the compiler-generated copy constructor?
- [ ] It will fail to compile.
- [ ] It will perform a "deep copy," which is inefficient.
- [ ] It will perform a "shallow copy," leading to two objects pointing to the same memory, causing issues like double-free.
- [ ] It will not copy the pointer member at all.
<br>
5.  In an inheritance hierarchy `class Derived : public Base`, what is the order of constructor execution when a `Derived` object is created?
- [ ] Derived constructor first, then Base constructor.
- [ ] Base constructor first, then Derived constructor.
- [ ] Only the Derived constructor is called.
- [ ] The order depends on the compiler.
<br>
6.  Which of the following is NOT a fundamental concept of Object-Oriented Programming?
- [ ] Encapsulation
- [ ] Inheritance
- [ ] Polymorphism
- [ ] Compilation
<br>
7.  When is a copy constructor called?
- [ ] When an object is passed by reference to a function.
- [ ] When an object is created using the `new` operator.
- [ ] When a new object is initialized from an existing object of the same type.
- [ ] When an object is assigned a new value using the `=` operator.
<br>
8.  What is true about a destructor?
- [ ] It can have parameters.
- [ ] It can be overloaded.
- [ ] It is called automatically when an object goes out of scope or is `deleted`.
- [ ] It must be declared `public`.

<br>

**Answer Key (Topic 4):**
1.  **C**: The "Rule of Three" (or Five/Zero in modern C++) states that if a class needs a user-defined destructor, copy constructor, or copy assignment operator, it likely needs all three because it's managing a resource.
2.  **B**: Objects are constructed in the order they are declared. They are destructed in the reverse order of construction (stack-like LIFO behavior).
3.  **C**: `explicit` prevents single-argument constructors from being used as conversion functions, which can avoid subtle bugs.
4.  **C**: The default copy constructor just copies member values bit by bit. For a pointer, this means only the address is copied (shallow copy), not the data it points to.
5.  **B**: The base class part of an object must be constructed before the derived class part can be constructed.
6.  **D**: Compilation is a necessary step in programming, but not a conceptual pillar of OOP.
7.  **C**: This is the primary trigger for the copy constructor. Assignment (`=`) on an *already existing* object calls the copy assignment operator, not the copy constructor.
8.  **C**: This is the fundamental purpose of a destructor. It cannot have parameters, cannot be overloaded, and while usually public, can be protected or private in certain design patterns.

---

### **Topic 5: Inheritance & Polymorphism (Sessions 10-11)**

1.  What is function "hiding" (or name hiding) in C++?
- [ ] A technique to make a function's implementation private.
- [ ] When a derived class function has the same name as a base class function but a different signature, it hides all base class functions with that name.
- [ ] Another term for function overloading.
- [ ] When a `friend` function is used to access private members.
<br>
2.  To resolve ambiguity when a class inherits from two base classes that both have a function named `foo()`, you would use:
- [ ] A `virtual` specifier.
- [ ] A `dynamic_cast`.
- [ ] The Scope Resolution Operator (e.g., `Base1::foo()`).
- [ ] A `friend` declaration.
<br>
3.  If a `friend` function is declared in class `A`, which statement is true?
- [ ] The function is a member of class `A`.
- [ ] The function can access `private` and `protected` members of class `A` objects.
- [ ] Only other `friend` functions can call it.
- [ ] The function is automatically inherited by classes derived from `A`.
<br>
4.  Which two operators cannot be overloaded in C++?
- [ ] `&&` and `||`
- [ ] `()` and `[]`
- [ ] `.` (Member Access) and `::` (Scope Resolution)
- [ ] `new` and `delete`
<br>
5.  What problem does a `virtual` base class solve?
- [ ] It prevents a class from being inherited.
- [ ] It allows a derived class to access private members of its base class.
- [ ] It resolves the "diamond problem" by ensuring only one copy of the grandparent base class exists in the object layout.
- [ ] It enables run-time polymorphism.
<br>
6.  In `class Derived : private Base`, what is the accessibility of `public` members of `Base` from within `Derived` and from an object of `Derived`?
- [ ] `public` within Derived, `public` from an object.
- [ ] `private` within Derived, inaccessible from an object.
- [ ] `public` within Derived, inaccessible from an object.
- [ ] `private` within Derived, `private` from an object (inaccessible).
<br>
7.  Which of the following demonstrates compile-time (static) polymorphism?
- [ ] Virtual functions.
- [ ] Function overloading and operator overloading.
- [ ] Abstract classes.
- [ ] The `dynamic_cast` operator.
<br>
8.  Can a constructor be declared as a `friend` of another class?
- [ ] No, constructors cannot be friends.
- [ ] Yes, but it has no practical effect.
- [ ] Yes, this is a common pattern for controlling object creation.
- [ ] Only if the constructor is `private`.

<br>

**Answer Key (Topic 5):**
1.  **B**: This is a common pitfall. Once a name is defined in a derived class, the compiler stops looking for that name in the base class scope unless explicitly told to.
2.  **C**: The scope resolution operator is used to specify exactly which base class's version of the function you intend to call.
3.  **B**: This is the definition of a `friend` function. It's a non-member function given special access privileges.
4.  **C**: These operators are fundamental to the language's structure and their meaning cannot be changed.
5.  **C**: By inheriting virtually, any class that inherits from the virtual base will share a single subobject of that base.
6.  **B**: With `private` inheritance, all `public` and `protected` members of the base class become `private` members of the derived class. They are accessible within `Derived` but not from outside.
7.  **B**: Overloading is resolved at compile-time based on the function signature, hence it's static polymorphism.
8.  **A**: Friendship is granted to functions and classes, not to specific member functions like constructors or destructors.

---

### **Topic 6: Virtual Functions & Abstract Classes (Session 12)**

1.  What is the main purpose of a `virtual` destructor?
- [ ] To prevent the class from being instantiated.
- [ ] To ensure that the correct destructor is called when deleting a derived class object through a base class pointer.
- [ ] To allow the destructor to be overloaded.
- [ ] To make the class an abstract base class.
<br>
2.  What is the output of this program?
    ```cpp
    #include <iostream>
    class Base { public: virtual void show() { std::cout << "Base "; } };
    class Derived : public Base { public: void show() { std::cout << "Derived "; } };
    int main() {
        Base* bp = new Derived();
        bp->show();
        delete bp;
        return 0;
    }
    ```
- [ ] Base
- [ ] Derived
- [ ] A compile-time error.
- [ ] The output is undefined.
<br>
3.  A class is made abstract by...
- [ ] Declaring its constructor as `private`.
- [ ] Not providing a definition for any of its member functions.
- [ ] Inheriting from an abstract class.
- [ ] Including at least one pure virtual function (`= 0`).
<br>
4.  What is a VTABLE?
- [ ] A table of variables used by the compiler for optimization.
- [ ] A look-up table used at runtime to resolve virtual function calls.
- [ ] A table that stores the `sizeof` every class in the program.
- [ ] A security feature to prevent virtual memory exploits.
<br>
5.  If `class Derived : public Base {}` and `Base` is an abstract class, but `Derived` does not provide an implementation for all of `Base`'s pure virtual functions, then...
- [ ] The program will not compile.
- [ ] `Derived` will also be an abstract class.
- [ ] A runtime error will occur when creating a `Derived` object.
- [ ] The `Base` class implementations will be used by default.
<br>
6.  Why can't constructors be `virtual`?
- [ ] Because they are automatically `inline`.
- [ ] Because a `virtual` call is resolved using a pointer within an object, but the object is not fully constructed until the constructor has finished running.
- [ ] It's a purely arbitrary language rule with no technical reason.
- [ ] Because constructors cannot be inherited.
<br>
7.  Which cast should be used to safely convert a base class pointer to a derived class pointer?
- [ ] `static_cast`
- [ ] `reinterpret_cast`
- [ ] `const_cast`
- [ ] `dynamic_cast`
<br>
8.  An abstract class can have:
- [ ] Objects of its own type.
- [ ] Pointers and references to its own type.
- [ ] Only static member functions.
- [ ] No data members.

<br>

**Answer Key (Topic 6):**
1.  **B**: If the destructor is not virtual, deleting through a base pointer will only call the base destructor, leading to a resource leak if the derived class has its own resources.
2.  **B**: Because `show()` is `virtual`, the call `bp->show()` is resolved at runtime. Since `bp` points to a `Derived` object, `Derived::show()` is called. This is the essence of runtime polymorphism.
3.  **D**: This is the definition of an abstract base class (ABC) in C++.
4.  **B**: A class with virtual functions has a hidden pointer (vptr) to a VTABLE. The VTABLE contains addresses of the virtual functions for that class, enabling dynamic dispatch.
5.  **B**: A derived class must implement ALL inherited pure virtual functions to become a concrete (instantiable) class. If it doesn't, it remains abstract.
6.  **B**: At the time of construction, the virtual mechanism (vptr and VTABLE) is not yet set up for the object being created. The compiler must know the exact type to call the correct constructor.
7.  **D**: `dynamic_cast` performs a runtime check to ensure the conversion is valid. If it's not, it returns `nullptr` for pointers, making it the "safe" downcast.
8.  **B**: You cannot create an object of an abstract class (`Abstract obj;`), but you can create pointers (`Abstract* ptr;`) and references (`Abstract& ref;`) which can then point/refer to objects of concrete derived classes.

---

### **Topic 7: Exception & File Handling (Sessions 13-15)**

1.  What is "stack unwinding" in the context of C++ exceptions?
- [ ] A process where the compiler optimizes the function call stack.
- [ ] When an exception is thrown, the process of calling destructors for all automatic objects that have been created on the stack between the `try` block and the `throw` statement.
- [ ] A runtime error caused by infinite recursion.
- [ ] The process of catching an exception in the `main` function.
<br>
2.  What happens if an exception is thrown from a constructor?
- [ ] The program terminates immediately.
- [ ] The object's memory is leaked because the destructor is never called.
- [ ] The C++ runtime guarantees that the destructor for the object is called.
- [ ] The memory allocated for the object is automatically reclaimed, and its destructor is *not* called because the object was never fully constructed.
<br>
3.  What does opening a file with `ofstream myFile("data.txt", ios::app);` do?
- [ ] It opens the file for reading and writing at the same time.
- [ ] It truncates (clears) the file if it exists.
- [ ] It opens the file and positions the write pointer at the end, so any new writes are appended.
- [ ] It opens the file in binary mode.
<br>
4.  What is the purpose of the `catch(...)` block?
- [ ] It catches only exceptions of type `int`.
- [ ] It is a syntax error.
- [ ] It is a "catch-all" handler that catches any type of exception.
- [ ] It catches only standard library exceptions.
<br>
5.  How can you check if an `ifstream` object named `inFile` failed to open a file?
- [ ] `if (inFile == NULL)`
- [ ] `if (!inFile.is_open())` or `if (!inFile)`
- [ ] `if (inFile.has_failed())`
- [ ] You must use a `try`/`catch` block, as it throws an exception on failure.
<br>
6.  The RAII (Resource Acquisition Is Initialization) idiom helps write exception-safe code by:
- [ ] Acquiring resources in a global function and initializing them in `main`.
- [ ] Tying the lifetime of a resource (like a file handle or memory) to the lifetime of an object, so the resource is released when the object's destructor is called (even during stack unwinding).
- [ ] Using `goto` statements to handle cleanup code.
- [ ] Prohibiting dynamic memory allocation.
<br>
7.  What is the difference between opening a file with `ios::app` vs `ios::ate`?
- [ ] There is no difference; they are aliases.
- [ ] `app` positions the pointer at the end for all writes, while `ate` only positions the pointer at the end upon opening (it can be moved afterwards).
- [ ] `app` is for text files, `ate` is for binary files.
- [ ] `app` creates the file if it doesn't exist, `ate` does not.
<br>
8.  Re-throwing the currently handled exception inside a `catch` block is done using the statement:
- [ ] `throw e;` where `e` is the exception object caught.
- [ ] `rethrow;`
- [ ] `throw;`
- [ ] `catch(throw);`

<br>

**Answer Key (Topic 7):**
1.  **B**: This is a crucial feature for RAII and ensures that resources are properly cleaned up when an exception interrupts the normal flow of control.
2.  **D**: A fundamental rule of C++ exceptions: a destructor is only called for a fully constructed object. If the constructor fails, the object is not considered fully constructed.
3.  **C**: `ios::app` stands for "append mode."
4.  **C**: The ellipsis `(...)` is the syntax for a catch block that will handle an exception of any type.
5.  **B**: Both `!inFile.is_open()` and the more idiomatic `!inFile` (which checks the stream's state) are correct ways to test for file opening success.
6.  **B**: This is the definition of RAII. Smart pointers like `std::unique_ptr` and file stream objects are prime examples.
7.  **B**: This is the key difference. `ios::app` forces every single write operation to happen at the end of the file. `ios::ate` ("at end") simply starts you at the end, but you are free to seek to other positions.
8.  **C**: The simple `throw;` statement (with no expression) re-throws the original exception object, preserving its polymorphic type. `throw e;` might "slice" the exception if `e` was caught by value.

---

### **Topic 8: Templates, STL, & RTTI (Sessions 16-18)**

1.  Why must template definitions (implementations) usually be placed in header files?
- [ ] It is a stylistic convention only.
- [ ] To allow templates to access private members of other classes.
- [ ] Because the compiler needs the full template definition to be visible in any translation unit that uses it, in order to instantiate the template for a specific type.
- [ ] It makes compilation faster.
<br>
2.  What is "iterator invalidation"?
- [ ] A runtime error when an iterator goes past the end of a container.
- [ ] When an operation on a container (like inserting an element into a `std::vector`) makes some or all of its existing iterators unusable.
- [ ] A compile-time error when an iterator type does not match its container type.
- [ ] When an iterator is used with a generic algorithm that doesn't support it.
<br>
3.  Which STL container is the best choice if you need fast look-up by a unique key and also require the elements to be stored in a sorted order?
- [ ] `std::vector`
- [ ] `std::unordered_map`
- [ ] `std::list`
- [ ] `std::map`
<br>
4.  What is template specialization?
- [ ] Creating a template that only works for a specific set of types.
- [ ] The process of the compiler generating code from a template.
- [ ] Providing a separate, specific implementation of a template for a particular type that should behave differently from the generic version.
- [ ] Using a template as a base class.
<br>
5.  What is the purpose of `dynamic_cast` in RTTI?
- [ ] To cast away the `const`-ness of an object.
- [ ] To safely perform a downcast (from a base class pointer to a derived class pointer) by checking the object's actual type at runtime.
- [ ] To perform any type of pointer conversion without compile-time checks.
- [ ] To get the `type_info` object for a class.
<br>
6.  Which of the following operations is most likely to be significantly slower on a `std::vector` than on a `std::list` for a large number of elements?
- [ ] Accessing the element at a random index (e.g., `my_container[N/2]`).
- [ ] Adding an element to the very end (`push_back`).
- [ ] Inserting a new element at the very beginning.
- [ ] Getting the total number of elements (`.size()`).
<br>
7.  To use the `typeid` operator on a polymorphic type (a class with at least one virtual function) and get its *dynamic* type, what must be true?
- [ ] The class must have a public default constructor.
- [ ] RTTI must be explicitly enabled via a `#pragma` directive.
- [ ] The `typeid` operator must be applied to a pointer to the object.
- [ ] The expression given to `typeid` must be a dereferenced pointer or a reference to an object.
<br>
8.  Which container would you use to implement a print job queue where jobs are processed in the order they are received?
- [ ] `std::stack`
- [ ] `std::queue`
- [ ] `std::priority_queue`
- [ ] `std::vector`

<br>

**Answer Key (Topic 8):**
1.  **C**: This is a fundamental concept of C++'s compilation model. The compiler instantiates templates on-demand and needs the full source code (not just the declaration) to do so.
2.  **B**: For example, adding an element to a `std::vector` might cause it to reallocate its entire internal array, making all previous iterators point to freed memory.
3.  **D**: `std::map` provides both key-based look-up and sorted order. `std::unordered_map` is faster for look-up but does not maintain order.
4.  **C**: This is the definition of explicit template specialization. It's an override for the generic template.
5.  **B**: This is the primary use case for `dynamic_cast`. It's the "safe" way to downcast in a polymorphic hierarchy.
6.  **C**: Inserting at the beginning of a `vector` requires shifting all existing elements, which is a slow `O(n)` operation. For a `std::list`, it's a fast `O(1)` operation.
7.  **D**: `typeid` on a pointer itself will just tell you it's a pointer. To get the runtime type of the *object*, you must apply `typeid` to the dereferenced pointer (`*ptr`) or a reference.
8.  **B**: A queue is the perfect data structure for a First-In, First-Out (FIFO) process like a print queue.