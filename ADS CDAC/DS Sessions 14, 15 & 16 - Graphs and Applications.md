## **Sessions 14, 15 & 16: Graphs and Applications**

Welcome to our final sessions on data structures. We now explore **Graphs**, the most versatile and general data structure. While [[DS Sessions 7, 8 & 9 - Trees & Applications|Trees]] represent hierarchical relationships, graphs can represent any kind of connection or network—from social networks and road maps to computer networks and project dependencies.

---

## **1. Graph Terminology**

A graph `G` is a set of vertices (or nodes) and a set of edges that connect pairs of vertices. `G = (V, E)`.

*   **Vertex (V):** A node in the graph.
*   **Edge (E):** A connection between two vertices. An edge can be **weighted** (has a cost or distance associated with it) or **unweighted**.
*   **Adjacency:** Two vertices are adjacent if they are connected by an edge.
*   **Path:** A sequence of vertices where each adjacent pair is connected by an edge.
*   **Directed Graph (Digraph):** Edges have a direction (`A -> B`). This represents a one-way relationship.
*   **Undirected Graph:** Edges have no direction (`A - B`). The relationship is two-way.
*   **Cycle:** A path that starts and ends at the same vertex. A graph with no cycles is called **acyclic**. A **Directed Acyclic Graph (DAG)** is a common and important type of graph.

**Graph Representation:**
How we store a graph in memory is crucial for algorithm performance.
1.  **Adjacency Matrix:** A V x V matrix where `matrix[i][j] = 1` (or the edge weight) if there is an edge from vertex `i` to `j`, and 0 otherwise.
    *   **Pros:** Fast to check if an edge exists between two vertices (O(1)).
    *   **Cons:** Uses a lot of space (O(V²)), which is inefficient for **sparse graphs** (graphs with few edges).
2.  **Adjacency List:** An array where each index `i` stores a [[DS Sessions 4 & 5 - Linked List Data Structures|linked list]] of all vertices adjacent to vertex `i`.
    *   **Pros:** Space efficient for sparse graphs (O(V+E)).
    *   **Cons:** Slower to check for a specific edge (O(degree of vertex)).
    *   This is the most common representation for graph algorithms.

**Visualizing Representations for an Undirected Graph:**
`A -- B -- C`

**Adjacency Matrix:**
```c
    A B C
  A[0,1,0]
  B[1,0,1]
  C[0,1,0]
```
**Adjacency List:**
```c
  A -> [B]
  B -> [A, C]
  C -> [B]
```
---

## **2. Graph Traversal**

Just like with trees, traversal means visiting every vertex exactly once.

*   **Breadth-First Search (BFS):** Explores the graph layer by layer. It starts at a source vertex, visits all its neighbors, then visits their unvisited neighbors, and so on. It uses a [[DS Sessions 2 & 3 - Algorithms & Data Structures#c) Queues (FIFO)|Queue]]. BFS is excellent for finding the **shortest path in an unweighted graph**.

*   **Depth-First Search (DFS):** Explores as far as possible along each branch before backtracking. It starts at a source vertex, explores one of its neighbors completely, then backtracks and explores another neighbor. It uses a [[DS Sessions 2 & 3 - Algorithms & Data Structures#b) Stacks (LIFO)|Stack]] (often the implicit call stack via [[DS Session 6 - Recursion|recursion]]). DFS is great for detecting cycles and for topological sorting.

Traversal means visiting every vertex in a graph exactly once. The order in which you visit them defines the traversal type. The key to both BFS and DFS is to keep track of which vertices have already been visited to avoid infinite loops in graphs with cycles.

Let's use the following graph for all traversal examples, starting from vertex **A**.

```c
B ----- C
     / \   /   \
    /   \ /     \
   A --- D ----- E
    \   /
     \ /
      F
```

#### **a) Breadth-First Search (BFS) - In-depth**

- **Core Idea:** Explores the graph layer by layer. It visits the starting node, then all of its direct neighbors, then all of their unvisited neighbors, and so on.
    
- **Data Structure:** Uses a **[[DS Sessions 2 & 3 - Algorithms & Data Structures#c) Queues (FIFO)|Queue]]** to manage which node to visit next. The FIFO nature of the queue ensures the layer-by-layer exploration.
    
- **Application:** Excellent for finding the **shortest path** (in terms of number of edges) between two nodes in an unweighted graph.
    

**Step-by-Step Visualization of BFS (starting from A):**

1. **Initialize:**
    
    - Queue: [ A ]
        
    - Visited: [ A ]
        
    - **Output:** A
        
2. **Dequeue A. Enqueue A's unvisited neighbors (B, D, F).**
    
    - Queue: [ B, D, F ]
        
    - Visited: [ A, B, D, F ]
        
    - **Output:** A, B, D, F
        
    
    **State Visualization:**
    
    ```c
    Queue:  [ F | D | B ] -> (Front of queue)
    Visited: A, B, D, F
    Current Node being processed: A
    ```
    
3. **Dequeue B. Enqueue B's unvisited neighbors (C).** (A and D are already visited).
    
    - Queue: [ D, F, C ]
        
    - Visited: [ A, B, D, F, C ]
        
    - **Output:** A, B, D, F, C
        
    
    **State Visualization:**
    
    
    ```c
    Queue:  [ C | F | D ] ->
    Visited: A, B, D, F, C
    Current Node being processed: B
    ```
    
4. **Dequeue D. Enqueue D's unvisited neighbors (E).** (A, B, C, F are already visited).
    
    - Queue: [ F, C, E ]
        
    - Visited: [ A, B, D, F, C, E ]
        
    - **Output:** A, B, D, F, C, E
        
5. **Dequeue F.** F has no unvisited neighbors (A and D are visited).
    
    - Queue: [ C, E ]
        
6. **Dequeue C.** C has no unvisited neighbors (B, D, E are visited).
    
    - Queue: [ E ]
        
7. **Dequeue E.** E has no unvisited neighbors (C and D are visited).
    
    - Queue: [ ] (Empty)
        
8. The queue is empty. The traversal is complete.
    
    - **Final Traversal Order:** A, B, D, F, C, E
        

---

#### **b) Depth-First Search (DFS) - In-depth**

- **Core Idea:** Explores as far as possible down one path before backtracking. It's like navigating a maze by always taking the first available path at a junction until you hit a dead end, then backtracking to the last junction and trying the next available path.
    
- **Data Structure:** Uses a **[[DS Sessions 2 & 3 - Algorithms & Data Structures#b) Stacks (LIFO)|Stack]]** to manage which node to visit next. The LIFO nature of the stack ensures the "go deep first" behavior. This is often implemented implicitly using the function call stack via [[DS Session 6 - Recursion|recursion]].
    
- **Application:** Great for cycle detection, topological sorting (for DAGs), and finding connected components.
    

### **Step-by-Step Visualization of DFS (Recursive approach, starting from A):**

The order of visiting neighbors can change the final path. Let's assume we always explore neighbors in alphabetical order.

 #### **Steps :**

1. **Now at E.** Mark E as visited. **Output: A, B, C, D, E**.
    
    - E's neighbors C, D are visited. E has no more unvisited neighbors. **Return from DFS(E)**.
        
    - **Call Stack pops DFS(E):** [ main() -> DFS(A) -> DFS(B) -> DFS(C) -> DFS(D) ]
        
2. **Back at D.** We just returned from E. Check D's next unvisited neighbor: **F**.
    
    - **Call DFS(F)**.
        
    
    - **Call Stack:** [ main() -> DFS(A) -> DFS(B) -> DFS(C) -> DFS(D) -> DFS(F) ]
        
3. **Now at F.** Mark F as visited. **Output: A, B, C, D, E, F**.
    
    - F's neighbors A, D are visited. F is at a dead end. **Return from DFS(F)**.
        
    - **Call Stack pops DFS(F):** [ main() -> DFS(A) -> DFS(B) -> DFS(C) -> DFS(D) ]
        
4. **Back at D.** All of D's neighbors have been visited. **Return from DFS(D)**.
    
    - **Call Stack pops DFS(D)**.
        
5. ...and so on. The process continues backtracking until the original call to DFS(A) finishes.
    
    - **Final Traversal Order:** A, B, C, D, E, F
        

---

## **Shortest Path Algorithms (In-depth)**

The "shortest path" problem aims to find a path between two vertices such that the sum of the weights of its constituent edges is minimized.

#### **a) Dijkstra's Algorithm (Single-Source Shortest Path)**

*   **Goal:** Finds the shortest path from a **single source vertex** to **all other vertices** in the graph.
*   **Constraint:** It works only on graphs with **non-negative edge weights**.
*   **Type:** A "greedy" algorithm. At each step, it greedily chooses the next "closest" unvisited vertex.
*   **Core Idea:** Maintains a set of visited vertices and a distance array `dist[]`, where `dist[i]` stores the current shortest known distance from the source to vertex `i`.

**Step-by-Step Visualization of Dijkstra's Algorithm:**
Let's find the shortest path from source **A** in the graph below.
`dist` array initialized to `[A:0, B:∞, C:∞, D:∞, E:∞]`
`visited` set is empty.

```c
       (4)
    B ------ C
   / \       / \ (1)
(1)   \ (5) /   E
 /     \ /     /
A ------ D --(3)
 \     /
  \   / (2)
   ---
```

**Step 1:**
*   Start at source **A**. `dist[A] = 0`.
*   Visit A. Look at its neighbors:
    *   To B: `dist[A]+1 = 1`. Update `dist[B] = 1`.
    *   To D: `dist[A]+2 = 2`. Update `dist[D] = 2`.
*   **`dist` array:** `[A:0, B:1, C:∞, D:2, E:∞]`
*   **Choose next vertex:** Pick the unvisited vertex with the smallest distance: **B** (dist=1).

**Step 2:**
*   Visit **B**. Look at its unvisited neighbors (A is visited): C, D.
    *   To C: Path through B is `dist[B]+4 = 1+4 = 5`. Update `dist[C] = 5`.
    *   To D: Path through B is `dist[B]+5 = 1+5 = 6`. Current `dist[D]` is 2. Since 6 > 2, we **do not** update.
*   **`dist` array:** `[A:0, B:1, C:5, D:2, E:∞]`
*   **Choose next vertex:** Pick the unvisited vertex with the smallest distance: **D** (dist=2).

**Step 3:**
*   Visit **D**. Look at its unvisited neighbors: C, E.
    *   To C: Path through D is `dist[D]+1 = 2+1 = 3`. Current `dist[C]` is 5. Since 3 < 5, we **update** `dist[C] = 3`.
    *   To E: Path through D is `dist[D]+3 = 2+3 = 5`. Update `dist[E] = 5`.
*   **`dist` array:** `[A:0, B:1, C:3, D:2, E:5]`
*   **Choose next vertex:** Pick unvisited: **C** (dist=3).

**Step 4:**
*   Visit **C**. Look at its unvisited neighbors: E.
    *   To E: Path through C is `dist[C]+1 = 3+1 = 4`. Current `dist[E]` is 5. Since 4 < 5, we **update** `dist[E] = 4`.
*   **`dist` array:** `[A:0, B:1, C:3, D:2, E:4]`
*   **Choose next vertex:** Only **E** (dist=4) is left. Visit E. It has no unvisited neighbors.

**Final Result:** The shortest distances from A are: A(0), B(1), C(3), D(2), E(4).

#### **b) Floyd-Warshall Algorithm (All-Pairs Shortest Path)**

*   **Goal:** Finds the shortest paths between **every pair** of vertices in the graph.
*   **Constraint:** It can handle **negative edge weights**, but not negative cycles.
*   **Type:** A Dynamic Programming algorithm.
*   **Core Idea:** It iteratively considers each vertex `k` and checks if going from `i` to `j` *through `k`* is shorter than the currently known path from `i` to `j`.

**Pseudocode and Visualization:**
1.  Initialize a distance matrix `dist[V][V]` with the direct edge weights from the adjacency matrix. The distance from a node to itself is 0, and `∞` if there is no direct edge.
2.  Then, use three nested loops:
    `for k from 0 to V-1` (The intermediate vertex)
      `for i from 0 to V-1` (The source vertex)
        `for j from 0 to V-1` (The destination vertex)
          `if dist[i][k] + dist[k][j] < dist[i][j]`
            `dist[i][j] = dist[i][k] + dist[k][j]`

**Visualization (`k=0` iteration):**
Let's say we have vertices 0, 1, 2. The algorithm checks:
*   Is going from 1 to 2 shorter via vertex 0? i.e., is `dist[1][0] + dist[0][2]` less than `dist[1][2]`? If so, update `dist[1][2]`.
*   It does this for every possible pair `(i, j)`.
After the `k` loop finishes, the `dist` matrix contains all the shortest path distances.

---

### **Minimum Spanning Trees (MST) (In-depth)**

*   **Spanning Tree:** A subgraph of a connected, undirected graph that connects all the vertices together with the minimum possible number of edges (V-1 edges) and has no cycles.
*   **Minimum Spanning Tree (MST):** For a weighted graph, the MST is a spanning tree with the minimum possible total edge weight.
*   **Application:** Designing a network (like power grids or water pipelines) to connect all cities with the minimum amount of cable/pipe.

#### **a) Prim's Algorithm**

*   **Type:** A greedy algorithm.
*   **Core Idea:** Grows the MST from a single starting vertex. At each step, it greedily adds the **cheapest edge** that connects a vertex **inside** the growing MST to a vertex **outside** the MST.
*   **Analogy:** Building a connected territory. You start with one city. At every step, you find the cheapest road that connects your territory to a new, unconnected city and build it.

**Step-by-Step Visualization of Prim's Algorithm:**
Start at vertex **A**.

```c
       (4)
    B ------ C
   /|\(8)   / \ (1)
(1) | \   /   E
 /  |  \ / (5)
A --|--- D --(3)
 \ (2) /
  \   / (6)
   ---
```
*(Added edge B-D with weight 8 and A-D with weight 6 for this example)*

**Step 1:** Start at A. Look at all edges from A: A-B(1), A-D(2). Pick the cheapest: **A-B (1)**.
   *   MST so far: `{A, B}`. Total Cost: 1.

**Step 2:** Look at all edges from the current MST `{A, B}` to outside vertices: A-D(2), B-C(4), B-D(8). Pick the cheapest: **A-D (2)**.
   *   MST so far: `{A, B, D}`. Total Cost: 1+2=3.

**Step 3:** Look at all edges from `{A, B, D}` to outside vertices: B-C(4), D-C(5), D-E(3), A-D(6)-already connected. Pick the cheapest: **D-E (3)**.
   *   MST so far: `{A, B, D, E}`. Total Cost: 3+3=6.

**Step 4:** Look at all edges from `{A, B, D, E}` to outside vertices: B-C(4), D-C(5). Pick the cheapest: **B-C (4)**.
   *   MST so far: `{A, B, D, E, C}`. All vertices are connected. Stop.
   *   **Final MST Edges:** (A,B), (A,D), (D,E), (B,C). Total Cost: 1+2+3+4 = 10.

#### **b) Kruskal's Algorithm**

*   **Type:** A greedy algorithm.
*   **Core Idea:** It treats the MST as a growing "forest" of trees. It sorts all edges in the graph by weight and adds the next cheapest edge **as long as it does not form a cycle** with the edges already added.
*   **Analogy:** Building a railway network. You have a list of all possible tracks and their costs. You start by building the absolute cheapest track anywhere. Then you build the next cheapest track, and so on, but you never build a track that would create a closed loop.
*  **Core Idea:** A greedy algorithm that builds a Minimum Spanning Tree (MST) by adding edges one by one. It always picks the next lightest edge from the graph, but only adds it to the MST if doing so **does not form a cycle**.
* **Data Structure:** It conceptually uses a **list of all edges sorted by weight** and a **Disjoint Set Union (DSU)** data structure to efficiently detect cycles.

##### **The Disjoint Set Union (DSU) or Union-Find Data Structure:**

- This structure is designed to keep track of a set of elements partitioned into a number of disjoint (non-overlapping) subsets.
    
- **find(i):** Determines which subset an element i is in. It returns the "representative" or "parent" of that set.
    
- **union(i, j):** Merges the two subsets containing i and j into a single subset.
    
- **Cycle Detection:** Before adding an edge (u, v) to our MST, we check if find(u) == find(v). If they are already in the same set (have the same representative), it means there is already a path between them, and adding this edge would create a cycle. If they are in different sets, we add the edge and perform a union(u, v).
    

#### **Step-by-Step Visualization of Kruskal's Algorithm:**

**Let's use this graph.**

```c
B --(4)-- C
     /|\        /
    / | \      /
 (1) (7) (2)  / (5)
  /  |  \    /
 /   |   \  /
A --(6)-- D --(3)-- E
```

**Step 1: Create a sorted list of all edges.**

- (A, B, 1), (B, D, 2), (D, E, 3), (B, C, 4), (C, D, 5), (A, D, 6), (A, C, 7) - Corrected edge A-C weight to 7
    

**Step 2: Initialize DSU.** Each vertex is in its own set.

- Sets: {A}, {B}, {C}, {D}, {E}
    
- MST Edges: []
    

##### **Iteration 1:**

- **Edge:** (A, B, 1).
    
- **Check Cycle:** find(A) is not equal to find(B). No cycle.
    
- **Action:** Add edge to MST. Perform union(A, B).
    
- **MST Edges:** [(A,B)]. Sets: {A,B}, {C}, {D}, {E}.
    

##### **Iteration 2:**

- **Edge:** (B, D, 2).
    
- **Check Cycle:** find(B) (rep=A) is not equal to find(D). No cycle.
    
- **Action:** Add edge. Perform union(B, D).
    
- **MST Edges:** [(A,B), (B,D)]. Sets: {A,B,D}, {C}, {E}.

    **Visual State:**
    
    ```c
    A---B---D     C     E
    ```
    

##### **Iteration 3:**

- **Edge:** (D, E, 3).
    
- **Check Cycle:** find(D) (rep=A) is not equal to find(E). No cycle.
    
- **Action:** Add edge. Perform union(D, E).
    
- **MST Edges:** [(A,B), (B,D), (D,E)]. Sets: {A,B,D,E}, {C}.

    **Visual State:**
    
    ```c
    A---B---D---E     C
    ```


##### **Iteration 4:**

- **Edge:** (B, C, 4).
    
- **Check Cycle:** find(B) (rep=A) is not equal to find(C). No cycle.
    
- **Action:** Add edge. Perform union(B, C).
    
- **MST Edges:** [(A,B), (B,D), (D,E), (B,C)]. Sets: {A,B,C,D,E}.
    
    **Visual State:**
    
    ```c
	       C
         |
       A---B---D---E
    ```
    
    All vertices are now in one set. The algorithm can stop. The total MST weight is 1+2+3+4 = 10.
    

##### **Iteration 5 (for demonstration):**

- **Edge:** (C, D, 5).
    
- **Check Cycle:** find(C) (rep=A) **is equal to** find(D) (rep=A).
    
- **Action:** **Discard this edge.** It would form a cycle (B-C-D-B).
    

This process continues until V-1 edges have been added to the MST.


Kruskal's is often implemented using a `Disjoint Set Union (DSU)` data structure to efficiently check for cycles.

---

### **Topic Summary & Revision**

*   **Graph:** A structure of vertices and edges, represented by an Adjacency Matrix or Adjacency List.
*   **Shortest Path:**
    *   **Dijkstra:** Single-source shortest path. Greedy. **Cannot have negative edge weights.**
    *   **Floyd-Warshall:** All-pairs shortest path. Dynamic Programming. **Can have negative weights (but no negative cycles).**
*   **Minimum Spanning Tree (MST):** A subgraph that connects all vertices with minimum total edge weight and no cycles.
    *   **Prim's:** Grows from one vertex outwards, always adding the cheapest edge to connect a new vertex to the growing tree.
    *   **Kruskal's:** Sorts all edges and adds the next cheapest edge from the list as long as it doesn't form a cycle.

---

### **MCQs for Exam Preparation**

1.  **Dijkstra's algorithm for finding the shortest path will fail if:**
    - [ ] The graph is a DAG (Directed Acyclic Graph).
    - [ ] The graph has cycles.
    - [ ] The graph has negative edge weights.
    - [ ] The graph is not connected.
    <br>

2.  **Which algorithm is best suited to find the shortest path in an unweighted graph?**
    - [ ] Breadth-First Search (BFS)
    - [ ] Depth-First Search (DFS)
    - [ ] Prim's algorithm
    - [ ] Kruskal's algorithm
    <br>

3.  **Prim's algorithm for finding the MST is an example of which algorithmic paradigm?**
    - [ ] Divide and Conquer
    - [ ] Dynamic Programming
    - [ ] Greedy Algorithm
    - [ ] Backtracking
    <br>

4.  **A graph has 7 vertices. How many edges will its spanning tree have?**
    - [ ] 6
    - [ ] 7
    - [ ] 8
    - [ ] It depends on the graph structure.
    <br>

5.  **Which algorithm builds the MST by selecting edges one by one in increasing order of weight, as long as they don't form a cycle?**
    - [ ] Dijkstra's algorithm
    - [ ] Floyd-Warshall algorithm
    - [ ] Prim's algorithm
    - [ ] Kruskal's algorithm
    <br>

6.  **The time complexity of the Floyd-Warshall algorithm for a graph with V vertices is:**
    - [ ] O(V + E)
    - [ ] O(V log E)
    - [ ] O(V²)
    - [ ] O(V³)
    <br>

7.  **If a graph has multiple edges with the same weight, which statement is true?**
    - [ ] The graph can have multiple different Minimum Spanning Trees.
    - [ ] Dijkstra's algorithm will fail.
    - [ ] The graph must be directed.
    - [ ] Kruskal's algorithm cannot be used.
    <br>

8.  **The Adjacency Matrix representation of a graph is preferred over an Adjacency List when:**
    - [ ] The graph is sparse (has few edges).
    - [ ] The graph is dense (has many edges).
    - [ ] The graph is unweighted.
    - [ ] The graph is directed.
    <br>

9.  **Kruskal's algorithm often uses a Disjoint Set Union (DSU) data structure. What is the primary purpose of the DSU in this context?**
    - [ ] To sort the edges by weight efficiently.
    - [ ] To store the resulting MST.
    - [ ] To efficiently check if adding an edge will form a cycle.
    - [ ] To find the shortest path between two vertices.
    <br>

10. **Dijkstra's algorithm maintains a set of vertices whose shortest distance from the source is finalized. At each step, which vertex is added to this set?**
    - [ ] A random unvisited vertex.
    - [ ] The unvisited vertex with the most number of edges.
    - [ ] The unvisited vertex with the smallest calculated distance from the source.
    - [ ] The unvisited vertex that is farthest from the source.
    <br>

**Answer Key**
1.  **C**: ||Dijkstra's greedy approach of finalizing the shortest distance to a vertex at each step relies on the assumption that once a path is found, a shorter one cannot be created later. Negative edge weights can violate this assumption.||
2.  **A**: ||BFS explores the graph layer by layer from the source. This naturally finds the path with the fewest edges, which in an unweighted graph is, by definition, the shortest path.||
3.  **C**: ||Prim's algorithm is greedy because at each step it makes a locally optimal choice (picking the cheapest edge to connect a new vertex) in the hope of finding a globally optimal solution (the MST).||
4.  **A**: ||A fundamental property of any tree (including a spanning tree) with V vertices is that it will always have exactly V-1 edges. So, 7 - 1 = 6 edges.||
5.  **D**: ||This is the definition of Kruskal's algorithm. It builds a "forest" of trees by adding the globally cheapest available edges that don't create a loop within any of the existing tree fragments.||
6.  **D**: ||The Floyd-Warshall algorithm uses three nested loops, each iterating up to V times (for k... for i... for j...), resulting in a time complexity of O(V³).||
7.  **A**: ||If there are multiple edges with the same minimum weight, Kruskal's or Prim's algorithm might have a choice. Different choices at that step can lead to different, but equally valid, Minimum Spanning Trees, all having the same total minimum weight.||
8.  **B**: ||An adjacency matrix uses O(V²) space regardless of the number of edges. An adjacency list uses O(V+E) space. For a dense graph, E approaches V², making the space usage comparable, but the O(1) edge lookup time of the matrix becomes an advantage.||
9.  **C**: ||The DSU data structure is optimized for two operations: find (determine which set an element belongs to) and union (merge two sets). In Kruskal's, before adding an edge (u, v), we check if find(u) is the same as find(v). If they are already in the same set, adding the edge would form a cycle.||
10. **C**: ||This is the core greedy choice of Dijkstra's algorithm. It always explores from the "closest" frontier. By picking the unvisited vertex with the current minimum distance, it ensures that this distance is the final shortest path for that vertex.||

---

### **Bonus Tips**

*   **Dijkstra vs. Prim's:** These two algorithms look very similar but solve different problems.
    *   **Dijkstra:** Finds the shortest path. Its "priority" is the *total distance from the source*.
    *   **Prim's:** Finds the MST. Its "priority" is the *weight of the single edge* being considered to connect a new vertex.
*   **Visualizing is Key:** You cannot solve graph problems in your head. For Dijkstra's, draw the graph and a table to keep track of distances and visited nodes. For MST algorithms, draw the graph and highlight the edges as they are added to the MST set.
*   **When to use All-Pairs?** Floyd-Warshall (O(V³)) is often simpler to implement than running Dijkstra (O(E + V log V)) from all V vertices (`V * (E + V log V)`). For dense graphs where E is close to V², Floyd-Warshall can be a better choice despite its higher complexity notation.
*   **Real-World Application:** Think of Google Maps. When you ask for directions from your home to everywhere else, that's like Dijkstra's. When a city planner wants to connect all houses to a fiber optic network with the least amount of cable, that's a Minimum Spanning Tree problem (likely solved with Prim's or Kruskal's).

**🔗Links:** [[DS Sessions 17, 18 & 19 - Algorithm Design Strategies]]