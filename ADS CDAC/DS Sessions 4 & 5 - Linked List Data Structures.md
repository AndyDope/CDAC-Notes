## **Sessions 4 & 5: Linked List Data Structures**

Welcome. In the previous session, we saw that [[DS Sessions 2 & 3 - Algorithms & Data Structures#a) Arrays|arrays]] have a major limitation: they are fixed in size, and inserting or deleting elements is slow. The **Linked List** is a dynamic data structure that solves these problems. It is a linear collection of data elements whose order is not given by their physical placement in memory. Instead, each element points to the next.

---

### **1. Core Concept: Nodes and Pointers**

A linked list is a chain of **nodes**. Each node contains two pieces of information:
1.  **Data:** The actual value being stored.
2.  **Next Pointer:** A reference (or "pointer") to the next node in the sequence.

The first node in the list is called the **head**. The last node's "next" pointer points to **null**, indicating the end of the list.

**Visualizing a Node:**
In Java, we represent a node with a simple class.

```java
class Node {
    int data;     // The data item
    Node next;    // Reference to the next node

    public Node(int data) {
        this.data = data;
        this.next = null; // Initially, it doesn't point to anything
    }
}
```

**Visualizing a Linked List:**
A list storing `10 -> 20 -> 30`. We only need to keep track of the `head` node.

```bash
       +------+      +------+      +------+
head-->| 10 |o|----->| 20 |o|----->| 30 |/|   ( / represents null )
       +------+      +------+      +------+
```

---

### **2. Comparison: Linked List vs. Array**

This is a classic and crucial comparison.

| Feature | Array | Linked List |
| :--- | :--- | :--- |
| **Size** | Fixed (must be defined at creation) | Dynamic (can grow and shrink easily) |
| **Memory** | Contiguous block of memory | Non-contiguous; nodes can be anywhere in memory |
| **Random Access** | **Fast (O(1))**. `array[i]` is a direct calculation. | **Slow (O(n))**. To get the i-th element, you must traverse from the `head`. |
| **Insertion/Deletion** | **Slow (O(n))**. Requires shifting elements. | **Fast (O(1))**. Only requires changing pointers, once you are at the correct location. |
| **Memory Overhead** | Low. No extra space needed. | High. Each node requires extra space for the `next` pointer. |

**When to use a Linked List:** Use a linked list when you have an unpredictable number of items and will be performing frequent insertions and deletions. A classic example is a music playlist where you can easily add or remove songs from any position.

**When to use an Array:** Use an array (or `ArrayList` in Java) when you need fast, index-based access to elements and the number of insertions/deletions is low.

---

### **3. Types of Linked Lists**

##### **a) Singly Linked List**
This is the standard linked list we've discussed, where each node has a single pointer to the **next** node. Traversal is only possible in the forward direction.

**Insertion at the Beginning (O(1)):**
This is very fast.
1. Create a new node.
2. Point the new node's `next` to the current `head`.
3. Update `head` to be the new node.

```bash
// List: 20 -> 30. head points to 20.
// Insert 10 at the beginning.

// 1. Create new_node(10)
    +------+
    | 10 |/|
    +------+

// 2. new_node.next = head
    +------+      +------+
    | 10 |o|----->| 20 |...
    +------+      +------+

// 3. head = new_node
       +------+      +------+
head-->| 10 |o|----->| 20 |...
       +------+      +------+
```

##### **b) Doubly Linked List**
Each node has **two** pointers: one to the `next` node and one to the `previous` node.

**Visualizing a Doubly Linked List Node:**
```bash
     +--------------------+
<----| prev | data | next |---->
     +--------------------+
```
*   **Advantage:** Allows for traversal in both forward and backward directions. Deletion is more efficient because you don't need to keep track of the "previous" node manually when you find the node to delete.
*   **Disadvantage:** Requires more memory due to the extra `previous` pointer.

##### **c) Circular Linked List**
The `next` pointer of the last node points back to the **head** node instead of `null`.

**Visualizing a Circular Linked List:**
```bash
       +------+      +------+      +------+
head-->| 10 |o|----->| 20 |o|----->| 30 |o|-----> (points back to 10)
       +------+      +------+      +------+      |
         ^                                       |
         |_______________________________________|
```
*   **Advantage:** You can start traversing from any node and reach any other node in the list. Useful for applications that require continuous looping, like a round-robin scheduler.

---

### **4. Implementing a Stack and Queue with Linked Lists**

Linked lists provide a natural and efficient way to implement the [[DS Sessions 2 & 3 - Algorithms & Data Structures#b) Stacks (LIFO)|Stack]] and [[DS Sessions 2 & 3 - Algorithms & Data Structures#c) Queues (FIFO)|Queue]] ADTs.

##### **a) Stack Implementation**
*   **`push(item)`:** Corresponds to **inserting at the beginning** of the list (O(1)). The new node becomes the new `head`.
*   **`pop()`:** Corresponds to **deleting from the beginning** of the list (O(1)). The `head` is moved to the next node.

This is more efficient than an array-based stack because it never runs out of space (no overflow) and requires no resizing.

##### **b) Queue Implementation**
For an efficient queue, we need to keep track of both the `front` (head) and `rear` (tail) of the list.
*   **`enqueue(item)`:** Corresponds to **inserting at the end** of the list (O(1)). The new node becomes the new `rear`.
*   **`dequeue()`:** Corresponds to **deleting from the beginning** of the list (O(1)). The `front` is moved to the next node.

This avoids the "shuffling" problem of an array-based queue and the complexity of a circular array.

---

## **Topic Summary & Revision**

*   **Core Idea:** A linked list is a chain of nodes, where each node contains data and a pointer to the next node.
*   **Array vs. Linked List:** Array has fast O(1) access but slow O(n) insertion/deletion. Linked List has slow O(n) access but fast O(1) insertion/deletion.
*   **Singly Linked List:** Traversal in one direction.
*   **Doubly Linked List:** Has `next` and `previous` pointers. Traversal in both directions.
*   **Circular Linked List:** The last node points back to the `head`.
*   **Implementations:** Linked lists are an excellent choice for implementing dynamic Stacks and Queues, offering O(1) performance for their core operations.

---

## **MCQs for Exam Preparation**

1.  **What is the primary advantage of a linked list over an array?**
    - [ ] Faster access to elements by index.
    - [ ] Lower memory overhead per element.
    - [ ] Dynamic size and efficient insertion/deletion.
    - [ ] Elements are stored in contiguous memory locations.
    <br>

2.  **To access the 6th element in a singly linked list, what is the time complexity?**
    - [ ] O(1)
    - [ ] O(log n)
    - [ ] O(n)
    - [ ] O(n log n)
    <br>

3.  **In a circular linked list, what does the `next` pointer of the last node point to?**
    - [ ] null
    - [ ] The first node (head).
    - [ ] The node before it (previous node).
    - [ ] A special sentinel node.
    <br>

4.  **You are implementing a queue using a singly linked list. For O(1) enqueue and dequeue operations, you should maintain pointers to which nodes?**
    - [ ] Only the front node.
    - [ ] Only the rear node.
    - [ ] Both the front and the rear nodes.
    - [ ] The middle node.
    <br>

5.  **Which of the following operations is generally slower in a doubly linked list compared to a singly linked list?**
    - [ ] Deleting a given node.
    - [ ] Inserting a new node at the beginning.
    - [ ] Traversing the list backwards.
    - [ ] None of the above; all operations are of similar or better complexity.
    <br>

6.  **What condition indicates that a singly linked list with a `head` pointer is empty?**
    - [ ] `head.next == null`
    - [ ] `head.data == 0`
    - [ ] `head == null`
    - [ ] `head.next == head`
    <br>

7.  **If you want to insert a new node *before* a given node in a singly linked list, what is required?**
    - [ ] Only a pointer to the given node.
    - [ ] Only a pointer to the head of the list.
    - [ ] A pointer to the node *previous* to the given node.
    - [ ] The data of the next node.
    <br>

8.  **Which data structure is most suitable for implementing a playlist where users can easily add, remove, and reorder songs anywhere in the list?**
    - [ ] An array.
    - [ ] A stack.
    - [ ] A queue.
    - [ ] A doubly linked list.
    <br>

9.  **A memory leak is most likely to occur in a manually managed linked list implementation due to:**
    - [ ] Failing to set the `next` pointer of the last node to `null`.
    - [ ] Storing duplicate data in the list.
    - [ ] Deleting a node but not freeing the memory it occupied, while losing all references to it.
    - [ ] Traversing the list too many times.
    <br>

10. **In a singly linked list, you have a pointer to the head and the tail. What is the time complexity to insert a new node at the very end of the list?**
    - [ ] O(1)
    - [ ] O(log n)
    - [ ] O(n)
    - [ ] O(n log n)
    <br>

**Answer Key**
1.  **C**: ||Arrays have a fixed size allocated at creation. Linked lists can grow and shrink as needed, and inserting or deleting a node is an efficient O(1) operation once the position is found, as it only involves redirecting pointers.||
2.  **C**: ||Unlike an array, you cannot jump directly to an index in a linked list. You must start from the head and traverse through each of the first 5 nodes to reach the 6th one. In the worst case, you have to traverse all n nodes. This is linear time, O(n).||
3.  **B**: ||This is the defining feature of a circular linked list. The chain of nodes forms a loop by having the last node point back to the first (head) node.||
4.  **C**: ||To dequeue in O(1), you need a pointer to the front to remove the first element. To enqueue in O(1), you need a pointer to the rear to add a new element without traversing the whole list to find the end.||
5.  **D**: ||Insertion, deletion, and traversal are all either the same or more efficient in a doubly linked list. Specifically, deleting a given node is more efficient because you already have the previous pointer and don't need to find it by traversing from the head. Backward traversal is possible, unlike in a singly linked list.||
6.  **C**: ||An empty list has no nodes. The head pointer, which is supposed to point to the first node, will therefore be null.||
7.  **C**: ||To insert before node X, you must change the next pointer of the node that comes before X (let's call it P). You need to make P's next point to the new node, and the new node's next point to X. Without a pointer to P, this is impossible in a singly linked list without traversing from the head.||
8.  **D**: ||A playlist requires frequent insertions and deletions at arbitrary positions. A doubly linked list is perfect for this, as it provides O(1) insertion/deletion if you have a reference to a song, and easy reordering by manipulating next and previous pointers.||
9.  **C**: ||This question relates to languages with manual memory management like C/C++. In Java, this is handled by the|| [[Java Session 12 - Garbage collection|Garbage Collector]]||. A memory leak occurs when memory is allocated for a node, but after removing it from the list's pointer chain, the program fails to free or delete that memory block. The program no longer has a reference to it, so it cannot be freed, but the system still considers it "in use."||
10. **A**: ||Because you have a pointer to the tail (the last node), you can perform the insertion in O(1) time. The steps are: 1. tail.next = newNode. 2. tail = newNode. This doesn't require traversing the list from the head.||

---

## **Bonus Tips**

*   **The "Runner" Technique:** A very common interview problem is "find the middle element of a linked list in one pass." The solution is the "slow and fast pointer" or "runner" technique. You have one pointer (`slow`) that moves one step at a time, and another (`fast`) that moves two steps at a time. When the `fast` pointer reaches the end of the list, the `slow` pointer will be at the middle.
*   **Dummy Head Node:** When implementing linked list operations (especially deletion), the code to handle the case where you modify the `head` node is often different from other nodes. To simplify this, you can use a "dummy" or "sentinel" head node that sits before the actual first element. This way, every insertion/deletion happens *after* some node, and you don't need special `if (node == head)` checks.
*   **Visualize, Visualize, Visualize:** You cannot solve linked list problems in your head. Always draw the boxes and arrows on a piece of paper. Trace how the `head`, `next`, and `previous` pointers change for each step of your algorithm. This is the single most effective way to avoid bugs.
*   **Null Pointer Exception:** The most common bug when working with linked lists is the `NullPointerException`. This happens when you try to access a property of a `null` object (e.g., `currentNode.next` when `currentNode` is already `null`). Always check for `null` before trying to access a pointer's properties.

**🔗Links:** [[DS Session 6 - Recursion]]