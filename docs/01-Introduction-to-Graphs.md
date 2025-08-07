# What Is a Graph?

A graph is a collection of nodes (also called vertices) and the connections between them (called edges). It's one of the most powerful ways to represent relationships or connections between objects, and it plays a huge role in both real-world systems and coding problems.

---

## A Simple Analogy

Think of a graph like a city map.

- Cities are the nodes.
- Roads connecting the cities are the edges.
- If a road goes both ways, it's an undirected edge.
- If it's a one-way road, that's a directed edge.
- If the road has a distance or cost, it's a weighted edge.

This analogy really helped me when I was starting out. Instead of seeing graphs as code, I began to see them as real networks — which made it easier to understand problems visually.

---

## Key Properties of Graphs

- A graph consists of a set of vertices and edges.
- Edges can be either directed (A to B) or undirected (A and B connected both ways).
- Graphs can be weighted (edges have values) or unweighted.
- They may be cyclic (contain at least one cycle) or acyclic.
- They can be connected (every node is reachable) or disconnected.
- Some graphs have loops (an edge from a node to itself) or multiple edges between the same nodes (called multigraphs).

---

## How I Learned to Think About Graphs

At first, I was just writing code like `adj[u].push_back(v)` and trying to memorize implementations. But the real shift came when I started drawing graphs out on paper. 

Once I did that, I could actually *see* what the problem was asking — paths, cycles, bottlenecks — all became clearer. Now I make it a habit to sketch the graph before jumping to code.

---

## When Should You Think About Graphs?

Here are some common situations where graphs are the right tool:

- If the problem involves connections (like people in a social network or computers in a network), it probably needs a graph.
- If the problem involves states and transitions (like solving a puzzle or moving between levels), that's usually a graph.
- If it's about dependencies (like course prerequisites or task scheduling), you're probably dealing with a directed graph.

---

## Final Thoughts

Graphs are everywhere, both in competitive programming and real-world systems. The earlier you start thinking in terms of graphs — not just as data structures, but as networks — the easier many problems become.

Draw them, understand them, and try to build some intuition. It’ll go a long way.

— Mohit Chaudhary
