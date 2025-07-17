## **Algorithms and Data Structures Overview**

This page provides a high-level summary of the essential concepts covered in the PG-DAC Algorithms and Data Structures module. Use it as a quick-recall cheat sheet before exams.

---

### [[DS Session 1 - Problem Solving & Computational Thinking|Session 1: Problem Solving & Computational Thinking]]
*   [[DS Session 1 - Problem Solving & Computational Thinking#1. What is Computational Thinking?|Computational Thinking]]: A methodical approach involving **Decomposition**, **Pattern Recognition**, **Abstraction**, and **Algorithm Design**.
*   [[DS Session 1 - Problem Solving & Computational Thinking#2. A Four-Step Problem-Solving Process|Problem-Solving Process]]: A 4-step method: **Understand** the problem, **Plan** a solution (algorithm), **Implement** the plan (code), and **Review** the result.

---

### [[DS Sessions 2 & 3 - Algorithms & Data Structures|Sessions 2 & 3: Algorithms & Data Structures]]
*   [[DS Sessions 2 & 3 - Algorithms & Data Structures#2. Complexity Analysis of Algorithms (Big O Notation)|Big O Notation]]: Describes the worst-case time complexity of an algorithm as input size `(n)` grows (e.g., `O(1)`, `O(log n)`, `O(n)`, `O(n log n)`, `O(n²)`).
*   [[DS Sessions 2 & 3 - Algorithms & Data Structures#3. OO Design: Abstract Data Types (ADTs)|ADT (Abstract Data Type)]]: A logical description of a data structure defining *what* it does (operations) but not *how* it does it (implementation).
*   [[DS Sessions 2 & 3 - Algorithms & Data Structures#b) Stacks (LIFO)|Stack]]: A LIFO (Last-In, First-Out) data structure with `push` and `pop` operations.
*   [[DS Sessions 2 & 3 - Algorithms & Data Structures#c) Queues (FIFO)|Queue]]: A FIFO (First-In, First-Out) data structure with `enqueue` and `dequeue` operations.
*   [[DS Sessions 2 & 3 - Algorithms & Data Structures#d) Circular Queues|Circular Queue]]: An efficient array-based queue that reuses space by wrapping around.

---

### [[DS Sessions 4 & 5 - Linked List Data Structures|Sessions 4 & 5: Linked List Data Structures]]
*   [[DS Sessions 4 & 5 - Linked List Data Structures#1. Core Concept: Nodes and Pointers|Linked List]]: A dynamic data structure of nodes linked by pointers. Has slow O(n) access but fast O(1) insertion/deletion.
*   [[DS Sessions 4 & 5 - Linked List Data Structures#3. Types of Linked Lists|Singly vs. Doubly]]: A **Singly** list has a `next` pointer. A **Doubly** list has `next` and `previous` pointers, allowing backward traversal.
*   [[DS Sessions 4 & 5 - Linked List Data Structures#c) Circular Linked List|Circular Linked List]]: The last node's `next` pointer points back to the `head`.
*   [[DS Sessions 4 & 5 - Linked List Data Structures#4. Implementing a Stack and Queue with Linked Lists|Implementation]]: Linked lists are excellent for implementing dynamic Stacks and Queues with O(1) operations.

---

### [[DS Session 6 - Recursion|Session 6: Recursion]]
*   [[DS Session 6 - Recursion#1. What is Recursion? The Core Idea|Recursion]]: A programming technique where a function calls itself to solve smaller, self-similar sub-problems.
*   [[DS Session 6 - Recursion#1. What is Recursion? The Core Idea|Base Case & Recursive Step]]: Every recursive function needs a **base case** to stop and a **recursive step** to break the problem down.
*   [[DS Session 6 - Recursion#2. How Recursion Works: The Call Stack|Call Stack]]: Recursion is managed by the system's call stack. Deep recursion can cause a `StackOverflowError`.
*   [[DS Session 6 - Recursion#4. Pros and Cons of Recursion|Recursion vs. Iteration]]: Recursion offers code elegance for inherently recursive problems (like trees) but often has higher performance overhead than iteration.

---

### [[DS Sessions 7, 8 & 9 - Trees & Applications|Sessions 7-9: Trees & Applications]]
*   [[DS Sessions 7, 8 & 9 - Trees & Applications#2. Binary Trees|Binary Tree]]: A hierarchical data structure where each node has at most two children (left and right).
*   [[DS Sessions 7, 8 & 9 - Trees & Applications#3. Tree Traversals|Tree Traversals]]:
    *   **In-order** (Left, Root, Right): Sorts a BST.
    *   **Pre-order** (Root, Left, Right): Used to copy trees.
    *   **Post-order** (Left, Right, Root): Used to delete trees.
    *   **Level-order** (BFS): Visits level by level using a Queue.
*   [[DS Sessions 7, 8 & 9 - Trees & Applications#4. Binary Search Trees (BST)|Binary Search Tree (BST)]]: An ordered tree where `left < root < right`. Provides average O(log n) search, insert, and delete.
*   [[DS Sessions 7, 8 & 9 - Trees & Applications#5. Overcoming BST Limitations: AVL Trees|AVL Tree]]: A self-balancing BST that uses rotations to guarantee O(log n) worst-case performance.

---

### [[DS Sessions 10, 11 & 12 - Searching and Sorting Algorithms|Sessions 10-12: Searching and Sorting Algorithms]]
*   [[DS Sessions 10, 11 & 12 - Searching and Sorting Algorithms#2. The Binary Search|Binary Search]]: An O(log n) search algorithm that **requires a sorted array**.
*   [[DS Sessions 10, 11 & 12 - Searching and Sorting Algorithms#1. Simple Sorting Algorithms - O(n²)|O(n²) Sorts]]: **Selection Sort**, **Bubble Sort**, and **Insertion Sort**. Simple but inefficient for large datasets.
*   [[DS Sessions 10, 11 & 12 - Searching and Sorting Algorithms (Continuation)#**4. Merge Sort (Emphasis)**|Merge Sort]]: A stable, O(n log n) sorting algorithm that requires O(n) extra space.
*   [[DS Sessions 10, 11 & 12 - Searching and Sorting Algorithms (Continuation)#**5. Quicksort (Emphasis)**|Quicksort]]: An unstable, O(n log n) average-case sorting algorithm that is in-place (O(log n) stack space).

---

### [[DS Session 13 - Hash Functions and Hash Tables|Session 13: Hash Functions and Hash Tables]]
*   [[DS Session 13 - Hash Functions and Hash Tables#1. Core Concepts: Hash Function and Hash Table|Hash Table]]: A data structure providing average O(1) time for search, insertion, and deletion.
*   [[DS Session 13 - Hash Functions and Hash Tables#2. The Problem: Hash Collisions|Collision]]: Occurs when two different keys map to the same index.
*   [[DS Session 13 - Hash Functions and Hash Tables#3. Collision Resolution Technique 1: Separate Chaining|Separate Chaining]]: Resolves collisions by storing collided elements in a linked list at the conflicted index.
*   [[DS Session 13 - Hash Functions and Hash Tables#4. Collision Resolution Technique 2: Open Addressing (Probing)|Open Addressing]]: Resolves collisions by finding the next available slot in the array itself (e.g., **Linear Probing**, **Quadratic Probing**).
*   [[DS Session 13 - Hash Functions and Hash Tables#5. Inserting and Deleting from a Hash Table (Open Addressing)|Deletion in Open Addressing]]: Requires a special "DELETED" marker to preserve the probe chain.

---

### [[DS Sessions 14, 15 & 16 - Graphs and Applications|Sessions 14-16: Graphs and Applications]]
*   [[DS Sessions 14, 15 & 16 - Graphs and Applications#**a) Breadth-First Search (BFS) - In-depth**|Breadth-First Search (BFS)]]: Explores a graph layer by layer using a Queue. Finds the shortest path in unweighted graphs.
*   [[DS Sessions 14, 15 & 16 - Graphs and Applications#**b) Depth-First Search (DFS) - In-depth**|Depth-First Search (DFS)]]: Explores a graph by going as deep as possible down a path before backtracking, using a Stack or recursion.
*   [[DS Sessions 14, 15 & 16 - Graphs and Applications#a) Dijkstra's Algorithm (Single-Source Shortest Path)|Dijkstra's Algorithm]]: Finds the shortest path from a single source in a **weighted graph with non-negative edges**.
*   [[DS Sessions 14, 15 & 16 - Graphs and Applications#**Minimum Spanning Trees (MST) (In-depth)**|Minimum Spanning Tree (MST)]]: A subgraph connecting all vertices with the minimum total edge weight.
    *   [[DS Sessions 14, 15 & 16 - Graphs and Applications#a) Prim's Algorithm|Prim's Algorithm]]: Grows the MST from a single vertex.
    *   [[DS Sessions 14, 15 & 16 - Graphs and Applications#**b) Kruskal's Algorithm**|Kruskal's Algorithm]]: Adds the next cheapest edge as long as it doesn't form a cycle.

---

### [[DS Sessions 17, 18 & 19 - Algorithm Design Strategies|Sessions 17-19: Algorithm Design Strategies]]
*   [[DS Sessions 17, 18 & 19 - Algorithm Design Strategies#1. Greedy Method|Greedy Method]]: Makes the locally optimal choice at each step.
*   [[DS Sessions 17, 18 & 19 - Algorithm Design Strategies#2. Divide and Conquer|Divide and Conquer]]: Break the problem into sub-problems, solve them recursively, and combine the results.
*   [[DS Sessions 17, 18 & 19 - Algorithm Design Strategies#3. Dynamic Programming (DP) - In-depth|Dynamic Programming]]: Solves problems with overlapping sub-problems by storing the results of sub-problems to avoid re-computation.
    *   [[DS Sessions 17, 18 & 19 - Algorithm Design Strategies#b) The DP Solution: Memoization (Top-Down Approach)|Memoization]]: A top-down recursive approach with caching.
    *   [[DS Sessions 17, 18 & 19 - Algorithm Design Strategies#c) The DP Solution: Tabulation (Bottom-Up Approach)|Tabulation]]: A bottom-up iterative approach that fills a table.

---

🔗 **[[DSA MCQs|All MCQs]]**