### **Sessions 2 & 3: Algorithms & Data Structures**

Welcome. Now that we have a framework for [[DS Session 1 - Problem Solving & Computational Thinking|problem-solving]], we can begin our journey into the core of this module. This session introduces two fundamental concepts: **Algorithms** and **Data Structures**. They are the "verbs" and "nouns" of computer programming. An algorithm is a set of instructions, and a data structure is a way of organizing data so that these instructions can be executed efficiently.

---

#### **1. Introductory Concepts & Algorithm Constructs**

An **algorithm**, as we've learned, is a step-by-step procedure for solving a problem. To be valid, an algorithm must have a few key properties:
*   **Finiteness:** It must terminate after a finite number of steps.
*   **Definiteness:** Each step must be precisely and unambiguously defined.
*   **Input:** It has zero or more well-defined inputs.
*   **Output:** It has one or more well-defined outputs.
*   **Effectiveness:** Each step must be basic enough to be carried out, in principle, by a person using only pencil and paper.

Algorithms are built using three basic constructs:
1.  **Sequence:** A series of steps executed one after another.
2.  **Selection (or Conditional):** A decision-making step, typically an `if-then-else` statement, which determines the next step based on a condition.
3.  **Iteration (or Repetition):** A loop (`for`, `while`) that repeats a block of steps.

---

#### **2. Complexity Analysis of Algorithms (Big O Notation)**

Why are there so many ways to sort a list? Why not just one? The answer is **efficiency**. Different algorithms perform differently depending on the size of the input data. We need a way to measure and compare this efficiency.

**Complexity Analysis** is the study of how the resource requirements of an algorithm (like time and memory) grow as the size of the input `(n)` grows. We are most often concerned with the **Time Complexity**.

**Big O Notation** is the mathematical notation used to describe the **worst-case scenario** or the upper bound of an algorithm's time complexity. It tells us how the runtime grows relative to the input size `n`.

**Visualizing Complexity Growth:**

```bash
          |
Runtime   |
          |                  ..O(n²)
          |                ..
          |              ..
          |            ..
          |        .. O(n log n)
          |     ...
          |   ..   O(n)
          | ...
          |.. O(log n)
          |___________ O(1)________________
          0            Input Size (n) -->
```

*   **O(1) - Constant Time:** The best. The algorithm takes the same amount of time regardless of the input size.
    *   *Example:* Accessing an element in an array by its index (`myArray[5]`).
*   **O(log n) - Logarithmic Time:** Excellent. The runtime grows very slowly. Every time you double the input size, you only add one extra step.
    *   *Example:* Binary Search.
*   **O(n) - Linear Time:** Good. The runtime grows directly in proportion to the input size.
    *   *Example:* Finding an item in an unsorted list (sequential search).
*   **O(n log n) - Log-Linear Time:** Very good. This is the gold standard for comparison-based sorting algorithms.
    *   *Example:* Merge Sort, Quicksort (average case).
*   **O(n²) - Quadratic Time:** Becomes slow very quickly. The runtime is proportional to the square of the input size. Often involves nested loops over the data.
    *   *Example:* Bubble Sort, Selection Sort.
*   **O(2ⁿ) - Exponential Time:** Extremely slow. Avoid at all costs for large inputs.
    *   *Example:* A naive recursive solution for Fibonacci numbers.

> **Quick Question:** If an algorithm has a time complexity of O(n), and it takes 2 seconds to run for an input of 1000 items, how long would you roughly expect it to take for an input of 2000 items?
> **Answer:** Approximately 4 seconds. Since the runtime grows linearly with the input size, doubling the input will roughly double the runtime.

---

#### **3. OO Design: Abstract Data Types (ADTs)**

An **Abstract Data Type (ADT)** is a high-level, logical description of a data structure. It defines:
1.  A collection of data.
2.  A set of operations that can be performed on that data.

Crucially, an ADT defines **WHAT** the data structure does, but **NOT HOW** it does it. This is [[Java Session 4 - Object Oriented Programming Concepts#b) Abstraction|Abstraction]] in action.

**Analogy: A Car**
*   **ADT (The logical description):** A car is a thing that holds passengers (data) and has operations like `start()`, `accelerate()`, `brake()`, and `turn()`.
*   **Data Structure (The concrete implementation):** This could be a petrol car, an electric car, or a hybrid car. The way `accelerate()` is *implemented* is very different for each, but from the driver's perspective (the user of the ADT), the operation is the same.

In Java, an `interface` is the perfect tool for defining an ADT. The `class` that `implements` the interface provides the concrete data structure.

---

#### **4. Basic Data Structures**

Now let's look at the implementation of some of the most fundamental data structures.

##### **a) Arrays**
An array is the simplest data structure: a contiguous block of memory holding elements of the same type.
*   **Strength:** Fast, O(1) random access using an index.
*   **Weakness:** Fixed size. Insertion and deletion are slow (O(n)) because elements must be shifted.

##### **b) Stacks (LIFO)**
A **Stack** is an ADT that follows a **Last-In, First-Out (LIFO)** principle. The last element added is the first one to be removed.

**Analogy:** A stack of plates. You add a new plate to the top, and you take a plate from the top.

**Core Operations (The ADT Definition):**
*   `push(item)`: Add an item to the top of the stack.
*   `pop()`: Remove and return the item from the top of the stack.
*   `peek()`: Look at the top item without removing it.
*   `isEmpty()`: Check if the stack is empty.

**Implementation: Using an Array**
We can implement a stack using a simple array and an integer variable `top` to keep track of the index of the top element.

**Visualizing a Stack (Array Implementation):**

```bash
// Initial State: top = -1 (empty)
[ , , , , ]
  ^
 top

// push(10): top becomes 0
[ 10, , , , ]
  ^
 top

// push(20): top becomes 1
[ 10, 20, , , ]
      ^
     top

// peek(): returns 20, top remains 1
[ 10, 20, , , ]
      ^
     top

// pop(): returns 20, top becomes 0
[ 10, , , , ]
  ^
 top
```

##### **c) Queues (FIFO)**
A **Queue** is an ADT that follows a **First-In, First-Out (FIFO)** principle. The first element added is the first one to be removed.

**Analogy:** A queue of people at a ticket counter.

**Core Operations (The ADT Definition):**
*   `enqueue(item)`: Add an item to the rear of the queue.
*   `dequeue()`: Remove and return the item from the front of the queue.
*   `peek()`: Look at the front item without removing it.
*   `isEmpty()`: Check if the queue is empty.

**Visualizing a Queue (Array Implementation):**
Implementing a queue with a standard array is tricky because as you dequeue items, you leave empty space at the front. This leads to the need for a **Circular Queue**.

##### **d) Circular Queues**
A circular queue is a linear data structure that overcomes the limitation of a simple array-based queue. The rear of the queue can "wrap around" to the front of the array, reusing empty space.

We use two pointers, `front` and `rear`.

**Visualizing a Circular Queue:**

```bash
// Initial State: front = -1, rear = -1
[ , , , , ]
 F/R

// enqueue(10): front=0, rear=0
[ 10, , , , ]
  F/R

// enqueue(20): rear=1
[ 10, 20, , , ]
  F    R

// enqueue(30): rear=2
[ 10, 20, 30, , ]
  F         R

// dequeue(): returns 10, front=1
[   , 20, 30, , ]
      F    R

// Now, if we enqueue past the end, rear wraps around.
// enqueue(40), enqueue(50), enqueue(60)
[ 60, 20, 30, 40, 50]
   R   F

// The queue is now full. The condition for full is when (rear + 1) % size == front.
```

> **Quick Question:** You need to implement the "Undo" functionality in a text editor. Which data structure is most appropriate?
> **Answer:** A **Stack**. Each action (typing, deleting) is `push`ed onto the stack. When the user hits "Undo," you `pop` the last action and reverse it.

---

### **Topic Summary & Revision**

*   **Algorithm:** A finite, definite, and effective step-by-step procedure.
*   **Big O Notation:** Describes the worst-case time complexity of an algorithm as input size `(n)` grows. Key complexities: `O(1)`, `O(log n)`, `O(n)`, `O(n log n)`, `O(n²)`.
*   **ADT (Abstract Data Type):** Defines *what* a data structure does (its operations), separating it from its concrete implementation (*how* it does it).
*   **Stack:** A LIFO (Last-In, First-Out) data structure. Operations: `push`, `pop`, `peek`.
*   **Queue:** A FIFO (First-In, First-Out) data structure. Operations: `enqueue`, `dequeue`, `peek`.
*   **Circular Queue:** An efficient array-based implementation of a queue that reuses space by allowing the `rear` to wrap around to the start of the array.

---

### **MCQs for Exam Preparation**

1.  **Which of the following data structures follows the First-In, First-Out (FIFO) principle?**
    - [ ] Stack
    - [ ] Array
    - [ ] Queue
    - [ ] Tree
    <br>

2.  **An algorithm's time complexity is described as O(log n). How does its runtime change when the input size is doubled?**
    - [ ] The runtime also doubles.
    - [ ] The runtime increases by a small constant amount.
    - [ ] The runtime is squared.
    - [ ] The runtime remains exactly the same.
    <br>

3.  **What is the defining characteristic of an Abstract Data Type (ADT)?**
    - [ ] It specifies the memory layout of the data structure.
    - [ ] It defines a set of operations but hides the implementation details.
    - [ ] It can only be implemented using arrays.
    - [ ] It provides the Java code for a data structure.
    <br>

4.  **A stack is implemented using an array of size 10. After pushing 6 elements, a `pop()` operation is performed, followed by another `pop()`. What is the index of the `top` element? (Assume the first element is at index 0 and `top` is -1 for an empty stack).**
    - [ ] 3
    - [ ] 4
    - [ ] 5
    - [ ] 6
    <br>

5.  **What is the worst-case time complexity for searching for an element in an unsorted array of size `n`?**
    - [ ] O(1)
    - [ ] O(log n)
    - [ ] O(n)
    - [ ] O(n²)
    <br>

6.  **Which real-world application is a classic example of a Queue?**
    - [ ] The back button in a web browser.
    - [ ] A printer queue handling print jobs.
    - [ ] The function call stack during recursion.
    - [ ] Checking for balanced parentheses in an expression.
    <br>

7.  **What is the primary advantage of a circular queue over a standard linear queue implemented with an array?**
    - [ ] It has a faster `peek()` operation.
    - [ ] It can store more elements than the array's size.
    - [ ] It allows for more efficient use of the array's space.
    - [ ] It can handle elements of different data types.
    <br>

8.  **Consider an empty stack. The following operations are performed: `push(5)`, `push(10)`, `pop()`, `push(15)`, `push(20)`, `pop()`, `peek()`. What value is returned by the `peek()` operation?**
    - [ ] 5
    - [ ] 10
    - [ ] 15
    - [ ] 20
    <br>

9.  **Which of the following sorting algorithms has a worst-case time complexity of O(n²)?**
    - [ ] Merge Sort
    - [ ] Heap Sort
    - [ ] Quick Sort
    - [ ] Bubble Sort
    <br>

10. **A function `F` has a loop that iterates from 1 to `n`. Inside this loop, there is another nested loop that also iterates from 1 to `n`. What is the Big O notation for this function `F`?**
    - [ ] O(1)
    - [ ] O(n)
    - [ ] O(n log n)
    - [ ] O(n²)
    <br>

**Answer Key**
1.  **C**: ||A Queue operates on a First-In, First-Out basis, like a line of people. A Stack is Last-In, First-Out (LIFO).||
2.  **B**: ||Logarithmic complexity means the runtime increases by a constant amount when the input size is multiplied by a constant factor. Doubling the input (from n to 2n) adds only one conceptual 'step' (log(2n) = log(2) + log(n)), so the increase is very small.||
3.  **B**: ||An ADT is a logical definition. It separates the interface (what it does) from the implementation (how it does it), which is a core principle of abstraction.||
4.  **A**: ||Initial: top=-1. Push 6 elements: top becomes 5 (at index 5). First pop(): returns element at index 5, top becomes 4. Second pop(): returns element at index 4, top becomes 3. The final index of the top element is 3.||
5.  **C**: ||In the worst case, you might have to look at every single element in the array to find what you're looking for (or to determine it's not there). This requires n comparisons, so the complexity is O(n).||
6.  **B**: ||Print jobs are handled in the order they are received, which is a perfect example of a FIFO (Queue) process. The browser back button and function calls use a Stack (LIFO).||
7.  **C**: ||In a standard linear queue, once elements are dequeued from the front, that space is wasted. A circular queue allows the rear to wrap around and reuse this empty space, leading to more efficient memory usage.||
8.  **C**: ||Let's trace the stack: 1. push(5) -> [5].  2. push(10) -> [5, 10]. 3. pop() -> returns 10, stack is [5].  4. push(15) -> [5, 15].  5. push(20) -> [5, 15, 20].  6. pop() -> returns 20, stack is [5, 15]. 7. peek() -> looks at the top element without removing it, which is 15.||
9.  **D**: ||Bubble Sort (and also Insertion Sort and Selection Sort) has a worst-case time complexity of O(n²). Merge Sort and Heap Sort are O(n log n). Quick Sort's worst case is O(n²), but its average case is O(n log n). Bubble Sort is consistently O(n²).||
10. **D**: ||A loop that runs n times and contains another loop that also runs n times results in the inner code block being executed approximately n \* n = n² times. Therefore, the complexity is O(n²).||

### **Bonus Tips**

- **Big O is about Growth, not Speed:** A common misconception is that an O(n) algorithm is always faster than an O(n²) algorithm. For very small n, the O(n²) algorithm might be faster due to lower constant factors. Big O notation is about describing how the performance scales as n becomes very large.
    
- **Lab Tip (Stack/Queue Implementation):** When implementing a stack or queue with an array, always check for two boundary conditions: **Overflow** (trying to push/enqueue to a full structure) and **Underflow** (trying to pop/dequeue from an empty structure). Handling these gracefully is key.
    
- **Think ADT First:** When faced with a new problem, don't immediately jump to thinking "should I use an array or a linked list?". First, think about the operations you need. "Do I need to add/remove from one end only (LIFO)? It's a Stack ADT." "Do I need to add to one end and remove from the other (FIFO)? It's a Queue ADT." Once you've identified the ADT, you can then decide on the best underlying data structure to implement it.
    
- **Complexity of Loops:** A quick way to estimate time complexity: A single loop that goes through n elements is typically O(n). A nested loop where both loops go through n elements is typically O(n²). A loop that halves the search space at each step (like binary search) is O(log n).
    

**🔗Links:** [[DS Sessions 4 & 5 - Linked List Data Structures]]