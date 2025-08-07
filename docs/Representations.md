# 02: How to Represent a Graph in Code

Once we understand what a graph is, the next crucial step is figuring out how to store it in memory. The choice we make here directly impacts the performance and memory usage of our graph algorithms, so it's a critical decision.

The three most common representations are the **Adjacency Matrix**, **Adjacency List**, and **Edge List**.

---

### The Example Graph

Throughout this section, we'll use this simple undirected and unweighted graph to compare the different representations:

![Simple Graph Example](../images/simple-graph.png)

- **Vertices (Nodes):** `{A, B, C, D}` mapped to `{0, 1, 2, 3}`
- **Edges (Connections):** `{(A,B), (B,C), (B,D), (C,D)}`

---

### 1. Adjacency Matrix

An adjacency matrix is a 2D array of size `V x V`, where `V` is the number of vertices.  
If there’s an edge from vertex `i` to `j`, `matrix[i][j] = 1` (or the weight). Otherwise, it’s 0.

**Representation:**

|           | 0(A) | 1(B) | 2(C) | 3(D) |
|-----------|------|------|------|------|
| **0(A)**  |  0   |  1   |  0   |  0   |
| **1(B)**  |  1   |  0   |  1   |  1   |
| **2(C)**  |  0   |  1   |  0   |  1   |
| **3(D)**  |  0   |  1   |  1   |  0   |

**Complexities:**
- Space: `O(V²)`
- Check for an edge: `O(1)`
- Add/Remove an edge: `O(1)`
- Find all neighbors: `O(V)`

---

### 2. Adjacency List

This is an array (or vector) of lists. Each index `i` in the array represents a vertex, and its list contains the neighbors of vertex `i`.

**Representation:**


**Complexities:**
- Space: `O(V + E)`
- Check for an edge: `O(degree(u))`
- Add an edge: `O(1)`
- Find all neighbors: `O(degree(u))`

---

### 3. Edge List

An edge list is simply a list of all the edges in the graph.

**Representation:**


**Complexities:**
- Space: `O(E)`
- Check for an edge: `O(E)`
- Add an edge: `O(1)`
- Find all neighbors: `O(E)`

---

### When to Use Which Representation?

| Use Case                          | Adjacency Matrix | Adjacency List  | Trade-Off                                                                 |
|----------------------------------|------------------|------------------|--------------------------------------------------------------------------|
| Graph is dense (`E ≈ V²`)         | ✅ Good Choice   | Ok Choice         | Space isn't a major concern, and O(1) edge checks are fast.               |
| Graph is sparse (`E ≪ V²`)        | ❌ Bad Choice    | ✅ Best Choice     | Adjacency list is much more memory-efficient.                             |
| Need fast edge lookups?          | ✅ Best Choice   | Ok Choice         | Matrix offers `O(1)` edge lookup.                                         |
| Need to iterate neighbors fast?  | ❌ Bad Choice    | ✅ Best Choice     | Adjacency list gives fast access to neighbors with less memory usage.     |
| Using Kruskal’s Algorithm?        | Ok Choice         | Ok Choice         | Edge List is usually the preferred format for such algorithms.            |

---

### Additional Notes

- **Default Choice in Interviews:** Adjacency List — space-efficient and fast for most operations.
- **Implicit Graphs:** When the graph isn't explicitly given (e.g., knight's moves on a chessboard).
- **Real-World Examples:**
  - Facebook's network (sparse) → Use Adjacency List.
  - Airline distances between all major airports (dense) → Use Adjacency Matrix.

---

### Implementation Examples

#### C++ (Adjacency List)

```cpp
#include <iostream>
#include <vector>

int main() {
    int V = 4;
    std::vector<std::vector<int>> adj(V);

    adj[0].push_back(1);
    adj[1].push_back(0);

    adj[1].push_back(2);
    adj[2].push_back(1);

    adj[1].push_back(3);
    adj[3].push_back(1);

    adj[2].push_back(3);
    adj[3].push_back(2);

    std::cout << "Neighbors of vertex 1: ";
    for (int neighbor : adj[1]) {
        std::cout << neighbor << " ";
    }
    std::cout << std::endl;
    return 0;
}


###Python

from collections import defaultdict

adj = defaultdict(list)

adj[0].append(1)
adj[1].append(0)

adj[1].append(2)
adj[2].append(1)

adj[1].append(3)
adj[3].append(1)

adj[2].append(3)
adj[3].append(2)

print(f"Neighbors of vertex 1: {adj[1]}")
# Output: Neighbors of vertex 1: [0, 2, 3]
