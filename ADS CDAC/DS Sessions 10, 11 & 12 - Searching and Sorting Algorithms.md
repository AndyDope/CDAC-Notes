### **Sessions 10, 11 & 12: Searching and Sorting Algorithms**

Welcome. This block of sessions is dedicated to two essential tasks: finding an item in a collection (**Searching**) and arranging a collection in a specific order (**Sorting**). We will analyze different algorithms for these tasks, paying close attention to their **time and space complexity**. Understanding the trade-offs between these algorithms is crucial for writing efficient and scalable software.

---

### **Part 1: Searching Algorithms**

Searching is the process of finding the location of a specific element in a list.

#### **1. The Sequential Search (Linear Search)**

This is the most basic search algorithm. It sequentially checks each element of the list until a match is found or the whole list has been searched.

*   **How it works:** Start at index 0, compare the element with the target. If it matches, return the index. If not, move to the next element. Repeat until the end of the list.
*   **Requirement:** Works on any list, sorted or unsorted.
*   **Time Complexity:**
    *   **Best Case:** O(1) - The element is the first one in the list.
    *   **Worst Case:** O(n) - The element is the last one, or not in the list at all.
    *   **Average Case:** O(n)

#### **2. The Binary Search**

This is a much more efficient search algorithm, but it has one critical prerequisite: **the list must be sorted.**

*   **How it works:** It uses a "divide and conquer" approach.
    1.  Compare the target value with the middle element of the list.
    2.  If they match, the search is successful.
    3.  If the target is **less than** the middle element, it can only be in the **left half** of the list. Discard the right half.
    4.  If the target is **greater than** the middle element, it can only be in the **right half**. Discard the left half.
    5.  Repeat this process on the remaining sub-list until the element is found or the sub-list is empty.

**Visualizing Binary Search (Target = 23):**

```c
Array: [2, 5, 8, 12, 16, 23, 38, 56, 72, 91]
        L              M                 R      (L=0, R=9, M=4) -> a[4]=16. Target > 16. Search right half.

                   [23, 38, 56, 72, 91]
                    L       M        R         (L=5, R=9, M=7) -> a[7]=56. Target < 56. Search left half.

                   [23, 38, 56]
                    L   M   R                  (L=5, R=6, M=5) -> a[5]=23. Target == 23. Found at index 5.
```

*   **Time Complexity:**
    *   **Best Case:** O(1) - The middle element is the target.
    *   **Worst/Average Case:** **O(log n)** - The search space is halved in each step. This is extremely fast.

> **Quick Question:** Why can't Binary Search be used on an unsorted array?
> **Answer:** Because its core logic relies on the ability to discard half of the search space based on a single comparison (less than or greater than). This is only possible if the elements are in a sorted order.

---

### **Part 2: Sorting Algorithms**

Sorting is the process of arranging elements in a specific order (ascending or descending).

#### **1. Simple Sorting Algorithms - O(n²)**

These algorithms are easy to understand and implement but are inefficient for large datasets.

*   **Selection Sort:**
    *   **Idea:** Find the smallest element in the unsorted part of the list and swap it with the element at the beginning of the unsorted part.
    *   **Process:** In pass 1, find the minimum element in the whole array and swap it to index 0. In pass 2, find the minimum in the rest of the array (from index 1 onwards) and swap it to index 1, and so on.

*   **Bubble Sort:**
    *   **Idea:** Repeatedly step through the list, compare adjacent pairs of elements, and swap them if they are in the wrong order. After each pass, the next largest element "bubbles up" to its correct position at the end.
    *   **Optimization:** Can be optimized to stop early if a pass is completed with no swaps, meaning the array is already sorted.

*   **Insertion Sort:**
    *   **Idea:** Builds the final sorted array one item at a time. It iterates through the input elements and inserts each element into its correct position in the sorted part of the array.
    *   **Analogy:** How you would sort a hand of playing cards.
    *   **Performance:** It is very efficient for small datasets and for datasets that are **already mostly sorted**.

#### **2. Efficient Sorting Algorithms - O(n log n)**

These algorithms use more complex "divide and conquer" strategies to achieve much better performance.

*   **Merge Sort:**
    *   **Idea:** A classic divide and conquer algorithm.
        1.  **Divide:** Recursively split the array into two halves until you have sub-arrays of size 1 (which are inherently sorted).
        2.  **Conquer (Merge):** Merge the sorted sub-arrays back together to produce a larger sorted array. The merging process is the key step.
    *   **Space Complexity:** **O(n)**, as it requires an auxiliary array of the same size for the merging step.
    *   **Stability:** It is a **stable** sort (it preserves the relative order of equal elements).

**Visualizing Merge Sort:**

```c
[38, 27, 43, 3, 9, 82, 10]
        /           \
   [38, 27, 43, 3]  [9, 82, 10]
      /      \          /     \
 [38, 27]  [43, 3]    [9, 82]   [10]
   /    \    /    \
 [38] [27] [43] [3]
   \    /    \    /
  [27, 38]  [3, 43]
      \      /
   [3, 27, 38, 43]   [9, 10, 82]  <-- Merge Step
           \         /
      [3, 9, 10, 27, 38, 43, 82]
```

*   **Quicksort:**
    *   **Idea:** Also a divide and conquer algorithm.
        1.  **Pick a pivot:** Choose an element from the array as the pivot (e.g., the last element).
        2.  **Partition:** Reorder the array so that all elements with values less than the pivot come before it, while all elements with values greater than the pivot come after it. After this partitioning, the pivot is in its final sorted position.
        3.  **Recurse:** Recursively apply the above steps to the sub-array of elements smaller than the pivot and the sub-array of elements greater than the pivot.
    *   **Performance:** **Average case is O(n log n)**, but the **worst case is O(n²)** (occurs when the pivot is consistently the smallest or largest element, e.g., on an already sorted array).
    *   **Space Complexity:** **O(log n)** on average (due to the recursive call stack).
    *   **Stability:** It is an **unstable** sort.

*   **Heapsort:**
    *   **Idea:** Uses a **Heap** data structure (a complete binary tree with specific ordering properties).
        1.  **Build Max-Heap:** Convert the input array into a max-heap, where the largest element is at the root.
        2.  **Sort:** Repeatedly swap the root element (the largest) with the last element of the heap, reduce the heap size by one, and "heapify" the root to restore the max-heap property.
    *   **Performance:** Guaranteed **O(n log n)** in all cases (best, average, worst).
    *   **Space Complexity:** **O(1)** (in-place sort).

---

### **Topic Summary & Revision**

*   **Searching:**
    *   **Linear Search:** O(n), works on any list.
    *   **Binary Search:** O(log n), **requires a sorted list**.
*   **Simple Sorts (O(n²)):**
    *   **Selection Sort:** Find min, swap to front.
    *   **Bubble Sort:** Swap adjacent elements.
    *   **Insertion Sort:** Insert element into sorted portion.
*   **Efficient Sorts (O(n log n)):**
    *   **Merge Sort:** Divide and merge. Stable. Needs O(n) extra space.
    *   **Quicksort:** Pivot and partition. Unstable. O(log n) space. Fast on average, but O(n²) worst case.
    *   **Heapsort:** Uses a heap data structure. In-place O(1) space. Guaranteed O(n log n).

---

### **MCQs for Exam Preparation**

1.  **Binary search algorithm cannot be applied to:**
    - [ ] sorted linked lists
    - [ ] sorted binary trees
    - [ ] sorted arrays
    - [ ] a sorted list of numbers
    <br>

2.  **What is the worst-case time complexity of Quicksort?**
    - [ ] O(n log n)
    - [ ] O(log n)
    - [ ] O(n)
    - [ ] O(n²)
    <br>

3.  **Which sorting algorithm is the most efficient for a list that is already "almost sorted"?**
    - [ ] Quicksort
    - [ ] Merge Sort
    - [ ] Insertion Sort
    - [ ] Selection Sort
    <br>

4.  **A sorting algorithm is considered "stable" if:**
    - [ ] It takes the same amount of time regardless of the input.
    - [ ] It does not require any extra memory space.
    - [ ] It maintains the original relative order of equal elements.
    - [ ] It has a worst-case complexity of O(n log n).
    <br>

5.  **Which sorting algorithm works by repeatedly finding the minimum element from the unsorted part and putting it at the beginning?**
    - [ ] Bubble Sort
    - [ ] Insertion Sort
    - [ ] Selection Sort
    - [ ] Merge Sort
    <br>

6.  **The primary advantage of Merge Sort over Quicksort is that Merge Sort:**
    - [ ] is an in-place sorting algorithm.
    - [ ] has a better average-case time complexity.
    - [ ] has a guaranteed O(n log n) worst-case time complexity.
    - [ ] is easier to implement.
    <br>

7.  **For an array of size `n`, what is the maximum number of comparisons a linear search will perform?**
    - [ ] 1
    - [ ] n/2
    - [ ] n
    - [ ] n+1
    <br>

8.  **The "partition" step is a key part of which sorting algorithm?**
    - [ ] Heapsort
    - [ ] Quicksort
    - [ ] Merge Sort
    - [ ] Radix Sort
    <br>

9.  **Which of the following algorithms requires O(n) auxiliary space in its typical implementation?**
    - [ ] Insertion Sort
    - [ ] Quicksort
    - [ ] Heapsort
    - [ ] Merge Sort
    <br>

10. **In a Bubble Sort implementation, after the first pass through an array of `n` elements, where is the largest element located?**
    - [ ] At index 0
    - [ ] At index n/2
    - [ ] At index n-1 (the last position)
    - [ ] Its position is not guaranteed.
    <br>

**Answer Key**
1.  **A**: ||Binary search requires O(1) random access to the middle element. In a linked list, reaching the middle element requires traversing half the list, which is an O(n) operation, defeating the purpose of binary search.||
2.  **D**: ||While Quicksort's average and best-case complexity is O(n log n), its worst-case occurs when the pivot selection is poor (e.g., always picking the smallest or largest element, as in a pre-sorted array). This degenerates the partitioning and leads to O(n²) complexity.||
3.  **C**: ||Insertion Sort performs very well on nearly sorted data. Its complexity is O(nk) where k is the maximum distance an element is from its sorted position. If data is almost sorted, k is small, and the performance approaches O(n).||
4.  **C**: ||Stability is an important property. For example, if you sort a list of students by name, and then by city, a stable sort will keep the name-based order for students within the same city.||
5.  **C**: ||This is the definition of Selection Sort. It "selects" the minimum element and places it in its correct position in each pass.||
6.  **C**: ||Quicksort can degrade to O(n²) in its worst case, whereas Merge Sort's divide-and-conquer approach guarantees O(n log n) performance in all cases, making it more reliable for mission-critical applications where the worst case must be avoided. However, Quicksort is often faster in practice on average.||
7.  **C**: ||In the worst-case scenario for a linear search, the target element is the very last element, or it is not in the array at all. In both cases, the algorithm must perform n comparisons to check every element.||
8.  **B**: ||The core idea of Quicksort is to pick a pivot and then partition the array around it, placing smaller elements to the left and larger elements to the right.||
9.  **D**: ||The "merge" step of Merge Sort requires an auxiliary array of size n to merge two sorted halves back together. This O(n) space requirement is its main disadvantage compared to Quicksort and Heapsort.||
10. **C**: ||After the first full pass of Bubble Sort, the largest element in the array is guaranteed to have "bubbled up" to the final position in the array, which is index n-1.||

---

### **Bonus Tips**

*   **Interview Hotspot:** Quicksort is one of the most popular interview questions. Be prepared to not only explain how it works but also to write its partitioning logic on a whiteboard. Also, know its worst-case complexity and how to mitigate it (e.g., by choosing a random pivot or the "median-of-three" pivot).
*   **Stability Matters:** Remember that Merge Sort is stable, but Quicksort and Heapsort are not. This is a key distinguishing factor and a common source of questions. If the relative order of equal elements must be preserved, Merge Sort is the go-to choice.
*   **Choosing a Sort:**
    *   For small `n` or nearly sorted data: **Insertion Sort**.
    *   For general-purpose, fast sorting where worst-case is not a major concern: **Quicksort**.
    *   When a guaranteed O(n log n) is required (mission-critical) and space is not an issue: **Merge Sort**.
    *   When a guaranteed O(n log n) is required and you need an in-place sort (O(1) space): **Heapsort**.
*   **Java's `Arrays.sort()`:** In Java, the `Arrays.sort()` method is highly optimized. For primitive types, it uses a dual-pivot Quicksort. For object types, it uses a stable algorithm called Timsort (a hybrid of Merge Sort and Insertion Sort), which performs exceptionally well on real-world data.

**🔗Links:** [[DS Sessions 10, 11 & 12 - Searching and Sorting Algorithms (Continuation)]]