## **Sessions 7, 8 & 9: Trees & Applications**

Welcome. So far, we have dealt with linear data structures like [[DS Sessions 4 & 5 - Linked List Data Structures|Linked Lists]], [[DS Sessions 2 & 3 - Algorithms & Data Structures#b) Stacks (LIFO)|Stacks]], and [[DS Sessions 2 & 3 - Algorithms & Data Structures#c) Queues (FIFO)|Queues]], where elements are arranged sequentially. Now we move to **Trees**, which are hierarchical data structures. They are incredibly useful for representing data that has a parent-child relationship, such as file systems, organizational charts, and even the syntax of a program.

---

### **1. Trees and Terminology**

A **tree** is a collection of nodes connected by edges. It's a non-linear, hierarchical data structure.

**Key Terminology:**
*   **Node:** An entity that contains a data value and pointers to its child nodes.
*   **Root:** The topmost node in a tree. It is the only node with no parent.
*   **Edge:** The link between a parent node and a child node.
*   **Parent:** A node that has child nodes.
*   **Child:** A node that has a parent node.
*   **Siblings:** Nodes that share the same parent.
*   **Leaf Node:** A node with no children.
*   **Path:** A sequence of nodes and edges from one node to another.
*   **Height of a Node:** The number of edges on the longest path from the node down to a leaf. The height of a leaf is 0.
*   **Height of a Tree:** The height of its root node.
*   **Depth of a Node:** The number of edges from the root to the node. The depth of the root is 0.
*   **Degree of a Node:** The number of children a node has.

**Visualizing a Tree:**

```bash
                  A  (Root, Depth 0, Height 2)
                 / \
                /   \
 (Edge) -->    B     C  (Children of A, Siblings)
              /     / \
             /     /   \
            D     E     F (Leaves, Height 0)
```
In the tree above:
*   `A` is the root.
*   `B` and `C` are children of `A`.
*   `D`, `E`, `F` are leaf nodes.
*   The path from A to E is A -> C -> E.
*   The height of node C is 1. The height of the tree is 2.
*   The depth of node E is 2.

---

### **2. Binary Trees**

A **Binary Tree** is a special type of tree where each node can have at most **two** children: a left child and a right child. This is the most common type of tree used in computer science.

**Types of Binary Trees:**
*   **Full Binary Tree:** A binary tree where every node has either 0 or 2 children.
*   **Complete Binary Tree:** A binary tree where all levels are completely filled except possibly the last level, and the last level has its nodes filled from left to right.
*   **Perfect Binary Tree:** A full binary tree where all leaf nodes are at the same depth.
*   **Balanced Binary Tree:** A binary tree where the height of the left and right subtrees of any node differ by at most one. (e.g., AVL Tree).
*   **Degenerate (or Skewed) Tree:** A tree where each parent node has only one child. It behaves like a [[DS Sessions 4 & 5 - Linked List Data Structures|Linked List]].

**Visualizing Tree Types:**

```c
      (Full, Perfect, Complete)       (Complete, but not Full)      (Degenerate/Skewed)
              A                             A                             A
             / \                           / \                           /
            B   C                         B   C                         B
           / \ / \                       / \                           /
          D  E F  G                      D   E                         C
                                                                      /
                                                                     D
```

---

### **3. Tree Traversals**

Traversing a tree means visiting every node in the tree exactly once. Unlike linear data structures, there are multiple logical ways to do this. The three main traversal methods are based on [[DS Session 6 - Recursion|recursion]].

Let's use this tree for the examples:
```bash
          (1)
         /   \
       (2)   (3)
      / \
    (4) (5)
```

##### **a) In-order Traversal (Left, Root, Right)**
1.  Traverse the left subtree.
2.  Visit the root.
3.  Traverse the right subtree.
*   **Result:** `4, 2, 5, 1, 3`
*   **Use Case:** For a Binary Search Tree, this traversal visits the nodes in **sorted order**.

##### **b) Pre-order Traversal (Root, Left, Right)**
1.  Visit the root.
2.  Traverse the left subtree.
3.  Traverse the right subtree.
*   **Result:** `1, 2, 4, 5, 3`
*   **Use Case:** Useful for creating a copy of a tree or getting a prefix expression (e.g., `+ a b`).

##### **c) Post-order Traversal (Left, Right, Root)**
1.  Traverse the left subtree.
2.  Traverse the right subtree.
3.  Visit the root.
*   **Result:** `4, 5, 2, 3, 1`
*   **Use Case:** Useful for deleting nodes in a tree (you delete children before the parent) or getting a postfix expression (e.g., `a b +`).

These three are a type of **Depth First Search (DFS)** because they go deep into one branch before exploring others.

##### **d) Level-order Traversal (Breadth First Search - BFS)**
This traversal visits nodes level by level, from left to right. It is not recursive; it is implemented using a [[DS Sessions 2 & 3 - Algorithms & Data Structures#c) Queues (FIFO)|Queue]].
*   **Result:** `1, 2, 3, 4, 5`

---

### **4. Binary Search Trees (BST)**

A **Binary Search Tree (BST)** is a special type of binary tree that imposes a strict ordering on its nodes.

**The BST Property:**
For any given node `N`:
1.  All values in the **left subtree** of `N` are **less than** `N`'s value.
2.  All values in the **right subtree** of `N` are **greater than** `N`'s value.
3.  Both the left and right subtrees must also be binary search trees.

**Visualizing a BST:**

```bash
          (8)
         /   \
       (3)   (10)
      / \       \
    (1) (6)     (14)
       / \       /
     (4) (7)   (13)
```

**Operations:**
*   **Search:** Searching in a BST is very fast. You start at the root. If the value you're looking for is less than the current node, you go left; if it's greater, you go right. You repeat this until you find the value or hit a `null` pointer.
    *   **Complexity:** In a balanced BST, search is **O(log n)**. In the worst case (a degenerate tree), it becomes **O(n)**.
*   **Insertion:** Follow the same path as a search. When you reach a `null` pointer, you insert the new node there.
*   **Deletion:** This is the most complex operation, with three cases for the node to be deleted:
    1.  **Node is a leaf:** Simply remove it.
    2.  **Node has one child:** Replace the node with its child.
    3.  **Node has two children:** Find its **in-order successor** (the smallest value in its right subtree) or **in-order predecessor** (the largest value in its left subtree). Replace the node's value with its successor/predecessor's value, and then delete the successor/predecessor node (which is now an easier case 1 or 2 deletion).

---

### **5. Overcoming BST Limitations: AVL Trees**

*   **Limitation of BST:** If you insert elements in a sorted order (e.g., 1, 2, 3, 4, 5), the BST becomes a degenerate tree, and its performance degrades to that of a linked list (O(n)).
*   **Solution: Self-Balancing Trees.**
*   An **AVL Tree** is a self-balancing BST. After every insertion or deletion, it performs "rotations" to ensure that the tree remains balanced (the height difference between left and right subtrees of any node is at most 1). This guarantees that all operations (search, insert, delete) remain **O(log n)**.

---

## **Topic Summary & Revision**

*   **Tree:** A non-linear, hierarchical data structure of nodes and edges.
*   **Binary Tree:** A tree where each node has at most two children (left and right).
*   **Tree Traversals:** Methods for visiting every node.
    *   **DFS:** In-order (LNR), Pre-order (NLR), Post-order (LRN).
    *   **BFS:** Level-order (uses a Queue).
*   **Binary Search Tree (BST):** An ordered binary tree where `left < root < right`.
*   **BST Performance:** Provides fast **O(log n)** search, insertion, and deletion on average, but degrades to **O(n)** in the worst case (a skewed tree).
*   **AVL Tree:** A self-balancing BST that uses rotations to guarantee **O(log n)** worst-case performance for all operations.

---

## **MCQs for Exam Preparation**

1.  **Which tree traversal method would visit the nodes of a Binary Search Tree in ascending sorted order?**
    - [ ] Pre-order
    - [ ] Post-order
    - [ ] In-order
    - [ ] Level-order
    <br>

2.  **What is the maximum number of nodes in a perfect binary tree of height `h`? (Assume height of a single-node tree is 0)**
    - [ ] 2h + 1
    - [ ] 2ⁿ
    - [ ] 2^(h+1) - 1
    - [ ] 2^h
    <br>

3.  **In a complete binary tree, if a node is at index `i` in an array representation, its left child is at what index?**
    - [ ] `i/2`
    - [ ] `2\*i`
    - [ ] `2\*i + 1`
    - [ ] `2\*i - 1`
    <br>

4.  **You need to delete a node from a BST that has two children. What is the standard procedure?**
    - [ ] Replace the node with its left child.
    - [ ] Replace the node with its right child.
    - [ ] Replace the node's value with its in-order successor, then delete the successor.
    - [ ] Simply set the node's pointer from its parent to null.
    <br>

5.  **Which data structure is typically used to implement a level-order traversal (BFS) of a tree?**
    - [ ] Stack
    - [ ] Queue
    - [ ] Array
    - [ ] Linked List
    <br>

6.  **The post-order traversal of a certain binary tree is `D, E, B, F, G, C, A`. The in-order traversal is `D, B, E, A, F, C, G`. What is the pre-order traversal?**
    - [ ] A, B, D, E, C, F, G
    - [ ] A, B, C, D, E, F, G
    - [ ] A, C, F, G, B, D, E
    - [ ] A, B, E, D, C, G, F
    <br>

7.  **What is the primary motivation for using a self-balancing BST like an AVL tree over a standard BST?**
    - [ ] They use less memory per node.
    - [ ] They are easier to implement.
    - [ ] They guarantee O(log n) worst-case time complexity for operations.
    - [ ] They allow for faster level-order traversal.
    <br>

8.  **The root of a tree is at depth `d=0`. A node `N` is at depth `d`. The number of edges on the path from the root to `N` is:**
    - [ ] d+1
    - [ ] d
    - [ ] d-1
    - [ ] 2^d
    <br>

9.  **A binary tree has 10 nodes. What is the maximum possible height and minimum possible height of this tree?**
    - [ ] Max: 9, Min: 3
    - [ ] Max: 10, Min: 4
    - [ ] Max: 9, Min: 4
    - [ ] Max: 10, Min: 3
    <br>

10. **Which of the following is always a full binary tree?**
    - [ ] A complete binary tree.
    - [ ] A perfect binary tree.
    - [ ] A binary search tree.
    - [ ] A skewed tree.
    <br>

**Answer Key**
1.  **C**: ||The In-order traversal (Left-Root-Right) property of a BST ensures that values are visited in their natural sorted order.||
2.  **C**: ||A perfect binary tree of height h has 2⁰ + 2¹ + ... + 2^h nodes. This is a geometric series which sums to 2^(h+1) - 1. For h=2, nodes = 2³-1 = 7.||
3.  **C**: ||In a 1-based indexing array, the children of node i are at 2i and 2i+1. However, in a 0-based indexing array (standard in Java), the children of node i are at 2\*i + 1 (left) and 2\*i + 2 (right).||
4.  **C**: ||To maintain the BST property, the node must be replaced by the next highest value (in-order successor) or previous highest value (in-order predecessor). The successor is the smallest node in the right subtree. This preserves the ordering.||
5.  **B**: ||BFS works by processing nodes level by level. A queue (FIFO) is perfect for this: you add the root, then in a loop, you dequeue a node, process it, and enqueue its children.||
6.  **A**: ||From the post-order traversal (LRN), the last element A is the root. In the in-order traversal (LNR), everything to the left of A (D, B, E) is in the left subtree, and everything to the right (F, C, G) is in the right subtree. Now repeat the process for the subtrees. For the left subtree {D, B, E}, the post-order is D, E, B, so B is the root. Following this logic reconstructs the tree, and the pre-order (NLR) is A, B, D, E, C, F, G.||
7.  **C**: ||A standard BST can degenerate into a linked list in the worst case, making operations O(n). A self-balancing tree like AVL performs rotations to maintain a logarithmic height, which guarantees that search, insert, and delete operations will not be worse than O(log n).||
8.  **B**: ||The depth of a node is defined as the number of edges on the path from the root to that node.||
9.  **A**: ||Maximum height occurs when the tree is a skewed list (degenerate tree), where each node has one child. For 10 nodes, the height would be 9 (from root at level 0 to leaf at level 9). Minimum height occurs when the tree is as complete as possible. A height of 2 allows for 2^(2+1)-1 = 7 nodes. A height of 3 allows for 2^(3+1)-1 = 15 nodes. Since we need 10 nodes, the minimum height must be 3.||
10. **B**: ||A perfect binary tree is one where all internal nodes have two children and all leaves are at the same level. This definition automatically satisfies the condition for a full binary tree (every node has 0 or 2 children). A complete binary tree is not necessarily full (the last level might not be filled).||

---

## **Bonus Tips**

*   **Recursion is Your Friend:** Tree traversal algorithms are the classic examples of recursion. When trying to solve a tree problem, always think recursively first. The iterative solution using a stack or queue is often more complex to implement.
*   **The Power of In-order Successor:** The concept of the in-order successor (the smallest node in the right subtree) is not just for deletion. It's a fundamental property of BSTs and appears in many different types of problems, such as finding the "next" largest element or converting a BST into a sorted linked list.
*   **Visualize Deletion:** When practicing BST deletion, always draw the tree. Physically erase the node and redraw the pointers. This is the only way to truly understand the three cases (0, 1, or 2 children) and how the in-order successor rule preserves the BST property.
*   **Array Implementation:** Remember that any complete binary tree can be efficiently represented in an array. This is the core idea behind the **Heap** data structure, which we will see in the next set of sessions. The parent-child relationship is calculated using indices (`parent=(i-1)/2`, `left=2i+1`, `right=2i+2`).

**🔗Links:** [[DS Sessions 10, 11 & 12 - Searching and Sorting Algorithms]]