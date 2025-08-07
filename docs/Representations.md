# 02: How to Represent a Graph in Code

[cite_start]Once we understand what a graph is, the next crucial step is figuring out how to store it in memory[cite: 39]. [cite_start]The choice we make here directly impacts the performance and memory usage of our graph algorithms, so it's a critical decision[cite: 39].

[cite_start]The three most common representations are the **Adjacency Matrix**, **Adjacency List**, and **Edge List**[cite: 40].

---

### The Example Graph

[cite_start]Throughout this section, we'll use this simple undirected and unweighted graph to compare the different representations[cite: 41]:



* [cite_start]**Vertices (Nodes):** `{A, B, C, D}` which we'll map to `{0, 1, 2, 3}`[cite: 43].
* [cite_start]**Edges (Connections):** `{(A,B), (B,C), (B,D), (C,D)}`[cite: 44].

---

### 1. Adjacency Matrix

[cite_start]An adjacency matrix is a 2D array (a grid) of size V x V, where V is the total number of vertices[cite: 46]. [cite_start]If there's an edge from vertex `i` to vertex `j`, we set `matrix[i][j] = 1` (or the edge's weight); otherwise, it's 0[cite: 47, 48].

**Representation:**

|           | 0(A) | 1(B) | 2(C) | 3(D) |
| :-------- | :--: | :--: | :--: | :--: |
| **0(A)** |  0   |  1   |  0   |  0   |
| **1(B)** |  1   |  0   |  1   |  1   |
| **2(C)** |  0   |  1   |  0   |  1   |
| **3(D)** |  0   |  1   |  1   |  0   |

**Complexities:**
* [cite_start]**Space:** O(V²) [cite: 56]
* [cite_start]**Check for an edge:** O(1) [cite: 58]
* [cite_start]**Add/Remove an edge:** O(1) [cite: 59]
* [cite_start]**Find all neighbors:** O(V) [cite: 60]

---

### 2. Adjacency List

[cite_start]This is an array of lists[cite: 62]. [cite_start]The main array has a size of V (the number of vertices)[cite: 63]. [cite_start]Each index `i` in the array represents a vertex, and it holds a list of all the neighbors of vertex `i`[cite: 64, 65].

**Representation:**


**Complexities:**
* [cite_start]**Space:** O(V + E) [cite: 73]
* [cite_start]**Check for an edge:** O(degree(u)) [cite: 75]
* [cite_start]**Add an edge:** O(1) [cite: 76]
* [cite_start]**Find all neighbors:** O(degree(u)) [cite: 78]

---

### 3. Edge List

[cite_start]This is the simplest form: just a list of all the edges in the graph[cite: 80]. [cite_start]Each element in the list is a pair of vertices that are connected[cite: 80].

**Representation:**

[cite_start][cite: 86]

**Complexities:**
* [cite_start]**Space:** O(E) [cite: 88]
* [cite_start]**Check for an edge:** O(E) [cite: 91]
* [cite_start]**Add an edge:** O(1) [cite: 94]
* [cite_start]**Find all neighbors:** O(E) [cite: 93]

---

### 🤔 When to Use Which Representation?

Choosing the right structure is a trade-off between space and the speed of common operations.

| Use Case                                  | Adjacency Matrix | Adjacency List  | The Trade-Off                                                                              |
| :---------------------------------------- | :--------------: | :-------------: | :----------------------------------------------------------------------------------------- |
| **Graph is dense** (E ≈ V²)               | ✅ **Good Choice** |    Ok Choice    | [cite_start]Space isn't a major concern, and getting O(1) edge checks is a huge win[cite: 96].            |
| **Graph is sparse** (E ≪ V²)              |    Bad Choice    | ✅ **Best Choice** | An O(V²) matrix is extremely wasteful. [cite_start]O(V + E) is far more memory efficient[cite: 96].     |
| **Need fast edge lookups?** | ✅ **Best Choice** |    Ok Choice    | [cite_start]O(1) is always faster than O(degree(u))[cite: 96].                                          |
| **Need to iterate neighbors fast?** |    Bad Choice    | ✅ **Best Choice** | [cite_start]O(degree(u)) is much faster than iterating through an entire row of O(V)[cite: 96].         |
| **Using algorithms like Kruskal’s?** |    Ok Choice     |    Ok Choice    | [cite_start]An **Edge List** is often the most direct and natural input format for these algorithms[cite: 96]. |

---

### 💡 Brownie Points & Pro Tips

* [cite_start]**The Default Choice:** In interviews and competitive programming, the **Adjacency List is the default choice**[cite: 98]. [cite_start]It offers the best all-around balance of space and time for most problems[cite: 98, 99].
* [cite_start]**Implicit Graphs:** Remember that sometimes a graph isn't given to you explicitly[cite: 100]. [cite_start]On a chessboard, for example, the squares are the nodes and a knight's possible moves are the edges[cite: 100]. [cite_start]You build this "implicit graph" as you go[cite: 101].
* **Real-World Examples:**
    * [cite_start]Facebook's social network is a **sparse graph**; you have millions of users but are only connected to a few hundred[cite: 105]. [cite_start]An **adjacency list** is perfect here[cite: 106].
    * [cite_start]A flight distance table between every major airport is a **dense graph**[cite: 107]. [cite_start]An **adjacency matrix** is a suitable choice for this scenario[cite: 107].

---

### 💻 Implementation Examples (Adjacency List)

Since the Adjacency List is the most common representation, here is how you would typically implement it in C++ and Python.

#### C++
```cpp
#include <iostream>
#include <vector>

int main() {
    // Number of vertices
    int V = 4;

    // Declare an adjacency list for V vertices
    std::vector<std::vector<int>> adj(V);

    // Add edges for our example graph
    // A(0) -- B(1)
    adj[0].push_back(1);
    adj[1].push_back(0);

    // B(1) -- C(2)
    adj[1].push_back(2);
    adj[2].push_back(1);

    // B(1) -- D(3)
    adj[1].push_back(3);
    adj[3].push_back(1);

    // C(2) -- D(3)
    adj[2].push_back(3);
    adj[3].push_back(2);

    // Print the neighbors of vertex 1 (B)
    std::cout << "Neighbors of vertex 1: ";
    for (int neighbor : adj[1]) {
        std::cout << neighbor << " ";
    }
    // Output: Neighbors of vertex 1: 0 2 3
    std::cout << std::endl;

    return 0;
}

from collections import defaultdict

# Declare an adjacency list using a dictionary
# defaultdict(list) means if a key doesn't exist, it's created with an empty list
adj = defaultdict(list)

# Add edges for our example graph
# A(0) -- B(1)
adj[0].append(1)
adj[1].append(0)

# B(1) -- C(2)
adj[1].append(2)
adj[2].append(1)

# B(1) -- D(3)
adj[1].append(3)
adj[3].append(1)

# C(2) -- D(3)
adj[2].append(3)
adj[3].append(2)

# Print the neighbors of vertex 1 (B)
print(f"Neighbors of vertex 1: {adj[1]}")
# Output: Neighbors of vertex 1: [0, 2, 3]
