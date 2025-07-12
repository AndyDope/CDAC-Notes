## **Session 13: Hash Functions and Hash Tables**

Welcome to Session 13. We know that searching in a [[DS Sessions 10, 11 & 12 - Searching and Sorting Algorithms|sorted array]] is O(log n) and in a [[DS Sessions 4 & 5 - Linked List Data Structures|linked list]] is O(n). But what if we could do better? What if we could achieve O(1), or constant time, lookups on average? This is the promise of the **Hash Table**.

A Hash Table is a data structure that maps **keys** to **values** for highly efficient lookups. It's the underlying structure for Java's `HashMap` and `HashSet`.

---

### **1. Core Concepts: Hash Function and Hash Table**

The magic of a hash table comes from a **hash function**.

*   **Hash Function:** A function that takes an input (the key) and computes a fixed-size integer value from it. This integer is called the **hash code**. A good hash function should produce a wide, uniform distribution of hash codes.
*   **Hash Table:** A data structure, fundamentally an array, where the hash code is used to calculate an **index** where the corresponding value should be stored.

**The Process:**
`Key -> Hash Function -> Hash Code -> Compression Function -> Index`

1.  A key (e.g., a string "John Smith") is passed to a hash function.
2.  The hash function produces a large integer hash code (e.g., `21736182`).
3.  This hash code is often too large to be an array index. A **compression function** (most commonly the modulo operator `%`) is used to scale it down to a valid index within the array's bounds.
    *   `index = hashCode % array_size`
4.  The value associated with the key is stored at that calculated index in the array.

**Visualizing the Ideal Scenario (No Collisions):**

```c
Keys: "apple", "banana", "mango"   Array Size: 10
                                    +---+
hash("apple")  % 10 -> 3            | 0 |
hash("banana") % 10 -> 7            | 1 |
hash("mango")  % 10 -> 1            | 2 | value_for_mango
                                    +---+
                                    | 3 | value_for_apple
                                    +---+
                                    | 4 |
                                    |...|
                                    | 7 | value_for_banana
                                    +---+
                                    |...|
```

In this ideal case, finding "apple" is an O(1) operation: calculate its hash, get the index `3`, and retrieve the value directly.

---

### **2. The Problem: Hash Collisions**

The ideal scenario is rare. A **hash collision** occurs when **two different keys produce the same index** after the compression function.

`Key1 != Key2`, but `hash(Key1) % size == hash(Key2) % size`

Since two values cannot be stored in the same array slot, we need a strategy to handle this. This is called **Collision Resolution**.

---

### **3. Collision Resolution Technique 1: Separate Chaining**

This is one of the most common and effective techniques.

*   **Core Idea:** Instead of the array storing the values directly, each slot (or "bucket") in the array stores a pointer to a [[DS Sessions 4 & 5 - Linked List Data Structures|linked list]]. All keys that hash to the same index are stored in the linked list at that index.

**Visualizing Separate Chaining:**
Let's say `hash("apple") % 10 -> 3` and `hash("grape") % 10 -> 3`.

```c
     Array (Table)
      +---+
    0 | / |  (null pointer)
      +---+
    1 | o |----> [ "mango" | value_M ] -> /
      +---+
    2 | / |
      +---+
    3 | o |----> [ "apple" | value_A ] -> [ "grape" | value_G ] -> /
      +---+
      ...
```
*   **Insertion:** Calculate the index. Go to the linked list at that index and add the new key-value pair.
*   **Search:** Calculate the index. Traverse the linked list at that index, checking each node's key until you find a match.
*   **Performance:** If the hash function is good and distributes keys evenly, the linked lists will be very short. The average lookup time remains close to **O(1)**. In the worst case (all keys hash to the same index), it degrades to **O(n)** as you have to search a single long linked list.

---

### **4. Collision Resolution Technique 2: Open Addressing (Probing)**

In open addressing, all key-value pairs are stored within the array itself. When a collision occurs, we "probe" or search for the next available empty slot in the array according to a specific rule.

##### **a) Linear Probing (In-depth)**

*   **Core Idea:** If the calculated index `h` is occupied, try the next slot `h+1`. If that is occupied, try `h+2`, then `h+3`, and so on, wrapping around the array if necessary, until an empty slot is found.
*   **Probe Sequence:** `h, (h+1)%N, (h+2)%N, (h+3)%N, ...` (where N is the array size).

**Visualizing Insertion with Linear Probing:**
Let's insert "apple" (hashes to index 3), "grape" (hashes to 3), and "melon" (hashes to 4).

1.  **Insert "apple"**: `hash("apple") % 10 = 3`. Slot 3 is empty. Place it there.
    ```c
        |...| 2 | 3:apple | 4 |...|
    ```
2.  **Insert "grape"**: `hash("grape") % 10 = 3`. Slot 3 is occupied.
    *   **Probe 1:** Check index `3+1 = 4`. Slot 4 is empty. Place "grape" there.
    ```c
        |...| 2 | 3:apple | 4:grape |...|
    ```
3.  **Insert "melon"**: `hash("melon") % 10 = 4`. Slot 4 is occupied.
    *   **Probe 1:** Check index `4+1 = 5`. Slot 5 is empty. Place "melon" there.
    ```c
        |...| 2 | 3:apple | 4:grape | 5:melon |...|
    ```

*   **Problem: Primary Clustering.** Linear probing suffers from a phenomenon where long "clusters" of occupied slots form. When a key hashes into this cluster, it has to traverse the entire cluster to find an empty spot, increasing the number of probes and degrading performance.

##### **b) Quadratic Probing (In-depth)**

*   **Core Idea:** To avoid primary clustering, quadratic probing uses a different interval for probing. Instead of checking `h+1, h+2, h+3`, it checks `h+1², h+2², h+3²`, etc.
*   **Probe Sequence:** `h, (h+1²)%N, (h+2²)%N, (h+3²)%N, ...` which is `h, (h+1)%N, (h+4)%N, (h+9)%N, ...`

**Advantage:** It spreads out the probes more effectively, which helps to mitigate the primary clustering issue found in linear probing.
**Disadvantage:** It can create its own, less severe "secondary clustering." Also, if the table is more than half full, it's not guaranteed to find an empty slot even if one exists.

##### **c) Double Hashing**
*   **Core Idea:** Uses a second, different hash function to determine the "step size" for probing.
*   **Probe Sequence:** `h, (h + 1*h₂)%N, (h + 2*h₂)%N, ...` where `h₂` is the result of the second hash function.
*   **Advantage:** This is the most effective open addressing technique at avoiding clustering, as each key gets its own unique probe sequence.

---

### **5. Inserting and Deleting from a Hash Table (Open Addressing)**

**Insertion:**
1.  Calculate the initial index `h` for the key.
2.  If `table[h]` is empty, insert the element there.
3.  If `table[h]` is occupied, follow the probe sequence (linear, quadratic, etc.) until an empty slot is found. Insert the element there.
4.  If the table becomes too full (exceeds its **load factor**), you must perform a **rehashing**: create a new, larger array and re-insert all existing elements into it.

**Deletion (The Tricky Part):**
You **cannot** simply find an element and empty its slot. Why?

*   **Problem:** Consider our linear probing example: `| 3:apple | 4:grape | 5:melon |`. If we delete "grape" from slot 4 and empty it, a later search for "melon" (which hashes to 4) would hit the now-empty slot 4 and incorrectly conclude that "melon" is not in the table. The chain of probes would be broken.

*   **Solution: The `DELETED` Marker.**
    Instead of emptying the slot, we mark it with a special `DELETED` state (sometimes called a tombstone).
    *   **Search:** When searching, if you encounter a `DELETED` slot, you must continue probing as if it were occupied.
    *   **Insertion:** You can insert a new element into the first `DELETED` slot you find.

---

## **Topic Summary & Revision**

*   **Hash Table:** An array-based data structure that provides average O(1) time for insertion, deletion, and search.
*   **Hash Function:** Maps a key to an integer hash code.
*   **Collision:** Occurs when two different keys map to the same array index.
*   **Collision Resolution:**
    *   **Separate Chaining:** Each array slot points to a linked list of collided items. Simple and effective.
    *   **Open Addressing:** Find the next available slot in the array itself.
        *   **Linear Probing:** Checks `h+1, h+2, ...`. Suffers from primary clustering.
        *   **Quadratic Probing:** Checks `h+1, h+4, h+9, ...`. Mitigates primary clustering.
        *   **Double Hashing:** Uses a second hash function for the step size. Best at avoiding clustering.
*   **Deletion in Open Addressing:** Requires a special `DELETED` marker to avoid breaking the probe chain.

---

## **MCQs for Exam Preparation**

1.  **What is the primary purpose of a hash function?**
    - [ ] To sort the data in the most efficient way possible.
    - [ ] To map a key of arbitrary size to a value of a fixed size (an index).
    - [ ] To encrypt data for secure storage.
    - [ ] To guarantee that no two keys will have the same value.
    <br>

2.  **A "hash collision" occurs when:**
    - [ ] Two different keys are stored in the same hash table.
    - [ ] A hash function produces a negative value.
    - [ ] Two different keys produce the same hash index.
    - [ ] The hash table runs out of memory.
    <br>

3.  **In Separate Chaining, where are elements stored when a collision occurs?**
    - [ ] In the next available empty slot in the array.
    - [ ] In a linked list at the collided index.
    - [ ] In a separate, overflow array.
    - [ ] The older element is replaced by the new one.
    <br>

4.  **A hash table of size 10 uses linear probing. The following keys are inserted with the given hash indices: `keyA(hash=3)`, `keyB(hash=4)`, `keyC(hash=3)`. Where will `keyC` be placed?**
    - [ ] At index 3, replacing `keyA`.
    - [ ] At index 4, replacing `keyB`.
    - [ ] At index 5.
    - [ ] It cannot be placed.
    <br>

5.  **What is the main problem associated with Linear Probing?**
    - [ ] It is computationally very expensive.
    - [ ] It requires a second hash function.
    - [ ] It leads to a phenomenon called "primary clustering".
    - [ ] It only works if the table size is a prime number.
    <br>

6.  **Why is it problematic to simply delete an element from a hash table that uses linear probing by emptying its slot?**
    - [ ] It would leave a hole that wastes memory.
    - [ ] It could break the probe chain for other elements that collided earlier.
    - [ ] The hash function would become invalid.
    - [ ] It requires rehashing the entire table, which is slow.
    <br>

7.  **If the probe sequence for a hash table is `h, h+1, h+4, h+9, h+16, ...`, which collision resolution technique is being used?**
    - [ ] Linear Probing
    - [ ] Separate Chaining
    - [ ] Double Hashing
    - [ ] Quadratic Probing
    <br>

8.  **The "load factor" of a hash table is defined as:**
    - [ ] The size of the underlying array.
    - [ ] The ratio of `(number of elements) / (table size)`.
    - [ ] The number of collisions that have occurred.
    - [ ] The speed of the hash function.
    <br>

9.  **Which collision resolution technique is generally considered to be the best at avoiding clustering?**
    - [ ] Linear Probing
    - [ ] Separate Chaining
    - [ ] Quadratic Probing
    - [ ] Double Hashing
    <br>

10. **In the worst-case scenario, what is the time complexity for a search operation in a hash table?**
    - [ ] O(1)
    - [ ] O(log n)
    - [ ] O(n)
    - [ ] O(n²)
    <br>

### **Answer Key**
1.  **B**: ||The goal of a hash function in this context is to take a key (like a string or a custom object) and convert it into an integer that can be used to calculate a table index.||
2.  **C**: ||A collision is specifically the event where two distinct keys compute to the same final index in the hash table's array, creating a conflict for that slot.||
3.  **B**: ||Separate Chaining resolves collisions by treating each array slot as a bucket, which is typically the head of a linked list. All colliding elements are simply added to that list.||
4.  **C**: ||keyA goes to index 3. keyB goes to index 4. When keyC hashes to 3, it finds the slot occupied. Using linear probing, it checks the next slot, h+1, which is index 4. It finds that occupied too. It then checks the next slot, h+2, which is index 5. This slot is empty, so keyC is placed there.||
5.  **C**: ||Primary clustering occurs when keys that collide at one slot then compete for the next available slots, forming long, continuous runs of occupied cells. This significantly increases the average number of probes needed to find an empty slot.||
6.  **B**: ||If an element that was inserted due to a collision is later searched for, the search algorithm must follow the same probe path. If an intermediate slot in that path was emptied, the search would stop prematurely and incorrectly report that the element is not found.||
7.  **D**: ||Quadratic probing checks slots h + i² for i = 1, 2, 3..., which corresponds to the sequence h+1, h+4, h+9, ....||
8.  **B**: ||The load factor (alpha) is a measure of how full the hash table is. It is crucial for determining when to rehash the table to a larger size to maintain its O(1) average performance. A common threshold for rehashing is a load factor of 0.75.||
9.  **D**: ||Double hashing gives each key its own unique probe sequence based on a second hash function, which effectively scatters collided keys across the table and prevents the kind of pile-ups (clustering) seen in linear and quadratic probing.||
10. **C**: ||The worst case for a hash table occurs when all n keys hash to the same index. In Separate Chaining, this creates a single linked list of n elements. In Open Addressing, it requires probing through n slots. In both scenarios, the search degrades to a linear search, which is O(n).||

---

## **Bonus Tips**

*   **Load Factor and Rehashing:** The performance of an open addressing hash table degrades significantly as it gets full. To prevent this, tables are "rehashed" when the load factor exceeds a certain threshold (e.g., 0.5 for quadratic probing, 0.75 for linear probing/chaining). Rehashing involves creating a new, larger array (typically double the size) and re-inserting all existing key-value pairs into the new table. This is an expensive operation but ensures that the average time complexity remains O(1).
*   **Good Hash Functions:** The quality of your hash table depends entirely on the quality of your hash function. A good hash function should be:
    1.  **Fast:** Easy and quick to compute.
    2.  **Deterministic:** The same key must always produce the same hash code.
    3.  **Uniform:** It should distribute keys as evenly as possible across the potential hash codes to minimize collisions.
*   **Java's `hashCode()` and `equals()`:** As we saw in the [[Java Session 18 - Object Class & java.util Package|Java module]], the contract between `hashCode()` and `equals()` is vital for hash tables (`HashMap`, `HashSet`). If you put an object in a `HashMap` and then modify the object in a way that changes its hash code, you will likely not be able to find that object again.
*   **Choosing a Technique:**
    *   **Separate Chaining:** Generally the preferred method. It's simpler to implement (especially deletion), and its performance degrades more gracefully as the load factor increases.
    *   **Open Addressing:** Can be faster in practice due to better cache performance (all data is in one array), but it's more complex to implement correctly (especially deletion) and requires careful management of the load factor.

**🔗Links:** [[DS Sessions 14, 15 & 16 - Graphs and Applications]]