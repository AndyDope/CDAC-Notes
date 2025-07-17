# **Comprehensive MCQ Review: All Chapters**

1.  **Which pillar of computational thinking involves focusing on the essential features of a problem while ignoring irrelevant details?**
- [ ] Decomposition
- [ ] Pattern Recognition
- [x] Abstraction
- [ ] Algorithm Design

**Answer:** ||(C) Abstraction is the process of hiding complexity and exposing only the necessary parts. This is the core idea behind interfaces and Abstract Data Types.||
<br>

2.  **What is the time complexity of accessing an element in an array at a known index `i`?**
- [x] O(1)
- [ ] O(log n)
- [ ] O(n)
- [ ] O(n²)

**Answer:** ||(A) Accessing an element by its index in an array is a direct memory calculation and takes the same amount of time regardless of the array's size. This is constant time, O(1).||
<br>

3.  **Which data structure is most appropriate for managing function calls in a programming language?**
- [ ] Queue
- [x] Stack
- [ ] Tree
- [ ] Hash Table

**Answer:** ||(B) The call stack uses the LIFO (Last-In, First-Out) principle. When a function is called, it's pushed onto the stack; when it returns, it's popped off.||
<br>

4.  **A queue is implemented using a standard linear array. After several enqueue and dequeue operations, the `front` pointer is at index 5 and the `rear` is at index 8. What is the main issue with this implementation?**
- [ ] The queue is about to overflow.
- [x] The space at indices 0 through 4 is wasted and cannot be easily reused.
- [ ] The `peek` operation will be very slow.
- [ ] The queue can no longer be dequeued.

**Answer:** ||(B) In a simple linear array implementation, the front pointer only moves forward, leaving unused space at the beginning of the array. This is solved by using a circular queue.||
<br>

5.  **Which of the following data structures is non-linear?**
- [ ] Array
- [ ] Stack
- [ ] Queue
- [x] Tree

**Answer:** ||(D) Arrays, Stacks, and Queues arrange data sequentially (linearly). Trees represent hierarchical data, which is a non-linear structure.||
<br>

6.  **What is the primary disadvantage of a linked list compared to an array?**
- [ ] It has a fixed size.
- [ ] Insertion and deletion of elements is slow.
- [x] It does not allow random access to elements by index in O(1) time.
- [ ] It cannot store duplicate elements.

**Answer:** ||(C) To get to the i-th element of a linked list, you must traverse from the head node through i-1 nodes, which is an O(n) operation.||
<br>

7.  **If you need to implement a "Back" button functionality in a web browser, which data structure would you use?**
- [ ] Queue
- [x] Stack
- [ ] Tree
- [ ] Hash Table

**Answer:** ||(B) Each new page visited is pushed onto a stack. The "Back" button simply pops the last visited page off the stack. This is a classic LIFO application.||
<br>

8.  **What does the `next` pointer of the last node in a standard singly linked list point to?**
- [ ] The head node.
- [ ] The first node.
- [ ] Itself.
- [x] null.

**Answer:** ||(D) The null pointer signifies the end of the list. In a circular linked list, it would point to the head node.||
<br>

9.  **A recursive function must have at least two parts: a recursive step and a __________.**
- [ ] loop
- [ ] pointer
- [x] base case
- [ ] data structure

**Answer:** ||(C) The base case is the condition that stops the recursion. Without it, the function would call itself infinitely, leading to a StackOverflowError.||
<br>

10. **What is the time complexity of a naive recursive algorithm for the Fibonacci sequence?**
- [ ] O(log n)
- [ ] O(n)
- [ ] O(n²)
- [x] O(2ⁿ)

**Answer:** ||(D) A naive implementation fib(n) = fib(n-1) + fib(n-2) has a branching factor of 2, leading to an exponential number of redundant calculations as n grows.||
<br>

11. **The topmost node of a tree is called the ______.**
- [ ] Leaf
- [x] Root
- [ ] Edge
- [ ] Child

**Answer:** ||(B) The root is the single node at the top of the hierarchy from which all other nodes descend.||
<br>

12. **In a Binary Search Tree (BST), where would you find the smallest element?**
- [ ] At the root node.
- [ ] At the rightmost leaf node.
- [x] At the leftmost node.
- [ ] It can be anywhere in the tree.

**Answer:** ||(C) The BST property states that all nodes in the left subtree are smaller than the root. By repeatedly going left from the root until you can't go left anymore, you will find the minimum value.||
<br>

13. **Which tree traversal visits the nodes in the order: Left, Root, Right?**
- [ ] Pre-order
- [x] In-order
- [ ] Post-order
- [ ] Level-order

**Answer:** ||(B) In-order traversal visits the left subtree, then the root itself, then the right subtree.||
<br>

14. **What is the main purpose of a self-balancing tree like an AVL tree?**
- [ ] To ensure the tree is always a complete binary tree.
- [x] To prevent the tree from becoming skewed, thus guaranteeing O(log n) performance.
- [ ] To make the in-order traversal run faster.
- [ ] To reduce the memory usage of the tree.

**Answer:** ||(B) A standard BST can degrade to O(n) performance if data is inserted in sorted order. A self-balancing tree performs rotations to keep its height logarithmic, guaranteeing O(log n) for search, insert, and delete operations.||
<br>

15. **Level-order traversal of a tree is typically implemented using which data structure?**
- [ ] A stack
- [x] A queue
- [ ] Recursion
- [ ] An array

**Answer:** ||(B) Level-order traversal is a Breadth-First Search (BFS). BFS uses a queue to process nodes layer by layer.||
<br>

16. **What is a major prerequisite for using the Binary Search algorithm?**
- [ ] The data must be stored in a linked list.
- [x] The data must be sorted.
- [ ] The data must not contain any duplicate values.
- [ ] The data must be integers.

**Answer:** ||(B) Binary search works by repeatedly dividing the search interval in half. This is only possible if the data is sorted, so it knows which half to discard.||
<br>

17. **Which of the following sorting algorithms has a time complexity of O(n²)?**
- [ ] Merge Sort
- [ ] Quicksort
- [ ] Heapsort
- [x] Selection Sort

**Answer:** ||(D) Selection Sort, Bubble Sort, and Insertion Sort are all simple, quadratic-time sorting algorithms. Quicksort's worst case is O(n²), but its average case is O(n log n).||
<br>

18. **Which of the following is a "stable" sorting algorithm?**
- [ ] Quicksort
- [ ] Heapsort
- [ ] Selection Sort
- [x] Merge Sort

**Answer:** ||(D) Merge Sort is a stable sort, meaning it preserves the original relative order of equal elements. Quicksort and Heapsort are unstable.||
<br>

19. **The "divide and conquer" strategy is the basis for which sorting algorithm?**
- [ ] Insertion Sort
- [ ] Bubble Sort
- [x] Quicksort
- [ ] All of the above

**Answer:** ||(C) Quicksort and Merge Sort are the classic examples of divide and conquer algorithms.||
<br>

20. **The process of merging two sorted arrays of size `m` and `n` takes how much time?**
- [ ] O(1)
- [ ] O(log n)
- [x] O(m+n)
- [ ] O(m\*n)

**Answer:** ||(C) The merge step requires iterating through both arrays once, so its time complexity is linear with respect to the total number of elements.||
<br>

21. **In a hash table, what is a "collision"?**
- [ ] When the hash table is full.
- [ ] When the hash function returns an error.
- [x] When two different keys map to the same index.
- [ ] When a key is not found in the table.

**Answer:** ||(C) A collision is the event where the hash function and compression function result in the same array index for two or more distinct keys.||
<br>

22. **Which collision resolution technique involves using a linked list at each index of the hash table?**
- [ ] Linear Probing
- [ ] Quadratic Probing
- [ ] Double Hashing
- [x] Separate Chaining

**Answer:** ||(D) Separate Chaining resolves collisions by having each bucket in the array be the head of a linked list that stores all keys that hashed to that bucket.||
<br>

23. **What is the primary drawback of linear probing?**
- [ ] It requires extra memory outside the table.
- [x] It suffers from "primary clustering," where long runs of occupied slots form.
- [ ] It is very complex to implement.
- [ ] It cannot handle string keys.

**Answer:** ||(B) Primary clustering happens when collisions pile up next to each other, causing subsequent collisions to require long traversals to find an empty slot.||
<br>

24. **In a graph, what is a "vertex"?**
- [ ] A connection between two nodes.
- [x] A node or a point in the graph.
- [ ] The weight or cost of a connection.
- [ ] A path that starts and ends at the same node.

**Answer:** ||(B) A vertex is the fundamental unit of a graph, representing an entity or a node. An edge is the connection between vertices.||
<br>

25. **Depth-First Search (DFS) of a graph is typically implemented using what?**
- [ ] A queue
- [ ] A priority queue
- [x] A stack (or recursion)
- [ ] An array

**Answer:** ||(C) DFS explores as far down a path as possible before backtracking. This "last-in, first-out" exploration order is naturally managed by a stack. Recursion uses the system's own call stack to achieve this.||
<br>

26. **Which algorithm is used to find the shortest path from a single source to all other vertices in a weighted graph with non-negative edge weights?**
- [ ] Prim's Algorithm
- [ ] Kruskal's Algorithm
- [x] Dijkstra's Algorithm
- [ ] Floyd-Warshall Algorithm

**Answer:** ||(C) This is the definition of Dijkstra's algorithm. Prim's and Kruskal's are for finding Minimum Spanning Trees.||
<br>

27. **What is a Minimum Spanning Tree (MST)?**
- [ ] The shortest path that visits every vertex.
- [ ] A tree with the smallest possible height for a given number of nodes.
- [ ] A subgraph that connects all vertices with the minimum number of edges and no cycles.
- [x] A subgraph that connects all vertices with the minimum total edge weight and no cycles.

**Answer:** ||(D) An MST connects all vertices (it's a spanning tree) and has the minimum possible sum of edge weights among all possible spanning trees.||
<br>

28. **Which of the following is a "greedy" algorithm?**
- [ ] Merge Sort
- [x] Prim's Algorithm
- [ ] Floyd-Warshall Algorithm
- [ ] Naive Fibonacci Recursion

**Answer:** ||(B) Prim's algorithm greedily chooses the cheapest edge at each step to connect a new vertex to its growing tree. Dijkstra's and Kruskal's are also greedy.||
<br>

29. **The property of "overlapping sub-problems" is a key characteristic of problems solved by which paradigm?**
- [ ] Greedy Algorithms
- [ ] Divide and Conquer
- [x] Dynamic Programming
- [ ] Brute Force

**Answer:** ||(C) Dynamic Programming excels when a recursive solution would solve the same smaller sub-problems repeatedly. DP avoids this by storing the results of sub-problems.||
<br>

30. **The "tabulation" or "bottom-up" method is an implementation technique for which paradigm?**
- [x] Dynamic Programming
- [ ] Greedy Method
- [ ] Recursion
- [ ] Backtracking

**Answer:** ||(A) Tabulation involves filling a table with solutions to sub-problems, starting from the base cases and working upwards, typically using loops instead of recursion.||
<br>

31. **What is the number of edges in a complete graph with `V` vertices?**
- [ ] V-1
- [ ] V
- [x] V \* (V-1) / 2
- [ ] V²

**Answer:** ||(C) In a complete graph, every vertex is connected to every other vertex. The number of such connections is given by the combination formula VC2, which simplifies to V\*(V-1)/2.||
<br>

32. **A "doubly linked list" has what feature that a singly linked list does not?**
- [ ] A pointer to the head node.
- [ ] A pointer to the next node.
- [x] A pointer to the previous node.
- [ ] It can store data.

**Answer:** ||(C) A doubly linked list node contains a next pointer and a prev pointer, allowing for traversal in both forward and backward directions.||
<br>

33. **The `pop` operation on a stack corresponds to which linked list operation for an efficient implementation?**
- [ ] Deleting from the end of the list.
- [x] Deleting from the beginning of the list.
- [ ] Deleting from the middle of the list.
- [ ] Searching the list.

**Answer:** ||(B) For an O(1) pop operation, you would remove the head of the linked list, which is a constant-time operation.||
<br>

34. **If a tree has `V` vertices, how many edges does it have?**
- [ ] V
- [x] V-1
- [ ] V/2
- [ ] It depends on the type of tree.

**Answer:** ||(B) A key property of any tree is that the number of edges is always exactly one less than the number of vertices.||
<br>

35. **The process of re-calculating hashes and moving all elements to a new, larger array in a hash table is called:**
- [ ] Rebalancing
- [x] Rehashing
- [ ] Re-chaining
- [ ] Re-probing

**Answer:** ||(B) Rehashing is triggered when the load factor of the hash table exceeds a certain threshold, to maintain its average O(1) performance.||
<br>

36. **Which algorithm is used to find the shortest paths between all pairs of vertices in a graph?**
- [ ] Dijkstra's Algorithm
- [ ] Prim's Algorithm
- [ ] Breadth-First Search
- [x] Floyd-Warshall Algorithm

**Answer:** ||(D) The Floyd-Warshall algorithm uses dynamic programming to compute the shortest paths for all pairs of vertices simultaneously. Dijkstra's is a single-source algorithm.||
<br>

37. **What does the "memoization" technique in dynamic programming involve?**
- [ ] Using an iterative approach to build a table of solutions.
- [x] Using a recursive approach but caching the results of sub-problems to avoid re-computation.
- [ ] Making a locally optimal choice at each step.
- [ ] Dividing the problem into completely independent sub-problems.

**Answer:** ||(B) Memoization is the top-down DP approach. It follows the natural recursive structure of the problem but adds a cache (or "memo") to store and retrieve results of sub-problems.||
<br>

38. **The "partition" step, where an array is rearranged around a pivot element, is central to which algorithm?**
- [ ] Merge Sort
- [ ] Heapsort
- [ ] Radix Sort
- [x] Quicksort

**Answer:** ||(D) The partition step is the "divide" phase of the Quicksort algorithm.||
<br>

39. **What is the Big O complexity of inserting an element at the beginning of an array of size `n`?**
- [ ] O(1)
- [ ] O(log n)
- [x] O(n)
- [ ] O(n log n)

**Answer:** ||(C) To insert an element at the beginning, all n existing elements must be shifted one position to the right to make space. This is a linear time operation.||
<br>

40. **A "degenerate" or "skewed" binary tree has the performance characteristics of which other data structure?**
- [ ] An array
- [ ] A queue
- [x] A linked list
- [ ] A hash table

**Answer:** ||(C) A degenerate tree is one where every node has only one child, forming a long, single chain. Searching or traversing this structure requires visiting each node sequentially, just like a linked list, leading to O(n) performance.||
<br>

41. **If a function calls itself, it is known as:**
- [ ] An iteration
- [ ] A loop
- [x] A recursion
- [ ] A selection

**Answer:** ||(C) Recursion is the technique where a function calls itself to solve a problem.||
<br>

42. **The Adjacency List representation of a graph is most space-efficient for which type of graph?**
- [ ] Dense graphs (many edges)
- [x] Sparse graphs (few edges)
- [ ] Complete graphs
- [ ] Weighted graphs

**Answer:** ||(B) An adjacency list uses O(V+E) space. An adjacency matrix uses O(V²) space. For a sparse graph where E is much smaller than V², O(V+E) is significantly better than O(V²).||
<br>

43. **Which traversal of the tree `(Root=10, Left=5, Right=15)` would produce the output `5, 15, 10`?**
- [ ] Pre-order
- [ ] In-order
- [x] Post-order
- [ ] Level-order

**Answer:** ||(C) Post-order traversal follows the pattern Left, Right, Root. It would visit the left child (5), then the right child (15), and finally the root (10).||
<br>

44. **Which algorithm design strategy does NOT guarantee an optimal solution for all problems?**
- [ ] Dynamic Programming
- [ ] Divide and Conquer
- [x] Greedy Method
- [ ] Brute Force

**Answer:** ||(C) The Greedy method makes locally optimal choices. While this works for some problems (like making change with standard coins), it fails for others (like the 0/1 Knapsack problem) where a local choice may prevent a better global solution.||
<br>

45. **What is the defining property of a Binary Heap data structure?**
- [ ] All elements are sorted.
- [ ] Every node's left child is smaller, and its right child is larger.
- [x] It is a complete binary tree where every parent node is greater than (or less than) its children.
- [ ] It has O(1) search time.

**Answer:** ||(C) This describes the "heap property." In a Max-Heap, every parent is greater than or equal to its children. In a Min-Heap, every parent is less than or equal to its children. It must also be a complete binary tree.||
<br>

46. **What is the number of nodes in a complete binary tree of height `h`?**
- [ ] Exactly 2^(h+1) - 1
- [x] Between 2^h and 2^(h+1) - 1
- [ ] Exactly 2^h
- [ ] V-1

**Answer:** ||(B) A complete binary tree must be full down to height h-1, and the last level h is filled from left to right. A tree of height h has at least 2^h nodes (if only the leftmost node at level h exists) and at most 2^(h+1)-1 nodes (if it's a perfect tree).||
<br>

47. **The `enqueue` operation in a queue is equivalent to which operation on a list for an efficient implementation?**
- [ ] Inserting at the beginning.
- [ ] Deleting from the end.
- [x] Inserting at the end.
- [ ] Getting the middle element.

**Answer:** ||(C) Enqueue means adding to the rear of the queue. In a linked list implementation with a tail pointer, this is an O(1) insertion at the end.||
<br>

48. **If you need to sort a list of numbers that are all within a small, fixed range (e.g., all numbers are between 0 and 100), which algorithm can be very efficient?**
- [ ] Quicksort
- [x] Counting Sort
- [ ] Merge Sort
- [ ] Insertion Sort

**Answer:** ||(B) Counting Sort is a non-comparison-based sorting algorithm that is extremely efficient (O(n+k) where k is the range of numbers) when the range of input data is small.||
<br>

49. **In a graph, a path that starts and ends at the same vertex is called a:**
- [ ] Tree
- [ ] Loop
- [x] Cycle
- [ ] Link

**Answer:** ||(C) A cycle is a path of edges and vertices wherein a vertex is reachable from itself.||
<br>

50. **The process of finding the location of a specific element in a data structure is called:**
- [ ] Sorting
- [ ] Traversal
- [ ] Recursion
- [x] Searching

**Answer:** ||(D) Searching is the fundamental operation of finding an element. Algorithms like Linear Search and Binary Search are used for this purpose.||