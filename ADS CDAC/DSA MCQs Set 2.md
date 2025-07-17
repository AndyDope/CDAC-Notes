# **Topic 1: Fundamentals, Stacks, and Queues (Sessions 1-3)**

1.  **An algorithm's time complexity is O(1). If it takes 0.05ms to process 1,000 items, how long will it take to process 1,000,000 items?**
- [ ] 50ms
- [ ] 5ms
- [x] 0.05ms
- [ ] 500ms

**Answer:** ||(C) O(1) complexity is constant time. The time taken is independent of the input size n. Therefore, it will take the same amount of time, 0.05ms.||
<br>

2.  **Which data structure would be most efficient for implementing a "recently viewed items" feature where you only want to store the last 5 items viewed?**
- [ ] Stack
- [ ] Linked List
- [ ] Array
- [x] Queue

**Answer:** ||(D) A queue is ideal here. When a new item is viewed, it is enqueued. If the queue size exceeds 5, the oldest item is dequeued. This naturally maintains the 5 most recent items in order.||
<br>

3.  **A circular queue is implemented in an array of size 10. `front` is at index 7 and `rear` is at index 2. How many elements are in the queue?**
- [ ] 4
- [ ] 5
- [x] 6
- [ ] The state is invalid.

**Answer:** ||(C) When rear has wrapped around and is less than front, the number of elements is (size - front) + (rear + 1). So, (10 - 7) + (2 + 1) = 3 + 3 = 6. The elements are at indices 7, 8, 9, 0, 1, 2.||
<br>

4.  **Which of the following defines an Abstract Data Type (ADT)?**
- [ ] It defines the memory representation and implementation of a data structure.
- [x] It defines a set of values and a set of operations on those values, independent of implementation.
- [ ] It is a data structure that can only store abstract classes.
- [ ] It is another term for a base class in an inheritance hierarchy.

**Answer:** ||(B) An ADT is a logical, mathematical model. It specifies what operations can be performed (e.g., a Stack has push, pop) but says nothing about how they are implemented (e.g., with an array or a linked list).||
<br>

5.  **You evaluate a postfix expression `5 3 2 * + 4 -`. Which data structure is essential for this evaluation?**
- [ ] Queue
- [x] Stack
- [ ] Tree
- [ ] Linked List

**Answer:** ||(B) To evaluate a postfix expression, you read from left to right. When you see a number, you push it onto a stack. When you see an operator, you pop two numbers, perform the operation, and push the result back onto the stack.||
<br>

### **Topic 2: Linked Lists & Recursion (Sessions 4-6)**

6.  **In a singly linked list, you are given a pointer to a node in the middle of the list (not the head). What is the time complexity to delete this node?**
- [ ] O(1)
- [ ] O(log n)
- [x] O(n)
- [ ] O(n log n)

**Answer:** ||(C) To delete a node in a singly linked list, you must modify the next pointer of the previous node. Since you only have a pointer to the current node, you must traverse the list from the head to find the previous node, which takes O(n) time. (A trick exists where you copy the next node's data into the current node and delete the next node, but this is not the standard deletion and fails for the last node).||
<br>

7.  **What is the primary advantage of a doubly linked list over a singly linked list?**
- [ ] It uses less memory per node.
- [x] It allows for efficient traversal in both forward and backward directions.
- [ ] It has a faster O(1) access time to any element.
- [ ] It prevents stack overflow errors.

**Answer:** ||(B) The previous pointer in each node of a doubly linked list allows you to traverse backwards, which is not possible in a singly linked list. It also makes certain operations, like deleting a given node, more efficient.||
<br>

8.  **The recurrence relation `T(n) = T(n/2) + O(1)` represents the time complexity of which algorithm?**
- [ ] Linear Search
- [ ] Merge Sort
- [x] Binary Search
- [ ] Factorial calculation

**Answer:** ||(C) This recurrence relation means the time to solve a problem of size n is the time to solve a problem half the size (n/2) plus some constant time work. This is the definition of Binary Search, which resolves to O(log n).||
<br>

9.  **A "tail-recursive" function is one where:**
- [x] The recursive call is the very last operation performed in the function.
- [ ] It calls itself twice.
- [ ] It has no base case.
- [ ] It returns a pointer to its own tail.

**Answer:** ||(A) In a tail-recursive function, there is no computation performed after the recursive call returns. This allows some compilers to perform "tail-call optimization," converting the recursion into an efficient loop and avoiding stack overflow.||
<br>

10. **To find the middle element of a singly linked list in a single pass, which is the most efficient approach?**
- [ ] Traverse the list once to find the length `n`, then traverse again to `n/2`.
- [x] Use a "slow and fast pointer" approach, where one pointer moves one step and the other moves two steps at a time.
- [ ] Store all elements in an array and find the middle index.
- [ ] Use recursion with a global counter.

**Answer:** ||(B) This is the classic "runner" technique. When the fast pointer reaches the end of the list, the slow pointer will be at the middle. This requires only one pass through the data.||
<br>

### **Topic 3: Trees (Sessions 7-9)**

11. **If a binary tree has a height `h`, what is the maximum number of nodes it can have? (Height of root is 0)**
- [ ] `2h + 1`
- [ ] `2^h`
- [ ] `h²`
- [x] `2^(h+1) - 1`

**Answer:** ||(D) This occurs when the tree is a "perfect" binary tree, completely filled at every level. The number of nodes is the sum of a geometric series 2^0 + 2^1 + ... + 2^h, which equals 2^(h+1) - 1.||
<br>

12. **The in-order traversal of a tree is `A, B, C, D, E` and its pre-order traversal is `D, B, A, C, E`. What is its post-order traversal?**
- [x] A, C, B, E, D
- [ ] A, B, C, E, D
- [ ] E, C, A, B, D
- [ ] D, E, C, B, A

**Answer:** ||(A) From pre-order (NLR), the root is D. From in-order (LNR), everything left of D (A,B,C) is the left subtree, and everything right (E) is the right subtree. By applying this logic recursively, you can reconstruct the tree and find the post-order (LRN) traversal to be A, C, B, E, D.||
<br>

13. **What is the worst-case time complexity for a search operation in a Binary Search Tree (BST)?**
- [ ] O(1)
- [ ] O(log n)
- [x] O(n)
- [ ] O(n log n)

**Answer:** ||(C) The worst case for a BST occurs when it degenerates into a skewed tree (like a linked list), for example, by inserting elements in sorted order. In this case, searching for an element requires traversing every node, leading to O(n) complexity.||
<br>

14. **When deleting a node with two children from a BST, it is replaced by its:**
- [ ] Left child.
- [ ] Right child.
- [x] In-order successor or in-order predecessor.
- [ ] Parent node.

**Answer:** ||(C) To maintain the BST property, the node must be replaced by a value that fits between its left and right subtrees. This is either the largest element in its left subtree (predecessor) or the smallest element in its right subtree (successor).||
<br>

15. **Which of the following is NOT a property of a red-black tree?**
- [ ] Every node is either red or black.
- [ ] The root is always black.
- [x] Every leaf node (NIL) must be red.
- [ ] Any path from a given node to any of its descendant NIL nodes contains the same number of black nodes.

**Answer:** ||(C) The leaf nodes (the conceptual NIL nodes) are always considered black. This property, along with the others, ensures the tree remains balanced.||
<br>

### **Topic 4: Searching, Sorting, and Hashing (Sessions 10-13)**

16. **Which sorting algorithm has the best time complexity for an array that is already sorted?**
- [ ] Quicksort
- [ ] Merge Sort
- [ ] Heapsort
- [x] Insertion Sort (with an optimization)

**Answer:** ||(D) An optimized Insertion Sort can detect that the array is already sorted and will only perform a single pass with n-1 comparisons, giving it a best-case time complexity of O(n). A naive Quicksort would perform at its worst (O(n²)) on a sorted array.||
<br>

17. **A hash function `h(key) = key mod 7` is used with a hash table of size 7. If linear probing is used to resolve collisions, where is the key `23` placed after inserting the keys `15, 11, 2, 9`?**
- [ ] Index 2
- [ ] Index 3
- [ ] Index 4
- [x] Index 5

**Answer:** ||(D) 15 mod 7 = 1. Place 15 at index 1. 11 mod 7 = 4. Place 11 at index 4. 2 mod 7 = 2. Place 2 at index 2. 9 mod 7 = 2. Index 2 is full. Probe to index 3. Place 9 at index 3. 23 mod 7 = 2. Index 2 is full. Probe to 3 (full). Probe to 4 (full). Probe to 5 (empty). Place 23 at index 5.||
<br>

18. **The "partitioning" step is the core of which sorting algorithm?**
- [ ] Merge Sort
- [x] Quicksort
- [ ] Bubble Sort
- [ ] Selection Sort

**Answer:** ||(B) Quicksort works by selecting a pivot and then partitioning the array into two sub-arrays: elements less than the pivot and elements greater than the pivot.||
<br>

19. **What is a key disadvantage of Merge Sort compared to Quicksort?**
- [ ] Merge Sort has a worse average-case time complexity.
- [ ] Merge Sort is not a stable sort.
- [x] Merge Sort requires O(n) auxiliary space.
- [ ] Merge Sort is harder to implement recursively.

**Answer:** ||(C) The merge step in Merge Sort requires a temporary array of the same size as the input to merge the sorted halves. This O(n) space complexity can be a drawback for memory-constrained systems.||
<br>

20. **The "load factor" of a hash table is a measure of:**
- [ ] The speed of the hash function.
- [ ] The number of collisions that have occurred.
- [x] The ratio of occupied slots to the total number of slots.
- [ ] The amount of memory the table uses.

**Answer:** ||(C) The load factor (alpha = n/m, where n is items and m is slots) is a critical metric used to decide when to rehash the table to maintain performance.||
<br>

21. **Why is it problematic to simply delete an element from a hash table that uses open addressing?**
- [ ] It causes a memory leak.
- [x] It breaks the probe chain for other collided elements.
- [ ] It requires rehashing the entire table.
- [ ] It is a very slow O(n) operation.

**Answer:** ||(B) If you empty a slot, a later search for an element whose probe path passed through that slot will stop prematurely, incorrectly concluding the element isn't in the table. This is solved by using a special "DELETED" marker.||
<br>

### **Topic 5: Graphs & Advanced Algorithms (Sessions 14-19)**

22. **Which algorithm is used to find a Minimum Spanning Tree?**
- [ ] Dijkstra's Algorithm
- [ ] Floyd-Warshall Algorithm
- [x] Kruskal's Algorithm
- [ ] Bellman-Ford Algorithm

**Answer:** ||(C) Kruskal's algorithm and Prim's algorithm are two classic greedy algorithms for finding an MST. The others are for shortest path problems.||
<br>

23. **Dijkstra's algorithm may produce incorrect results if the graph contains:**
- [ ] Cycles
- [ ] Multiple edges between two vertices
- [ ] Self-loops
- [x] Negative edge weights

**Answer:** ||(D) Dijkstra's greedy approach of finalizing the shortest path to a vertex assumes path lengths can only increase. A negative edge could create a shorter path to an already "visited" vertex, violating this assumption.||
<br>

24. **In an unweighted graph, which algorithm is equivalent to finding the single-source shortest path?**
- [ ] Depth-First Search (DFS)
- [x] Breadth-First Search (BFS)
- [ ] Prim's Algorithm
- [ ] A* Search

**Answer:** ||(B) BFS explores the graph layer by layer, guaranteeing that it finds the path with the fewest number of edges, which is the definition of the shortest path in an unweighted graph.||
<br>

25. **The Floyd-Warshall algorithm is an example of which design paradigm?**
- [ ] Greedy Method
- [ ] Divide and Conquer
- [x] Dynamic Programming
- [ ] Backtracking

**Answer:** ||(C) It builds up a solution for all-pairs shortest paths by iteratively considering each vertex k as an intermediate point, using previously computed results. This exhibits the optimal substructure and overlapping sub-problems properties of DP.||
<br>

26. **What is the number of edges in a spanning tree of a connected graph with `V` vertices?**
- [ ] V
- [x] V-1
- [ ] V/2
- [ ] It depends on the number of cycles in the original graph.

**Answer:** ||(B) A tree with V vertices always has exactly V-1 edges to connect all vertices without forming a cycle.||
<br>

27. **What is a "greedy choice property"?**
- [ ] A property where the algorithm chooses the option with the highest memory usage.
- [x] A property where making a locally optimal choice is guaranteed to lead to a globally optimal solution.
- [ ] A property of dynamic programming algorithms.
- [ ] A property where the algorithm divides the problem into smaller parts.

**Answer:** ||(B) This is the core principle that allows a greedy algorithm to work correctly. If a problem has this property, the simple greedy approach will find the true optimal solution.||
<br>

28. **Which algorithm typically uses a Disjoint Set Union (DSU) data structure for its implementation?**
- [ ] Prim's Algorithm
- [ ] Dijkstra's Algorithm
- [x] Kruskal's Algorithm
- [ ] Breadth-First Search

**Answer:** ||(C) Kruskal's algorithm needs to efficiently check if adding an edge will form a cycle. A DSU is the perfect data structure for this, as it can quickly determine if two vertices are already in the same connected component.||
<br>

### **Final Review Questions (All Topics)**

29. **The time complexity `O(n log n)` is better than:**
- [ ] O(n)
- [ ] O(log n)
- [ ] O(1)
- [x] O(n²)

**Answer:** ||(D) "Better" means a slower growth rate. O(n log n) grows faster than O(n) but significantly slower than O(n²).||
<br>

30. **What does it mean for a sorting algorithm to be "stable"?**
- [ ] It uses a constant amount of extra memory.
- [ ] Its worst-case and average-case performance are the same.
- [x] It preserves the original relative order of elements with equal keys.
- [ ] It can sort elements of any data type.

**Answer:** ||(C) Stability is important when sorting data on multiple criteria. For example, if a list is already sorted by name, a stable sort by city will keep the names in alphabetical order within each city.||
<br>

31. **Which data structure would you use to efficiently find the median in a stream of incoming numbers?**
- [ ] A sorted array
- [ ] A balanced binary search tree
- [x] Two heaps (a max-heap and a min-heap)
- [ ] A hash table

**Answer:** ||(C) This is a classic advanced problem. By maintaining a max-heap for the smaller half of the numbers and a min-heap for the larger half, the median can always be found in O(1) time by looking at the tops of the heaps.||
<br>

32. **A function's logic involves a single loop that iterates `n` times. Inside the loop, it performs a binary search on an array of size `n`. What is the overall time complexity?**
- [ ] O(n)
- [ ] O(n²)
- [x] O(n log n)
- [ ] O(log n)

**Answer:** ||(C) The loop runs n times. The operation inside the loop takes O(log n) time. The total time complexity is the product of the two: n * O(log n) = O(n log n).||
<br>

33. **Which traversal of a binary tree processes all of a node's descendants before processing the node itself?**
- [ ] Pre-order
- [ ] In-order
- [x] Post-order
- [ ] Level-order

**Answer:** ||(C) Post-order traversal follows the pattern Left-Right-Root. It recursively processes the entire left subtree and the entire right subtree before finally processing the root node. This is useful for tasks like deleting a tree.||
<br>

34. **An Adjacency Matrix is the most efficient representation for:**
- [ ] Sparse graphs
- [ ] Unweighted graphs
- [x] Dense graphs
- [ ] Directed acyclic graphs

**Answer:** ||(C) An adjacency matrix always uses O(V²) space. For a dense graph, where the number of edges E is close to V², the space usage is justified by the extremely fast O(1) time to check for the existence of an edge.||
<br>

35. **The "optimal substructure" property, required for both Greedy and DP algorithms, means:**
- [ ] The problem can be solved by making a locally optimal choice.
- [ ] The problem can be broken into independent sub-problems.
- [x] An optimal solution to the overall problem contains optimal solutions to its sub-problems.
- [ ] The substructure of the data is a tree.

**Answer:** ||(C) This is the formal definition. It means that if you have an optimal solution, any sub-part of that solution is also an optimal solution for its corresponding sub-problem.||
<br>

36. **What is the primary trade-off when using a hash table?**
- [ ] Speed vs. stability
- [ ] Time vs. security
- [ ] Simplicity vs. performance
- [x] Memory space vs. time complexity

**Answer:** ||(D) Hash tables achieve their fast O(1) average time complexity by using a large array (memory space). The load factor represents this trade-off: a lower load factor uses more memory but reduces collisions and improves speed.||
<br>

37. **Which of the following problems exhibits the "greedy choice property"?**
- [ ] 0/1 Knapsack Problem
- [ ] Longest Common Subsequence
- [x] Finding a Minimum Spanning Tree using Prim's algorithm
- [ ] All-Pairs Shortest Path

**Answer:** ||(C) Prim's algorithm works because the greedy choice of always adding the cheapest edge connecting a new vertex to the growing tree is guaranteed to be part of an optimal final solution.||
<br>

38. **The depth of the root of a tree is conventionally:**
- [ ] 1
- [x] 0
- [ ] -1
- [ ] Dependent on the number of children.

**Answer:** ||(B) The depth of a node is the length of the path from the root to that node. The path from the root to itself has a length of 0.||
<br>

39. **In a circular linked list, how do you detect the end of the list during traversal?**
- [ ] When the `next` pointer is `null`.
- [x] When the `next` pointer is equal to the `head` pointer again.
- [ ] When the data value is 0.
- [ ] You cannot detect the end; it loops infinitely.

**Answer:** ||(B) A traversal typically starts at the head and continues as long as the current node's next pointer is not the head. When it becomes the head again, one full cycle has been completed.||
<br>

40. **The process of converting an infix expression like `A + B * C` to a postfix expression `A B C * +` is a classic application of which data structure?**
- [ ] A queue
- [ ] A hash table
- [ ] A binary search tree
- [x] A stack

**Answer:** ||(D) The Shunting-yard algorithm, which performs this conversion, uses a stack to temporarily hold operators and manage their precedence.||
<br>

### **Topic 7: More Challenging Questions**

41. **A complete binary tree with `n` nodes has a height of:**
- [ ] O(n)
- [x] O(log n)
- [ ] O(1)
- [ ] O(n log n)

**Answer:** ||(B) A complete binary tree is always balanced. The relationship between the number of nodes n and the height h is logarithmic. n is approximately 2^h, so h is approximately log₂(n).||
<br>

42. **A hash table of size 11 uses quadratic probing `(h + i²) mod 11`. If the key `22` (hashes to 0) and `33` (hashes to 0) are inserted, where is the key `44` (hashes to 0) placed?**
- [ ] Index 1
- [ ] Index 2
- [x] Index 4
- [ ] Index 9

**Answer:** ||(C) 22 is placed at index 0. 33 hashes to 0 (occupied). Probe 1: (0+1²) mod 11 = 1. Place 33 at index 1. 44 hashes to 0 (occupied). Probe 1: (0+1²) mod 11 = 1 (occupied). Probe 2: (0+2²) mod 11 = 4. Place 44 at index 4.||
<br>

43. **Which statement is true about the relationship between Prim's and Dijkstra's algorithms?**
- [ ] They solve the same problem.
- [x] Their core algorithm structure is very similar, but they use a different "relaxation" or "priority" condition.
- [ ] Prim's uses a stack, while Dijkstra's uses a queue.
- [ ] Dijkstra's is for dense graphs, while Prim's is for sparse graphs.

**Answer:** ||(B) Both algorithms work by growing a set of vertices. However, when updating the priority of a neighbor, Dijkstra's considers the total path cost from the source, while Prim's only considers the weight of the single new edge.||
<br>

44. **Which algorithm is NOT a "divide and conquer" algorithm?**
- [ ] Merge Sort
- [ ] Quicksort
- [ ] Binary Search
- [x] Insertion Sort

**Answer:** ||(D) Insertion Sort is an "incremental" algorithm. It builds the sorted array one element at a time by inserting it into a growing sorted sub-array. It does not recursively divide the main problem.||
<br>

45. **If a graph is represented by an adjacency list, what is the time complexity to find all vertices adjacent to a given vertex `v`?**
- [ ] O(1)
- [ ] O(V)
- [ ] O(E)
- [x] O(degree(v))

**Answer:** ||(D) To find all neighbors of v, you simply traverse the linked list located at index v in the adjacency list array. The length of this list is equal to the degree of vertex v.||
<br>

46. **What is the number of possible binary search trees with 3 nodes?**
- [ ] 3
- [ ] 4
- [x] 5
- [ ] 6

**Answer:** ||(C) The number of unique BSTs for n nodes is given by the Catalan number C_n. For n=3, the number is 5. You can draw them out to verify.||
<br>

47. **A self-balancing BST like an AVL tree maintains balance through operations called:**
- [ ] Partitions
- [x] Rotations
- [ ] Merges
- [ ] Heapifying

**Answer:** ||(B) When an insertion or deletion unbalances the tree (height difference between subtrees becomes > 1), single or double rotations (LL, RR, LR, RL) are performed to restore the balance property.||
<br>

48. **What is the most accurate description of the relationship between an ADT and a Data Structure?**
- [ ] They are the same thing.
- [ ] An ADT is an implementation of a Data Structure.
- [x] A Data Structure is an implementation of an ADT.
- [ ] An ADT is a physical model, while a Data Structure is a logical model.

**Answer:** ||(C) The ADT is the logical blueprint (the interface), defining what operations are possible. A Data Structure is the concrete, physical implementation (the class), defining how the data is stored and how the operations work. E.g., Stack is the ADT; ArrayStack or LinkedListStack are the data structures.||
<br>

49. **In a graph with a negative cycle, which algorithm will fail to produce a correct result?**
- [ ] Breadth-First Search
- [ ] Prim's Algorithm
- [ ] Kruskal's Algorithm
- [x] Bellman-Ford Algorithm (used for shortest paths with negative edges)

**Answer:** ||(D) The Bellman-Ford algorithm can detect the presence of a negative cycle, but it cannot produce a "shortest path" because you could traverse the negative cycle infinitely to make the path length infinitely small. The concept of a shortest path is undefined in such a graph.||
<br>

50. **You need to implement a data structure that can efficiently perform two operations: add a new element and find the minimum element. Which is the best choice?**
- [ ] A sorted array
- [ ] A balanced binary search tree
- [x] A min-heap
- [ ] A hash table

**Answer:** ||(C) A min-heap is specifically designed for these operations. Finding the minimum is always an O(1) operation (it's the root). Adding a new element is an efficient O(log n) operation. A balanced BST can also do this, but with O(log n) for both operations, making the heap superior for finding the minimum.||