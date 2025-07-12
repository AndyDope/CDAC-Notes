## **Session 6: Recursion**

Welcome to Session 6. **Recursion** is a programming technique where a function calls itself to solve a problem. It's a powerful alternative to iteration (loops) for problems that can be broken down into smaller, self-similar sub-problems. Understanding recursion is not just about writing code; it's about learning a new way to think about problems.

---

### **1. What is Recursion? The Core Idea**

A recursive solution has two essential parts:

1.  **Base Case:** A simple condition that stops the recursion. It's the smallest version of the problem that can be solved directly without making another recursive call. Without a base case, a recursive function would call itself forever, leading to a `StackOverflowError`.
2.  **Recursive Step:** The part of the function that breaks the problem down into a smaller version of itself and calls the function again with the smaller problem. The function trusts that the recursive call will correctly solve the smaller problem.

**Analogy: Matryoshka Dolls (Russian Nesting Dolls)**
Imagine you want to find the innermost doll.
*   **Your algorithm:** `findInnermost(doll)`
*   **Recursive Step:** If the `doll` can be opened, open it, take out the smaller doll inside, and then `findInnermost(smaller_doll)`.
*   **Base Case:** If the `doll` cannot be opened, you have found the innermost one. Return it.

---

### **2. How Recursion Works: The Call Stack**

When a function is called, a **stack frame** is pushed onto the **call stack**. This frame contains the function's parameters, local variables, and the return address. When the function finishes, its frame is popped off the stack.

Recursion uses this mechanism extensively. Each recursive call pushes a new frame onto the stack.

**Visualizing `factorial(3)`:**

Let's trace the execution and the call stack for `factorial(3)`.
`factorial(n) = n * factorial(n-1)`

1.  `main()` calls `factorial(3)`. A frame for `factorial(3)` is pushed.
2.  `factorial(3)` must calculate `3 * factorial(2)`. It calls `factorial(2)` and waits. A frame for `factorial(2)` is pushed.
3.  `factorial(2)` must calculate `2 * factorial(1)`. It calls `factorial(1)` and waits. A frame for `factorial(1)` is pushed.
4.  `factorial(1)` must calculate `1 * factorial(0)`. It calls `factorial(0)` and waits. A frame for `factorial(0)` is pushed.
5.  `factorial(0)` hits the **base case** and returns `1`. Its frame is popped.
6.  `factorial(1)` receives the `1`, calculates `1 * 1 = 1`, returns `1`. Its frame is popped.
7.  `factorial(2)` receives the `1`, calculates `2 * 1 = 2`, returns `2`. Its frame is popped.
8.  `factorial(3)` receives the `2`, calculates `3 * 2 = 6`, returns `6`. Its frame is popped.
9.  `main()` receives `6`.

**The Call Stack in Action:**

```bash
Stack at Step 1:    Stack at Step 4:       Stack at Step 6:      Stack at Step 8:
+---------------+    +---------------+       +---------------+       +---------------+
|    main()     |    | factorial(0)  |       | factorial(2)  |       | factorial(3)  |
+---------------+    +---------------+       +---------------+       +---------------+
                     | factorial(1)  |       | factorial(3)  |       |    main()     |
                     +---------------+       +---------------+       +---------------+
                     | factorial(2)  |       |    main()     |
                     +---------------+       +---------------+
                     | factorial(3)  |
                     +---------------+
                     |    main()     |
                     +---------------+
```

This is why infinite recursion causes a `StackOverflowError`—the call stack runs out of memory.

---

### **3. Types of Recursion**

*   **Direct Recursion:** A function calls itself directly (e.g., `factorial()`). This is the most common type.
*   **Indirect Recursion:** A function `A` calls another function `B`, which in turn calls function `A`. This creates a cycle.

### **4. Pros and Cons of Recursion**

**Pros:**
*   **Elegance and Readability:** For problems that are naturally recursive (like tree traversals, Towers of Hanoi, Fibonacci), the recursive solution is often much cleaner, shorter, and easier to understand than an iterative one.
*   **Problem Solving:** It simplifies complex problems by breaking them into smaller, identical pieces.

**Cons:**
*   **Performance Overhead:** Each function call adds overhead (pushing/popping stack frames), which can make recursion slower than iteration for simple problems.
*   **Stack Overflow:** For very deep recursion (many nested calls), you risk running out of stack memory.
*   **Redundant Calculations:** A naive recursive solution can be very inefficient. For example, a simple `fibonacci(n)` function calculates the same sub-problems over and over again. This can be solved with a technique called **memoization** or **dynamic programming**.

---

### **5. Function Complexity during Recursion**

Analyzing the time complexity of recursive functions is done using a **recurrence relation**.

*   **Factorial `T(n) = T(n-1) + O(1)`:** The time to solve for `n` is the time to solve for `n-1` plus some constant time work. This unwinds to `O(n)`.
*   **Binary Search `T(n) = T(n/2) + O(1)`:** The time to solve for `n` is the time to solve for `n/2` plus constant time work. This resolves to `O(log n)`.
*   **Merge Sort `T(n) = 2T(n/2) + O(n)`:** The time to solve for `n` is twice the time to solve for `n/2` (two sub-problems) plus linear time `O(n)` work to merge the results. This resolves to `O(n log n)`.

> **Quick Question:** What are the two essential components of any valid recursive function?
> **Answer:** A base case to stop the recursion and a recursive step that calls itself with a smaller version of the problem.

---

## **Topic Summary & Revision**

*   **Core Idea:** Recursion is a function calling itself to solve smaller, self-similar versions of a problem.
*   **Must-Haves:** Every recursive function requires a **base case** and a **recursive step**.
*   **Mechanism:** Recursion works by using the **call stack**. Each call adds a new frame to the stack.
*   **Stack Overflow:** Infinite recursion or very deep recursion exhausts the stack memory.
*   **Pros vs. Cons:** Recursion offers code elegance but can have performance overhead and stack depth limitations compared to iteration.
*   **Complexity:** The time complexity of recursive algorithms is described by recurrence relations.

---

## **MCQs for Exam Preparation**

1.  **What will happen if a recursive function does not have a base case?**
    - [ ] It will not compile.
    - [ ] It will return 0 or null by default.
    - [ ] It will run indefinitely until the system crashes or a `StackOverflowError` occurs.
    - [ ] It will automatically stop after a fixed number of calls.
    <br>

2.  **Which of the following data structures is implicitly used by the system to manage recursive function calls?**
    - [ ] Queue
    - [ ] Linked List
    - [ ] Tree
    - [ ] Stack
    <br>

3.  **Consider the function: `int fun(int n) { if (n <= 1) return 1; return n * fun(n-1); }`. What does `fun(4)` return?**
    - [ ] 10
    - [ ] 12
    - [ ] 24
    - [ ] 4
    <br>

4.  **Which of the following problems is generally NOT solved efficiently using a simple recursive solution due to repeated computations of the same sub-problems?**
    - [ ] Factorial of a number.
    - [ ] Traversing a tree.
    - [ ] Binary search on a sorted array.
    - [ ] Finding the nth Fibonacci number.
    <br>

5.  **The recurrence relation for the Towers of Hanoi problem is `T(n) = 2T(n-1) + 1`. What is its time complexity?**
    - [ ] O(n)
    - [ ] O(log n)
    - [ ] O(n²)
    - [ ] O(2ⁿ)
    <br>

6.  **What is tail recursion?**
    - [ ] A recursion where the function calls itself at the beginning of the function.
    - [ ] A recursion where the recursive call is the very last operation in the function.
    - [ ] A recursion that uses a `while` loop.
    - [ ] A recursion that calls two different functions.
    <br>

7.  **What is the base case for finding the factorial of a positive integer `n` recursively?**
    - [ ] `if (n == 100)`
    - [ ] `if (n <= 1)`
    - [ ] `if (n > 1)`
    - [ ] There is no base case.
    <br>

8.  **How many times will the following function be called for `printFun(3)`? (Including the initial call)**
    ```java
    void printFun(int n) {
        if (n < 1) return;
        System.out.println(n);
        printFun(n - 1); // First recursive call
        printFun(n - 1); // Second recursive call
    }
    ```
    - [ ] 3
    - [ ] 7
    - [ ] 8
    - [ ] 15
    <br>

9.  **Which of the following is an advantage of recursion over iteration?**
    - [ ] Lower memory usage.
    - [ ] Faster execution speed.
    - [ ] More readable and elegant code for problems that are inherently recursive.
    - [ ] It can solve problems that iteration cannot.
    <br>

10. **A function `A` calls function `B`, and function `B` calls function `A`. This is an example of:**
    - [ ] Direct Recursion
    - [ ] Tail Recursion
    - [ ] Indirect Recursion
    - [ ] Iteration
    <br>

**Answer Key**
1.  **C**: ||Without a base case, the function will never stop calling itself. Each call adds a new frame to the call stack until the stack runs out of memory, causing a StackOverflowError.||
2.  **D**: ||The call stack is the fundamental data structure that manages the state of active function calls. Each recursive call pushes a new frame onto this stack.||
3.  **C**: ||This is the factorial function. fun(4) = 4 \* fun(3) = 4 \* (3 \* fun(2)) = 4 \* (3 \* (2 \* fun(1))) = 4 \* 3 \* 2 \* 1 = 24.||
4.  **D**: ||A naive recursive Fibonacci solution fib(n) = fib(n-1) + fib(n-2) has a massive number of overlapping sub-problems. For instance, fib(5) calls fib(4) and fib(3). fib(4) also calls fib(3), so fib(3) is computed twice. This leads to exponential time complexity.||
5.  **D**: ||A recurrence relation of the form T(n) = 2T(n-1) + c resolves to an exponential time complexity of O(2ⁿ). This is because each call generates two more calls, creating a tree of calls that grows exponentially.||
6.  **B**: ||Tail recursion occurs when the recursive call is the absolute last statement executed in the function. Some compilers can optimize tail recursion into a simple loop, eliminating the risk of stack overflow. This is called tail-call optimization.||
7.  **B**: ||The recursion needs to stop when the problem becomes trivial. The factorial of 1 is 1, and the factorial of 0 is also defined as 1. So n <= 1 is the condition that stops the chain of calls.||
8.  **D**: ||Let C(n) be the number of calls. C(n) = 1 + 2C(n-1). C(0)=1. C(1)=1+2C(0)=3. C(2)=1+2C(1)=7. C(3)=1+2C(2)=1+2(7)=15. The total number of calls is 15.||
9.  **C**: ||The main benefit of recursion is code clarity for problems that naturally break down into smaller versions of themselves, like tree traversals. Iterative solutions for these problems often require managing an explicit stack and are much harder to write and understand. In terms of performance (speed and memory), iteration is almost always better.||
10. **C**: ||When two or more functions call each other in a cycle, it is known as indirect recursion.||

---

## **Bonus Tips**

*   **The Leap of Faith:** When writing a recursive function, you must trust that your function will work correctly for the smaller sub-problem. Write the base case first. Then, for the recursive step, just assume `recursive_call(n-1)` gives you the correct answer for `n-1`, and figure out how to use that result to solve for `n`.
*   **Recursion vs. Iteration:** Every recursive algorithm can be re-written iteratively using an explicit [[DS Sessions 2 & 3 - Algorithms & Data Structures#b) Stacks (LIFO)|stack]]. If you are worried about stack depth or performance, use an iterative approach. If the problem is naturally recursive (like a tree) and the code clarity is more important, use recursion.
*   **Debugging Recursion:** Debugging recursion can be tricky. The best way is to use `print` statements. At the very beginning of your recursive function, print the parameters it was called with. This allows you to trace the entire call chain and see how the problem is being broken down.
*   **Memoization:** To fix the inefficiency of naive recursion for problems like Fibonacci, you can use memoization. This means storing the results of expensive function calls (in a hash map or an array) and returning the cached result when the same inputs occur again. This is the first step towards a technique called Dynamic Programming.

**🔗Links:** [[DS Sessions 7, 8 & 9 - Trees & Applications]]