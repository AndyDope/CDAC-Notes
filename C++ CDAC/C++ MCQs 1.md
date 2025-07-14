### **Comprehensive MCQ Review: C++**

Practice these questions to solidify your understanding of C++ concepts. For best results, attempt to answer them before checking the key.

**🔗 Back to [[C++ Overview]]**

---

### **Topic 1: C++ Fundamentals (Sessions 1-5)**

1.  **What is the output of the following C++ code?**
    ```cpp
    #include <iostream>
    int main() {
        int a = 5, b = 10;
        int result = a++ * --b;
        std::cout << result << ", " << a << ", " << b;
        return 0;
    }
    ```
    - [ ] 50, 6, 9
    - [ ] 45, 6, 9
    - [ ] 54, 6, 9
    - [ ] The behavior is undefined due to order of evaluation.
    <br>

2.  **A function is declared as `void process(int &data)`. How is the argument passed to this function?**
    - [ ] By value
    - [ ] By pointer
    - [ ] By reference
    - [ ] By constant reference
    <br>

3.  **What is the default access specifier for members of a `class` in C++?**
    - [ ] `public`
    - [ ] `protected`
    - [ ] `private`
    - [ ] It depends on the compiler.
    <br>

4.  **Consider the declaration `const int *ptr;`. Which statement is true?**
    - [ ] `ptr` is a constant pointer.
    - [ ] `ptr` is a pointer to a constant integer.
    - [ ] `ptr` is a constant pointer to a constant integer.
    - [ ] The declaration is invalid.
    <br>

5.  **What is the purpose of an `inline` function?**
    - [ ] To force the function to be executed on a separate thread.
    - [ ] To request the compiler to replace the function call with the function's code, potentially reducing function-call overhead.
    - [ ] To make the function accessible from other files.
    - [ ] To ensure the function can only be called once.
    <br>

6.  **What is the output of this code snippet?**
    ```cpp
    #include <iostream>
    int main() {
        int arr[5] = {1, 2, 3, 4, 5};
        std::cout << *(arr + 3);
        return 0;
    }
    ```
    - [ ] 3
    - [ ] 4
    - [ ] The address of the 3rd element.
    - [ ] Compilation error.
    <br>

7.  **In a `switch` statement, what happens if a `case` does not end with a `break` statement?**
    - [ ] It causes a compilation error.
    - [ ] Execution "falls through" to the next `case` block.
    - [ ] The `switch` statement terminates immediately.
    - [ ] Only the `default` block is executed.
    <br>

8.  **A static local variable declared inside a function:**
    - [ ] Is re-initialized every time the function is called.
    - [ ] Is only accessible within that function but retains its value between calls.
    - [ ] Is allocated on the heap.
    - [ ] Must be a constant.
    <br>

9.  **Which header file is required for using `cout` and `cin`?**
    - [ ] `<stdio.h>`
    - [ ] `<conio.h>`
    - [ ] `<string>`
    - [ ] `<iostream>`
    <br>

10. **What is the size of an empty class object in C++?**
    - [ ] 0 bytes
    - [ ] 1 byte (typically)
    - [ ] 4 bytes
    - [ ] It depends on whether it has a virtual function.
    <br>

**Answer Key (Topic 1)**
1.  **D**: ||While the calculation of `result` itself (`5 \* 9 = 45`) is well-defined, the order in which the arguments to `std::cout` are evaluated is unspecified by the C++ standard. This means a compiler could evaluate `a` before `result`, leading to different printed outputs.||
2.  **C**: ||The `&` symbol in a function parameter declaration indicates that the argument is passed by reference, meaning the function can modify the original variable.||
3.  **C**: ||By default, all members (data and functions) of a `class` are `private`. For a `struct`, they are `public`.||
4.  **B**: ||Reading from right to left, `ptr` is a pointer (`*`) to an `int` that is `const`. This means you cannot change the value of the integer `*ptr` points to, but you can change the pointer `ptr` itself to point to another integer.||
5.  **B**: ||An `inline` function is a hint to the compiler to perform inline expansion. This avoids the overhead of a function call (like pushing arguments to the stack) and can result in faster code for small functions.||
6.  **B**: ||In C++, pointer arithmetic on an array `arr + 3` calculates the memory address of the element at index 3. The dereference operator `*` then retrieves the value at that address, which is 4.||
7.  **B**: ||Without a `break`, the control flow continues into the next `case` block's statements until a `break` is encountered or the `switch` block ends. This is known as fall-through.||
8.  **B**: ||The `static` keyword gives a local variable static storage duration, meaning it is initialized only once (the first time the function is called) and its value persists across subsequent calls. Its scope, however, remains limited to the function.||
9.  **D**: ||`<iostream>` is the standard header for input/output stream objects like `std::cin` and `std::cout`.||
10. **B**: ||To ensure that two different objects of the same empty class have distinct memory addresses, the C++ standard mandates that they have a non-zero size, which is typically 1 byte.||

---

### **Topic 2: Core OOP Concepts (Sessions 6-9)**

11. **What is the `this` pointer in C++?**
    - [ ] A pointer to the base class of the current object.
    - [ ] A pointer to the current object instance itself, available inside its non-static member functions.
    - [ ] A pointer to a static data member.
    - [ ] A pointer to the function that called the current method.
    <br>

12. **If you define a class with a constructor `MyClass(int x)`, but no other constructors, what happens when you try to do `MyClass obj;`?**
    - [ ] The code compiles, and a default constructor is used.
    - [ ] The code fails to compile because no matching constructor is found.
    - [ ] A runtime error occurs.
    - [ ] The object `obj` is created but its members are uninitialized.
    <br>

13. **Which operator is used to deallocate memory for a single object allocated with `new`?**
    - [ ] `free()`
    - [ ] `delete[]`
    - [ ] `delete`
    - [ ] `remove`
    <br>

14. **When is a class's destructor automatically called?**
    - [ ] When the object is created.
    - [ ] When the object's data members are modified.
    - [ ] When the object goes out of scope or is explicitly deleted.
    - [ ] It must always be called manually.
    <br>

15. **A copy constructor is typically invoked in which of the following scenarios?**
    - [ ] When a new object is created from scratch.
    - [ ] When an object is passed by reference to a function.
    - [ ] When an object is passed by value to a function.
    - [ ] When a static object is created.
    <br>

16. **A function is declared as `friend class MyClass;`. What does this mean?**
    - [ ] `MyClass` is a friend of the function.
    - [ ] The function is a `friend` of `MyClass` and can access its `private` and `protected` members.
    - [ ] The function can only be called by `MyClass`.
    - [ ] The declaration is syntactically incorrect.
    <br>

17. **What is the correct way to deallocate an array of 10 integers allocated as `int *p = new int[10];`?**
    - [ ] `delete p;`
    - [ ] `delete p[10];`
    - [ ] `delete[] p;`
    - [ ] `free(p);`
    <br>

18. **The primary purpose of a constructor is to:**
    - [ ] Deallocate memory for an object.
    - [ ] Copy one object to another.
    - [ ] Initialize the data members of an object when it is created.
    - [ ] Return a value to the calling function.
    <br>

19. **If `obj` is an object and `memberFunc()` is a member function, `obj.memberFunc()` is internally converted by the compiler to something like:**
    - [ ] `memberFunc(obj)`
    - [ ] `memberFunc(&obj)`
    - [ ] `obj->memberFunc()`
    - [ ] `memberFunc(obj*)`
    <br>

20. **To call one constructor from another within the same class (constructor delegation), you use:**
    - [ ] The `this()` keyword in the function body.
    - [ ] The member initializer list.
    - [ ] The `super()` keyword.
    - [ ] A `goto` statement.
    <br>

**Answer Key (Topic 2)**
11. **B**: ||The `this` pointer holds the memory address of the object on which the member function was called. It is implicitly passed as an argument to all non-static member functions.||
12. **B**: ||Once you provide any user-defined constructor, the compiler no longer generates a default (no-argument) constructor. The line `MyClass obj;` requires a no-argument constructor, which doesn't exist, so compilation fails.||
13. **C**: ||The `delete` operator is used to free the memory for a single object allocated on the heap with `new`.||
14. **C**: ||The destructor is automatically invoked when the object's lifetime ends. For stack-allocated objects, this is when they go out of scope. For heap-allocated objects, this is when `delete` is called on their pointer.||
15. **C**: ||When an object is passed by value, a temporary copy of that object is created to be used inside the function. This creation of a copy is done by the copy constructor.||
16. **B**: ||The `friend` keyword grants a non-member function or another class access to the `private` and `protected` members of the class that declares it as a friend.||
17. **C**: ||When memory is allocated for an array using `new[]`, it must be deallocated using the corresponding array deletion operator `delete[]` to ensure all objects in the array are properly destroyed.||
18. **C**: ||A constructor's job is to ensure that an object is in a valid, usable state immediately upon creation by initializing its data members.||
19. **B**: ||The compiler implicitly passes the address of the object as the first argument to the member function, which becomes the `this` pointer inside that function. So `obj.memberFunc()` is treated like `memberFunc(&obj)`.||
20. **B**: ||In modern C++ (C++11 and later), you can call another constructor from the same class using the member initializer list syntax, e.g., `MyClass() : MyClass(0) {}`.||

---

### **Topic 3: Advanced OOP (Sessions 10-12)**

21. **A class `Derived` inherits from `Base` using `class Derived : protected Base`. What is the accessibility of `public` members of `Base` inside `Derived`?**
    - [ ] They become `public` in `Derived`.
    - [ ] They become `private` in `Derived`.
    - [ ] They become `protected` in `Derived`.
    - [ ] They are inaccessible.
    <br>

22. **What is "object slicing"?**
    - [ ] When a derived class object is assigned to a base class object, the derived-class part of the object is "sliced off".
    - [ ] A technique for optimizing memory usage in objects.
    - [ ] When a class inherits from multiple base classes.
    - [ ] When an exception is thrown during object construction.
    <br>

23. **How is run-time polymorphism achieved in C++?**
    - [ ] Through function overloading.
    - [ ] Through operator overloading.
    - [ ] Through templates.
    - [ ] Through virtual functions.
    <br>

24. **A class is made abstract by:**
    - [ ] Declaring it with the `abstract` keyword.
    - [ ] Not providing a constructor for it.
    - [ ] Making all its member functions `private`.
    - [ ] Including at least one pure virtual function in it.
    <br>

25. **Why should a base class in an inheritance hierarchy have a `virtual` destructor?**
    - [ ] To prevent the class from being instantiated.
    - [ ] To ensure that the correct destructor (the derived class's destructor) is called when deleting a derived object through a base class pointer.
    - [ ] To make the destructor faster.
    - [ ] It is not necessary; the compiler handles it automatically.
    <br>

26. **What is the mechanism used by most C++ compilers to implement virtual functions?**
    - [ ] A switch statement.
    - [ ] A virtual table (vtable) and a virtual pointer (vptr).
    - [ ] A linked list of function pointers.
    - [ ] An `if-else` chain.
    <br>

27. **How is the "diamond problem" of multiple inheritance typically solved in C++?**
    - [ ] By using `friend` functions.
    - [ ] By using private inheritance.
    - [ ] By using `virtual` inheritance.
    - [ ] It cannot be solved.
    <br>

28. **A base class has a non-virtual function `foo()`. A derived class also defines a function `foo()`. If you call `foo()` on a derived object through a base class pointer, which version is called?**
    - [ ] The derived class's version.
    - [ ] The base class's version.
    - [ ] It results in a compilation error.
    - [ ] It results in a runtime error.
    <br>

29. **What is the result of `dynamic_cast<Derived*>(base_ptr)` if `base_ptr` points to an object of the `Base` class, not the `Derived` class?**
    - [ ] A pointer to the `Base` object.
    - [ ] A `nullptr`.
    - [ ] A compilation error.
    - [ ] An exception is thrown.
    <br>

30. **Function overloading is an example of:**
    - [ ] Run-time polymorphism
    - [ ] Operator overloading
    - [ ] Compile-time polymorphism
    - [ ] Data hiding
    <br>

**Answer Key (Topic 3)**
21. **C**: ||With `protected` inheritance, `public` and `protected` members of the base class become `protected` members of the derived class.||
22. **A**: ||Object slicing occurs when a derived class object is copied into a base class object. The derived-specific information is lost in the process because the base class object doesn't have space for it. This is a common bug when passing polymorphic objects by value.||
23. **D**: ||Virtual functions are the mechanism that enables run-time polymorphism. The decision of which function version to call is deferred until runtime and is based on the actual type of the object being pointed to.||
24. **D**: ||A pure virtual function (e.g., `virtual void myFunction() = 0;`) is a function for which the class provides no implementation. Any class containing one or more pure virtual functions is considered an abstract class and cannot be instantiated.||
25. **B**: ||If you delete a derived object via a `Base*` pointer and the destructor is not virtual, only the base class destructor is called, leading to a memory leak of the derived class's resources. A virtual destructor ensures a proper chain of destructor calls, from most-derived to base.||
26. **B**: ||Compilers typically implement virtual functions by creating a vtable (an array of function pointers) for each class with virtual functions, and adding a hidden vptr to each object instance that points to its class's vtable.||
27. **C**: ||Virtual inheritance ensures that the common base class (`A` in the diamond `A -> B, A -> C, B+C -> D`) is included only once in the final derived object (`D`), resolving the ambiguity.||
28. **B**: ||This is function hiding or static binding. Since `foo()` is not virtual, the function call is resolved at compile-time based on the type of the pointer (`Base*`), not the type of the object it points to.||
29. **B**: ||`dynamic_cast` is used for safe downcasting. At runtime, it checks if the cast is valid. Since the object is actually a `Base` type, not a `Derived` type, the cast is invalid, and `dynamic_cast` returns a `nullptr` to indicate failure.||
30. **C**: ||Function overloading (multiple functions with the same name but different parameters) is resolved by the compiler at compile-time based on the arguments provided in the function call. This is also known as static polymorphism.||

---

### **Topic 4: Advanced C++ Features (Sessions 13-18)**

31. **In C++ exception handling, what does a `catch(...)` block do?**
    - [ ] It only catches integer exceptions.
    - [ ] It catches all types of exceptions.
    - [ ] It is a syntax error.
    - [ ] It re-throws the current exception.
    <br>

32. **Templates in C++ provide a mechanism for:**
    - [ ] Run-time polymorphism.
    - [ ] Exception handling.
    - [ ] Generic programming.
    - [ ] Multithreading.
    <br>

33. **What is the default behavior when you open an existing file using an `std::ofstream` object?**
    - [ ] The new data is appended to the end of the file.
    - [ ] The existing content of the file is erased (truncated).
    - [ ] An error is generated because the file already exists.
    - [ ] The user is prompted for an action.
    <br>

34. **Which STL container should you use if you need to store a collection of unique elements in a sorted order?**
    - [ ] `std::vector`
    - [ ] `std::list`
    - [ ] `std::map`
    - [ ] `std::set`
    <br>

35. **The process where local objects are properly destroyed when an exception is thrown is called:**
    - [ ] Stack unwinding.
    - [ ] Exception propagation.
    - [ ] Memory leaking.
    - [ ] Template instantiation.
    <br>

36. **How do you declare an object `myStack` of a class template `Stack<T>` that will hold `double` values?**
    - [ ] `Stack myStack<double>;`
    - [ ] `Stack double myStack;`
    - [ ] `Stack<double> myStack;`
    - [ ] `double Stack myStack;`
    <br>

37. **What is the purpose of the `is_open()` function on a file stream object?**
    - [ ] To open a file if it is closed.
    - [ ] To check if a file was successfully opened.
    - [ ] To close an open file.
    - [ ] To check if the file has content.
    <br>

38. **Which `ios` file mode is used to open a file and start writing at the end of it, preserving existing content?**
    - [ ] `ios::in`
    - [ ] `ios::trunc`
    - [ ] `ios::out`
    - [ ] `ios::app`
    <br>

39. **What is RAII (Resource Acquisition Is Initialization)?**
    - [ ] A technique for initializing resources in a random order.
    - [ ] A design pattern where resource lifetime is tied to an object's lifetime, using constructors and destructors to manage the resource.
    - [ ] A method for allocating memory on the stack instead of the heap.
    - [ ] An old C-style of programming to be avoided in C++.
    <br>

40. **Which STL container provides functionality similar to a dynamic array?**
    - [ ] `std::map`
    - [ ] `std::vector`
    - [ ] `std::set`
    - [ ] `std::stack`
    <br>

**Answer Key (Topic 4)**
31. **B**: ||The `catch(...)` block is a catch-all handler. It will catch any type of exception that was thrown and not caught by a more specific preceding `catch` block.||
32. **C**: ||Templates allow you to write type-independent code (functions and classes) that can operate on any data type, which is the definition of generic programming.||
33. **B**: ||By default, `ofstream` opens a file in `ios::out | ios::trunc` mode. This means if the file exists, its current contents are discarded. To append, you must specify `ios::app`.||
34. **D**: ||`std::set` is the STL container that stores unique elements and automatically keeps them in sorted order. `std::map` stores key-value pairs.||
35. **A**: ||When an exception is thrown, the program "unwinds" the call stack, looking for a handler. As it does so, it correctly calls the destructors for all local objects that are going out of scope. This is a key feature that makes RAII work.||
36. **C**: ||The syntax for instantiating a class template requires specifying the type argument within angle brackets after the class name: `ClassName<Type> objectName;`.||
37. **B**: ||After attempting to open a file, you should always call `is_open()` to verify that the operation was successful before trying to read from or write to the file stream.||
38. **D**: ||`ios::app` stands for append mode. When a file is opened with this flag, the output position is automatically set to the end of the file.||
39. **B**: ||RAII is a fundamental C++ concept. By acquiring a resource (like a file handle or a memory block) in an object's constructor and releasing it in the destructor, you guarantee the resource is properly cleaned up when the object goes out of scope, even if an exception occurs.||
40. **B**: ||`std::vector` is the STL's sequence container that encapsulates a dynamic array, handling memory management automatically as elements are added or removed.||