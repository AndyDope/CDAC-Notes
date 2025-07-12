## **Sessions 17, 18 & 19: Algorithm Design Strategies**

Welcome to the final sessions on algorithms. So far, we have seen specific algorithms for specific tasks. Now, we will study **Algorithm Design Strategies**, which are high-level approaches or paradigms for designing solutions to a wide range of problems. We will cover the Greedy approach, the Divide and Conquer strategy we've already seen, and then provide a deep dive into Dynamic Programming.

---

### **1. Greedy Method**

*   **Core Idea:** At each step of the algorithm, make a choice that is **locally optimal** (the best choice at the current moment) in the hope that these local choices will lead to a **globally optimal** solution for the entire problem.
*   **Analogy:** Giving change. To give change for 48 cents, you greedily pick the largest coin possible at each step: a 25c coin, then a 10c coin, then a 10c coin, then a 1c coin, then 1c, then 1c. In this case, the greedy approach works and gives the optimal solution.
*   **When it works:** Greedy algorithms are simple and fast, but they don't work for all problems. They are only successful for problems that have the **greedy choice property** (a locally optimal choice leads to a globally optimal solution) and **optimal substructure** (an optimal solution to the problem contains optimal solutions to its subproblems).

**Classic Examples:**
*   **[[DS Sessions 14, 15 & 16 - Graphs and Applications#a) Dijkstra's Algorithm (Single-Source Shortest Path)|Dijkstra's Algorithm]]**: Greedily picks the unvisited vertex with the smallest known distance.
*   **[[DS Sessions 14, 15 & 16 - Graphs and Applications#a) Prim's Algorithm|Prim's Algorithm]]**: Greedily grows an MST by picking the cheapest edge connecting the tree to a new vertex.
*   **[[DS Sessions 14, 15 & 16 - Graphs and Applications#b) Kruskal's Algorithm|Kruskal's Algorithm]]**: Greedily picks the cheapest available edge in the entire graph that doesn't form a cycle.
*   **Activity Selection Problem / Interval Scheduling:** Given a set of activities with start and end times, select the maximum number of non-overlapping activities. The greedy strategy is to always pick the next activity that **finishes earliest**.

---

### **2. Divide and Conquer**

*   **Core Idea:** A three-step process for solving problems.
    1.  **Divide:** Break the original problem into smaller, self-similar sub-problems.
    2.  **Conquer:** Solve the sub-problems recursively. If the sub-problems are small enough (the base case), solve them directly.
    3.  **Combine:** Merge the solutions of the sub-problems to create a solution for the original problem.

*   **Analogy:** Searching for a name in a physical phone book. You don't start at 'A'. You open to the middle (Divide). You see you're in the 'M' section and your target 'Smith' is later. You discard the first half and repeat the process on the second half (Conquer). The "Combine" step is trivial here as you just find the name.

**Classic Examples:**
*   **[[DS Sessions 10, 11 & 12 - Searching and Sorting Algorithms#2. The Binary Search|Binary Search]]**: Divides the array in half at each step.
*   **[[DS Sessions 10, 11 & 12 - Searching and Sorting Algorithms (Continuation)#4. Merge Sort (Emphasis)|Merge Sort]]**: Divides the array, recursively sorts the halves, and then combines them by merging.
*   **[[DS Sessions 10, 11 & 12 - Searching and Sorting Algorithms (Continuation)#5. Quicksort (Emphasis)|Quicksort]]**: Divides the array by partitioning around a pivot and recursively sorts the sub-arrays.

---

### **3. Dynamic Programming (DP) - In-depth**

Dynamic Programming is not about "dynamic" code; it's a powerful technique for solving optimization problems by breaking them down into simpler sub-problems and **storing the results of these sub-problems** to avoid re-computation.

It is used for problems that exhibit two key properties:

1.  **Overlapping Sub-problems:** A naive recursive solution would solve the same sub-problems over and over again.
2.  **Optimal Substructure:** The optimal solution to the overall problem can be constructed from the optimal solutions of its sub-problems.

**The Fibonacci Sequence: The "Hello World" of DP**
Let's consider the problem of finding the nth Fibonacci number.
`fib(n) = fib(n-1) + fib(n-2)` with base cases `fib(0)=0`, `fib(1)=1`.

**a) The Naive Recursive Solution:**
```java
int fib(int n) {
    if (n <= 1) return n;
    return fib(n-1) + fib(n-2);
}
```
This solution is elegant but horribly inefficient. Let's visualize the calls for `fib(5)`:

**Recursive Call Tree for `fib(5)`:**

```c
                        fib(5)
                      /        \
                 fib(4)          fib(3)
                /      \        /      \
            fib(3)   fib(2)    fib(2)   fib(1)
           /      \  /     \   /      \
       fib(2) fib(1) fib(1) fib(0) fib(1) fib(0)
      /      \
  fib(1)   fib(0)
```
Notice that `fib(3)` is calculated twice, `fib(2)` is calculated three times, and so on. The work is redundant, leading to an exponential time complexity of O(2ⁿ).

**b) The DP Solution: Memoization (Top-Down Approach)**

*   **Core Idea:** We still use recursion, but we store the result of each sub-problem in a cache (like an array or map). Before computing a result, we check if it's already in the cache.
*   **This is the "storing results" part of DP.**

**Pseudocode for Memoization:**
```c
// Initialize a cache array with a special value (e.g., -1)
create array cache of size n+1

procedure fib_memo(n, cache)
  // Base Case
  if n <= 1 then
    return n
    
  // Before computing, check if the result is already in the cache.
  if cache[n] is not -1 then
    return cache[n] // Return the stored result.
  
  // If not in cache, compute it, store it, and then return it.
  result = fib_memo(n-1, cache) + fib_memo(n-2, cache)
  cache[n] = result
  return result
end procedure
```
Now, `fib(3)` will be computed only once. The second time it's needed, the value is retrieved from the cache in O(1) time. This brings the complexity down to **O(n)** because each `fib(i)` from `0` to `n` is computed exactly once.

**c) The DP Solution: Tabulation (Bottom-Up Approach)**

*   **Core Idea:** Instead of starting from `n` and going down (top-down), we solve the problem from the smallest sub-problem up to the original problem. We build a "table" of solutions.
*   **This completely avoids recursion.**

**Pseudocode for Tabulation:**
```c
procedure fib_tab(n)
  // Create a table (array) to store results.
  create array table of size n+1
  
  // Fill in the base cases.
  table[0] = 0
  table[1] = 1
  
  // Fill the table iteratively from the bottom up.
  for i from 2 to n
    table[i] = table[i-1] + table[i-2]
    
  // The final answer is at the end of the table.
  return table[n]
end procedure
```

**Visualizing Tabulation for `fib(5)`:**
1.  **Initialize table:** `[ 0, 1, _, _, _, _ ]`
2.  **i=2:** `table[2] = table[1] + table[0] = 1+0=1`. Table: `[0, 1, 1, _, _, _]`
3.  **i=3:** `table[3] = table[2] + table[1] = 1+1=2`. Table: `[0, 1, 1, 2, _, _]`
4.  **i=4:** `table[4] = table[3] + table[2] = 2+1=3`. Table: `[0, 1, 1, 2, 3, _]`
5.  **i=5:** `table[5] = table[4] + table[3] = 3+2=5`. Table: `[0, 1, 1, 2, 3, 5]`
6.  **Return `table[5]` which is 5.**

This approach is also **O(n)** time and uses O(n) space for the table. It is often slightly more efficient in practice because it avoids the overhead of recursive function calls.

---

### **Topic Summary & Revision**

*   **Greedy Method:** Makes locally optimal choices. Fast and simple but only works for specific problem types (e.g., Dijkstra's, Prim's, Kruskal's).
*   **Divide and Conquer:** Break, solve, combine. Excellent for problems that can be neatly split (e.g., Merge Sort, Binary Search).
*   **Dynamic Programming (DP):** Used for optimization problems with **overlapping sub-problems** and **optimal substructure**.
    *   **Core Idea:** Solve sub-problems and **store their results** to avoid re-computation.
    *   **Memoization (Top-Down):** Use recursion but store results in a cache. Check the cache before computing.
    *   **Tabulation (Bottom-Up):** Fill a table with solutions to sub-problems iteratively, starting from the base cases. Avoids recursion.

---

### **MCQs for Exam Preparation**

1.  **Which algorithmic paradigm does Kruskal's algorithm for finding a Minimum Spanning Tree follow?**
    - [ ] Divide and Conquer
    - [ ] Dynamic Programming
    - [ ] Backtracking
    - [ ] Greedy Method
    <br>

2.  **Which of the following is NOT a characteristic property of problems solvable with Dynamic Programming?**
    - [ ] Overlapping Sub-problems
    - [ ] Optimal Substructure
    - [ ] Greedy Choice Property
    - [ ] Can be broken down into smaller sub-problems.
    <br>

3.  **What is the primary advantage of the memoized (top-down DP) approach over a naive recursive approach for the Fibonacci sequence?**
    - [ ] It uses less memory on the call stack.
    - [ ] It avoids the re-computation of the same sub-problems.
    - [ ] It does not require a base case.
    - [ ] It is always faster than the iterative tabulation approach.
    <br>

4.  **Binary Search is a classic example of which algorithm design strategy?**
    - [ ] Greedy Method
    - [ ] Divide and Conquer
    - [ ] Dynamic Programming
    - [ ] Brute Force
    <br>

5.  **The tabulation (bottom-up) approach to Dynamic Programming primarily avoids the use of what?**
    - [ ] Loops
    - [ ] Arrays
    - [ ] Recursion
    - [ ] Conditional statements
    <br>

6.  **For which of the following problems would a greedy algorithm NOT provide an optimal solution?**
    - [ ] The 0/1 Knapsack problem (items cannot be broken).
    - [ ] The Fractional Knapsack problem (items can be broken).
    - [ ] Finding the shortest path in an unweighted graph (using BFS).
    - [ ] Making change using standard US coins (1, 5, 10, 25 cents).
    <br>

7.  **What is the time complexity of a DP solution (either memoization or tabulation) for finding the nth Fibonacci number?**
    - [ ] O(1)
    - [ ] O(log n)
    - [ ] O(n)
    - [ ] O(2ⁿ)
    <br>

8.  **The "combine" step is the most complex part of which algorithm?**
    - [ ] Quicksort
    - [ ] Merge Sort
    - [ ] Binary Search
    - [ ] Selection Sort
    <br>

9.  **A problem can be solved by breaking it into smaller sub-problems. If the solutions to these sub-problems do NOT affect each other and are not reused, which paradigm is most suitable?**
    - [ ] Greedy Method
    - [ ] Dynamic Programming
    - [ ] Divide and Conquer
    - [ ] This cannot be solved by any standard paradigm.
    <br>

10. **What is the primary trade-off when using memoization in a recursive algorithm?**
    - [ ] It increases time complexity but simplifies the code.
    - [ ] It uses extra memory (for the cache) to decrease time complexity.
    - [ ] It only works for problems with non-overlapping sub-problems.
    - [ ] It decreases both time and memory complexity.
    <br>

#### **Answer Key**
1.  **D**: ||Kruskal's algorithm greedily picks the next cheapest edge from a sorted list at every step, as long as it doesn't violate the MST property (forming a cycle).||
2.  **C**: ||The Greedy Choice Property is specific to Greedy algorithms. It means a locally optimal choice is part of a globally optimal solution. DP requires overlapping sub-problems and optimal substructure.||
3.  **B**: ||The massive performance gain of DP over naive recursion comes from storing the results of sub-problems (like fib(3)) so they only need to be calculated once.||
4.  **B**: ||Binary Search perfectly follows the Divide and Conquer strategy: it divides the array in half, conquers the sub-problem by recursively searching one half, and the combine step is trivial.||
5.  **C**: ||The tabulation method is an iterative approach. It systematically fills a table of solutions from the bottom up, thereby avoiding the function call overhead and potential stack depth issues of recursion.||
6.  **A**: ||In the 0/1 Knapsack problem, a greedy approach (e.g., picking the item with the highest value-to-weight ratio) can fail. The optimal solution might require leaving out a high-ratio item to fit in a combination of other items that yields a higher total value. This problem requires Dynamic Programming.||
7.  **C**: ||Both DP approaches solve each sub-problem fib(i) from i=2 to n exactly once. This results in a linear number of calculations, giving a time complexity of O(n).||
8.  **B**: ||In Merge Sort, the "divide" step is simple (just finding the middle). The "conquer" step is the recursive call. The truly complex work is in the "combine" step, which involves merging two sorted arrays into one. In Quicksort, the work is done in the "divide" (partition) step.||
9.  **C**: ||If the sub-problems are independent and their results are not needed to solve other sub-problems, it's a classic Divide and Conquer scenario. Dynamic Programming is specifically for when sub-problems overlap and are re-used.||
10. **B**: ||Memoization achieves a significant speedup (time complexity reduction) at the cost of using extra space for the cache or memoization table (space complexity increase).||

---

### **Bonus Tips**

*   **How to Spot a DP Problem:** Look for keywords like "find the maximum/minimum/longest/shortest/count of..." for a problem that can be broken down into stages or steps. If you try to solve it recursively and notice you are solving the same sub-problem multiple times, it's a prime candidate for DP.
*   **DP is Recursion + Caching:** The easiest way to think about and develop a DP solution is to first write the naive recursive solution. Then, add a cache (a map or array) to store the results. This is the memoization approach. Converting it to a bottom-up tabular approach is an optimization you can do afterward.
*   **Greedy vs. DP:** The classic example is the Knapsack problem. For the **Fractional Knapsack** (you can take parts of items), a greedy approach works (take the item with the best value/weight ratio). For the **0/1 Knapsack** (you must take an item whole or leave it), the greedy choice might not be optimal, and you must use Dynamic Programming.
*   **The State of DP:** In a DP problem, the "state" refers to the parameters that uniquely identify a sub-problem. In the Fibonacci example, the state is simply `n`. In a problem like the Longest Common Subsequence between two strings `s1` and `s2`, the state would be `(i, j)`, representing the longest subsequence between the prefixes `s1[0..i]` and `s2[0..j]`. Identifying the state is the hardest part of solving a DP problem.

This concludes the Algorithms and Data Structures module. Congratulations on completing the syllabus.

**MCQs** 🔗[[DSA MCQs]]