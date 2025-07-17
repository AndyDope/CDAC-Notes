### **In-Depth Guide to Sorting Algorithms**

This guide provides a deeper look into the mechanics of five fundamental sorting algorithms. For each, we will visualize the step-by-step process to build a strong mental model of how they work.

**🔗 Back to [[DS Sessions 10, 11 & 12 - Searching and Sorting Algorithms]]**

---

### **1. Selection Sort**

*   **Core Idea:** Repeatedly find the minimum element in the unsorted portion of the array and swap it with the first element of that unsorted portion.
*   **Analogy:** Picking the lightest person from a group and making them stand at the front. Then, picking the next lightest from the rest and making them stand in the second position, and so on.
*   **Complexity:** O(n²) in all cases (Best, Average, Worst).
*   **In-place:** Yes (O(1) extra space).
*   **Stable:** No.

**Step-by-Step Visualization:**
Let's sort the array: `[64, 25, 12, 22, 11]`

**Pass 1:**
*   **Unsorted part:** `[64, 25, 12, 22, 11]`
*   Find the minimum element: **11** (at index 4).
*   Swap it with the first element of the unsorted part (64 at index 0).
*   **Array:** `[11, 25, 12, 22, 64]`
    *   `[Sorted | Unsorted]` -> `[11 | 25, 12, 22, 64]`

**Pass 2:**
*   **Unsorted part:** `[25, 12, 22, 64]`
*   Find the minimum element: **12** (at index 2).
*   Swap it with the first element of the unsorted part (25 at index 1).
*   **Array:** `[11, 12, 25, 22, 64]`
    *   `[Sorted | Unsorted]` -> `[11, 12 | 25, 22, 64]`

**Pass 3:**
*   **Unsorted part:** `[25, 22, 64]`
*   Find the minimum element: **22**.
*   Swap with 25.
*   **Array:** `[11, 12, 22, 25, 64]`
    *   `[Sorted | Unsorted]` -> `[11, 12, 22 | 25, 64]`

And so on. The key takeaway is that it performs a maximum of `n-1` swaps, which is good, but the number of comparisons is always O(n²), which makes it slow.

---

### **2. Bubble Sort**

*   **Core Idea:** Repeatedly step through the list, compare adjacent elements, and swap them if they are in the wrong order. The largest elements "bubble" to the end of the array.
*   **Complexity:** O(n²) in average and worst cases. O(n) in the best case (if the array is already sorted and we use an optimization).
*   **In-place:** Yes.
*   **Stable:** Yes.

**Step-by-Step Visualization:**
Let's sort the array: `[5, 1, 4, 2, 8]`

**Pass 1:**
*   `[**5, 1**, 4, 2, 8]` -> Swap. `[1, **5, 4**, 2, 8]` -> Swap.
*   `[1, 4, **5, 2**, 8]` -> Swap. `[1, 4, 2, **5, 8**]` -> No Swap.
*   **End of Pass 1:** `[1, 4, 2, 5, 8]`. The largest element, 8, is now in its correct final position.

**Pass 2:** (Now we only need to sort up to the second-to-last element)
*   `[**1, 4**, 2, 5, 8]` -> No Swap. `[1, **4, 2**, 5, 8]` -> Swap.
*   `[1, 2, **4, 5**, 8]` -> No Swap.
*   **End of Pass 2:** `[1, 2, 4, 5, 8]`. The second largest element, 5, is now in its correct position.

**Optimized Approach:**
We can add a boolean flag. If a full pass is completed with no swaps made, it means the array is already sorted, and we can break out of the loop early. This gives Bubble Sort a best-case complexity of O(n).

---

### **3. Insertion Sort**

*   **Core Idea:** Builds the final sorted array one item at a time. It takes an element from the unsorted part and "inserts" it into its correct position within the already sorted part.
*   **Analogy:** Sorting a hand of playing cards as you pick them up.
*   **Complexity:** O(n²) in average and worst cases. O(n) in the best case.
*   **In-place:** Yes.
*   **Stable:** Yes.
*   **Optimized Approach:** Very efficient for small lists and lists that are already mostly sorted. This is why it's used as a component in more advanced hybrid sorts like Timsort.

**Step-by-Step Visualization:**
Let's sort the array: `[12, 11, 13, 5, 6]`

**Initial:** `[12 | 11, 13, 5, 6]` (Sorted part is just `[12]`)

**Pass 1 (pick 11):**
*   Compare 11 with 12. 11 < 12. Shift 12 to the right. Insert 11.
*   **Array:** `[11, 12 | 13, 5, 6]`

**Pass 2 (pick 13):**
*   Compare 13 with 12. 13 > 12. No shift needed. 13 is in its correct place.
*   **Array:** `[11, 12, 13 | 5, 6]`

**Pass 3 (pick 5):**
*   Compare 5 with 13. 5 < 13. Shift 13 right.
*   Compare 5 with 12. 5 < 12. Shift 12 right.
*   Compare 5 with 11. 5 < 11. Shift 11 right.
*   Insert 5 at the beginning.
*   **Array:** `[5, 11, 12, 13 | 6]`

---

### **4. Merge Sort (Emphasis)**

^a79978

*   **Core Idea:** A "Divide and Conquer" algorithm. It recursively divides the array into two halves, sorts them independently, and then merges the two sorted halves back into a single sorted array.
*   **Complexity:** **O(n log n)** in all cases (Best, Average, Worst). This is its greatest strength.
*   **In-place:** No. It requires O(n) auxiliary space for the temporary array used in the merge step.
*   **Stable:** Yes.
*   **Optimized Approach:** It's the algorithm of choice when a guaranteed worst-case performance and stability are required.

**Step-by-Step Visualization:**
Let's sort `[38, 27, 43, 3, 9, 82, 10, 5]`

**Divide Phase (Recursive Calls):**
The array is recursively split.

```bash
                  [38, 27, 43, 3, 9, 82, 10, 5]
                                |
             -----------------------------------------
            |                                         |
    [38, 27, 43, 3]                                [9, 82, 10, 5]
            |                                         |
      ---------------                           ---------------
     |               |                         |               |
 [38, 27]         [43, 3]                   [9, 82]         [10, 5]
     |               |                         |               |
  -------         -------                   -------         -------
 |       |       |       |                 |       |       |       |
[38]   [27]     [43]    [3]               [9]     [82]    [10]    [5]
```

**Conquer Phase (Merging):**
Now, we merge the sub-arrays back up. This is where the sorting happens.

```bash
[27, 38]         [3, 43]                   [9, 82]         [5, 10]
     |_______________|                         |_______________|
            |                                         |
   [3, 27, 38, 43]                                [5, 9, 10, 82]
            |_________________________________________|
                                |
                   [3, 5, 9, 10, 27, 38, 43, 82]
```
The merge step is crucial. It takes two sorted arrays and iterates through them with two pointers, picking the smaller element at each step to place into a temporary array.

**Pseudocode:**

The main function mergeSort handles the division.

**Generated pseudocode**

```python
procedure mergeSort(array, begin, end)
  // Base Case: If the array has 0 or 1 elements, it's already sorted.
  if begin >= end then
    return

  // 1. Divide: Find the middle point to divide the array into two halves.
  mid = begin + (end - begin) / 2

  // 2. Conquer: Recursively call mergeSort for both halves.
  mergeSort(array, begin, mid)
  mergeSort(array, mid + 1, end)

  // 3. Combine: Merge the two sorted halves.
  merge(array, begin, mid, end)
end procedure
```

The helper function merge does the heavy lifting.

**Generated pseudocode**

```python
procedure merge(array, left, mid, right)
  // Create temporary arrays to hold the two halves.
  left_half_size = mid - left + 1
  right_half_size = right - mid
  
  create array L of size left_half_size
  create array R of size right_half_size
  
  // Copy data to temporary arrays L[] and R[].
  for i from 0 to left_half_size-1
    L[i] = array[left + i]
  for j from 0 to right_half_size-1
    R[j] = array[mid + 1 + j]
    
  // Merge the temporary arrays back into the original array.
  // Initialize pointers for the two halves and the main array.
  i = 0  // pointer for L[]
  j = 0  // pointer for R[]
  k = left // pointer for merged array (the original array)
  
  // Compare elements from L and R and place the smaller one into the main array.
  while i < left_half_size and j < right_half_size
    if L[i] <= R[j] then
      array[k] = L[i]
      i = i + 1
    else
      array[k] = R[j]
      j = j + 1
    k = k + 1
    
  // Copy any remaining elements of L[] (if any).
  while i < left_half_size
    array[k] = L[i]
    i = i + 1
    k = k + 1
    
  // Copy any remaining elements of R[] (if any).
  while j < right_half_size
    array[k] = R[j]
    j = j + 1
    k = k + 1
end procedure
```

---
### **5. Quicksort (Emphasis)**

*   **Core Idea:** Also a "Divide and Conquer" algorithm. It works by picking a "pivot" element and partitioning the other elements into two sub-arrays, according to whether they are less than or greater than the pivot. The pivot is now in its final sorted position. The sub-arrays are then sorted recursively.
*   **Complexity:** **O(n log n)** on average and best case. **O(n²)** in the worst case.
*   **In-place:** Yes (O(log n) space is used for the recursion call stack).
*   **Stable:** No.
*   **Optimized Approach:** In practice, Quicksort is often faster than Merge Sort due to better cache performance and no need for extra memory allocation. The key optimization is **choosing a good pivot**. Instead of picking the first or last element, using a **random pivot** or the **"median-of-three"** (the median of the first, middle, and last elements) can help avoid the worst-case scenario.

**Step-by-Step Visualization (Lomuto Partition Scheme):**
Let's sort `[7, 2, 1, 6, 8, 5, 3, 4]` using the last element as the pivot.

**Initial Call:** `quicksort(array, low=0, high=7)`. Pivot = 4.

**Partition Step:**
*   `[7, 2, 1, 6, 8, 5, 3, 4]` Pivot=4
*   We maintain a pointer `i`. We iterate with `j` from low to high-1. If `array[j]` is less than the pivot, we swap it with `array[i]` and increment `i`.
*   After loop: `[2, 1, 3, **6, 8, 5, 7, 4**]` (Elements `<4` are on the left of bold). `i` is at index 3.
*   Swap pivot (4) with `array[i]` (6).
*   **Array after 1st partition:** `[2, 1, 3, **4**, 8, 5, 7, 6]`.
*   The pivot **4** is now in its final sorted position.

**Recursive Calls:**
*   Now, call `quicksort` on the left sub-array: `[2, 1, 3]`
*   And call `quicksort` on the right sub-array: `[8, 5, 7, 6]`

This process continues until the sub-arrays have a size of 1 or 0.

Quicksort also follows "Divide and Conquer," but its structure is different. The key work happens in the partition function, which rearranges the array.

**Pseudocode:**

The main quickSort function.

**Generated pseudocode**

```python
procedure quickSort(array, low, high)
  // Base Case: If there are 1 or 0 elements, it's sorted.
  if low < high then
    // 1. Partition the array and get the index of the pivot.
    // The pivot is now in its correct, final sorted position.
    pivot_index = partition(array, low, high)
    
    // 2. Conquer: Recursively sort the sub-arrays.
    // Sort elements before the pivot.
    quickSort(array, low, pivot_index - 1)
    // Sort elements after the pivot.
    quickSort(array, pivot_index + 1, high)
end procedure
```

The partition function (using the common Lomuto scheme).

**Generated pseudocode**

```python
procedure partition(array, low, high)
  // 1. Choose the last element as the pivot.
  pivot = array[high]
  
  // 2. `i` is the index of the last element that was smaller than the pivot.
  // It acts as the boundary of the "less than pivot" section.
  i = low - 1
  
  // 3. Iterate through the array (from `low` to `high-1`).
  for j from low to high - 1
    // If the current element is smaller than or equal to the pivot...
    if array[j] <= pivot then
      // ...increment the boundary `i` and swap the current element `array[j]`
      // into the "less than pivot" section.
      i = i + 1
      swap(array[i], array[j])
      
  // 4. At the end, swap the pivot (at `array[high]`) with the element
  // just after the "less than pivot" section boundary (`array[i+1]`).
  // This places the pivot in its final sorted position.
  swap(array[i + 1], array[high])
  
  // 5. Return the final index of the pivot.
  return (i + 1)
end procedure
```

**In-Depth Visualization of the partition Step:**

Let's partition the array [7, 2, 1, 6, 8, 5, 3, 4] with low=0, high=7.

- **Pivot:** array[7] which is **4**.
    
- **Initialize i = -1**.
    

**Iteration j=0 to 6:**

| j   | array[j] | Condition array[j] <= pivot(4)? | Action                              | Array State                          | i   |
| --- | -------- | ------------------------------- | ----------------------------------- | ------------------------------------ | --- |
| -   | -        | -                               | Initial                             | [7, 2, 1, 6, 8, 5, 3, **4**]         | -1  |
| 0   | 7        | 7 <= 4 is **False**             | Do nothing.                         | [7, 2, 1, 6, 8, 5, 3, **4**]         | -1  |
| 1   | 2        | 2 <= 4 is **True**              | i++ (i=0). swap(array[0], array[1]) | [**2**, **7**, 1, 6, 8, 5, 3, **4**] | 0   |
| 2   | 1        | 1 <= 4 is **True**              | i++ (i=1). swap(array[1], array[2]) | [2, **1**, **7**, 6, 8, 5, 3, **4**] | 1   |
| 3   | 6        | 6 <= 4 is **False**             | Do nothing.                         | [2, 1, 7, 6, 8, 5, 3, **4**]         | 1   |
| 4   | 8        | 8 <= 4 is **False**             | Do nothing.                         | [2, 1, 7, 6, 8, 5, 3, **4**]         | 1   |
| 5   | 5        | 5 <= 4 is **False**             | Do nothing.                         | [2, 1, 7, 6, 8, 5, 3, **4**]         | 1   |
| 6   | 3        | 3 <= 4 is **True**              | i++ (i=2). swap(array[2], array[6]) | [2, 1, **3**, 6, 8, 5, **7**, **4**] | 2   |

**End of Loop:** The loop finishes. i is 2.

- The section from low to i ([2, 1, 3]) contains all elements less than or equal to the pivot.
    

**Final Swap:**

- Swap the pivot (array[high]) with the element at i+1 (array[3]).
    
- swap(array[7], array[3]) -> swap(4, 6)
    
- **Final Partitioned Array:** [2, 1, 3, **4**, 8, 5, 7, 6]
    
- **Return pivot index:** i+1 = 3.
    

Now, the quickSort function will be called recursively for the left part [2, 1, 3] (from index 0 to 2) and the right part [8, 5, 7, 6] (from index 4 to 7).


---

## **Bonus Tips**

*   **Hybrid Sorts:** Modern real-world sorting functions (like Java's `Arrays.sort`) are often **hybrid**. For example, they might use Quicksort for large partitions, but when a sub-array becomes small enough (e.g., < 16 elements), they switch to **Insertion Sort**, because it's faster for small, nearly sorted lists and has less overhead.
*   **Pivot Selection is Everything:** The performance of Quicksort lives and dies by its pivot selection strategy. A naive strategy (always picking the first or last element) makes it vulnerable to its O(n²) worst case on sorted or reverse-sorted data. Using a random or median-of-three pivot makes this worst-case scenario astronomically unlikely.
*   **External Sorting:** What if the data to be sorted is too large to fit into memory (e.g., a 100GB file)? This requires **External Sorting**. The typical approach is a modified Merge Sort. You read chunks of the data that fit into memory, sort them using an internal sort like Quicksort, save these sorted chunks to disk, and then perform a multi-way merge on the sorted chunks.
*   **Visualizing the Difference:**
    *   **Merge Sort:** The "hard work" is done during the **merge** phase, after the array has been broken all the way down.
    *   **Quicksort:** The "hard work" is done during the **partition** phase, before the recursive calls are made.

**🔗Links:** [[DS Session 13 - Hash Functions and Hash Tables]]