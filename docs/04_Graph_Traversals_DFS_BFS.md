# 04: Graph Traversals (BFS & DFS)

Traversing a graph means visiting every vertex and edge in a systematic way. And guess what? This is where the real fun begins. Whether you're searching for the shortest path, checking connectivity, or solving puzzles—graph traversal is the key.

The two most famous traversal algorithms are:

* **Breadth-First Search (BFS)**
* **Depth-First Search (DFS)**

Let’s begin with **BFS** – the more level-headed one of the two!

---

### 1. Breadth-First Search (BFS)

BFS explores the graph level by level. It starts at a source node and explores all of its immediate neighbors before moving on to their neighbors, and so on.

####Analogy:

Imagine dropping a stone in a pond — the ripples spread out level by level. That’s BFS in action.

####How to Think with BFS

BFS uses a **queue** to keep track of nodes to visit next. Because queues follow First-In-First-Out (FIFO) logic, you always explore nodes in layers. You’ll also need a **visited array or set** to make sure each node is only processed once — no one wants to get stuck in an infinite loop!

####When Should I Use BFS?

Use BFS when:

* You want the **shortest path** in an **unweighted** graph.
* You’re solving a **multi-source** shortest path problem.
* You need to explore a graph level-by-level.

####Why BFS Guarantees the Shortest Path:

Because it visits all nodes at distance 1 before distance 2, and so on. The **first** time you reach the destination is the **shortest path** to it.

---

###BFS Pattern Checklist

| Use Case                          | BFS?  | Why?                                               |
| --------------------------------- | ----- | -------------------------------------------------- |
| Shortest path in unweighted graph | ✅ Yes | First time you reach a node = shortest path to it. |
| Connectivity / component checks   | ✅ Yes | Easily visits all reachable nodes from a source.   |
| Implicit graphs (grids, mazes)    | ✅ Yes | Easy to handle directions and levels.              |

---

###C++ Implementation (Adjacency List)

```cpp
#include <iostream>
#include <vector>
#include <queue>
using namespace std;

void bfs(int V, vector<vector<int>>& adj, int start) {
    vector<bool> visited(V, false);
    queue<int> q;

    q.push(start);
    visited[start] = true;

    while (!q.empty()) {
        int node = q.front();
        q.pop();
        cout << node << " ";

        for (int neighbor : adj[node]) {
            if (!visited[neighbor]) {
                visited[neighbor] = true;
                q.push(neighbor);
            }
        }
    }
}
```

###Python Implementation

```python
from collections import deque, defaultdict

def bfs(V, adj, start):
    visited = [False] * V
    q = deque()

    q.append(start)
    visited[start] = True

    while q:
        node = q.popleft()
        print(node, end=' ')

        for neighbor in adj[node]:
            if not visited[neighbor]:
                visited[neighbor] = True
                q.append(neighbor)
```

---

###Time and Space Complexity (BFS)

* **Time Complexity:** `O(V + E)`
* **Space Complexity:** `O(V)` — for the queue and visited array

---

###Brownie Points

* **Common Mistake:** Don’t delay marking nodes as visited! Mark them right **after enqueueing**, not when dequeuing. Otherwise, they may be added to the queue multiple times, causing TLE.

* **Real-World Applications:**

  * **Shortest Path:** Maze solving, navigating maps
  * **Web Crawlers:** Level-wise link exploration
  * **Social Networks:** Finding mutual friends
  * **Connected Components** in undirected graphs

---

###Practice Problem: Rotting Oranges (Amazon, Google, Microsoft)

> Given an `m x n` grid:
>
> * `0` = empty cell
> * `1` = fresh orange
> * `2` = rotten orange
>
> Every minute, any fresh orange adjacent to a rotten orange becomes rotten. Return the **minimum number of minutes** that must elapse until no cell has a fresh orange. Return `-1` if impossible.

**Intuition:** It’s a shortest path on an **implicit graph**. Multiple rotten oranges? → **Multi-source BFS!**

####C++ Code (Rotting Oranges)

```cpp
int orangesRotting(vector<vector<int>>& grid) {
    int m = grid.size(), n = grid[0].size();
    queue<pair<int, int>> q;
    int fresh = 0, time = 0;

    for (int i = 0; i < m; ++i) {
        for (int j = 0; j < n; ++j) {
            if (grid[i][j] == 2)
                q.push({i, j});
            else if (grid[i][j] == 1)
                ++fresh;
        }
    }

    vector<int> dx = {-1, 1, 0, 0};
    vector<int> dy = {0, 0, -1, 1};

    while (!q.empty() && fresh > 0) {
        int sz = q.size();
        while (sz--) {
            auto [x, y] = q.front(); q.pop();
            for (int i = 0; i < 4; ++i) {
                int nx = x + dx[i], ny = y + dy[i];
                if (nx >= 0 && ny >= 0 && nx < m && ny < n && grid[nx][ny] == 1) {
                    grid[nx][ny] = 2;
                    --fresh;
                    q.push({nx, ny});
                }
            }
        }
        ++time;
    }
    return fresh == 0 ? time : -1;
}
```

####Python Code (Rotting Oranges)

```python
from collections import deque

def orangesRotting(grid):
    rows, cols = len(grid), len(grid[0])
    q = deque()
    fresh = 0

    for r in range(rows):
        for c in range(cols):
            if grid[r][c] == 2:
                q.append((r, c))
            elif grid[r][c] == 1:
                fresh += 1

    directions = [(-1,0), (1,0), (0,-1), (0,1)]
    time = 0

    while q and fresh > 0:
        for _ in range(len(q)):
            r, c = q.popleft()
            for dr, dc in directions:
                nr, nc = r + dr, c + dc
                if 0 <= nr < rows and 0 <= nc < cols and grid[nr][nc] == 1:
                    grid[nr][nc] = 2
                    fresh -= 1
                    q.append((nr, nc))
        time += 1

    return time if fresh == 0 else -1
```

---

###More BFS-Based Practice Problems

* [ ] 01 Matrix (Find distance of nearest 0)
* [ ] Word Ladder (Shortest word transformation)
* [ ] Shortest path in a Binary Maze

Coming up next: **Depth-First Search (DFS)** — the recursive explorer!
