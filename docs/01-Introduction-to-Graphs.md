# 01: What is a Graph? An Introduction

When I first started learning data structures, graphs felt abstract and a bit intimidating. The definitions were dry, the code was unfamiliar, and it didn’t really “click” at first. But then I realized — graphs aren’t just a computer science concept. They’re everywhere.

From social networks to road systems, airline routes to recommendation engines, graphs are a way of seeing how things are connected. Once I saw that, graphs started to make a lot more sense.

This guide is my attempt to explain graphs the way I wish someone had explained them to me — using intuition, analogies, and just enough theory to build real understanding.

---

## The Analogy That Made It Click

The mental model that unlocked everything for me was the **city map** analogy. Here's how I think about it:

- **Cities are Nodes (or Vertices):** Each city is a distinct point.
- **Roads are Edges:** Roads connect cities, just like edges connect nodes.
- **Two-Way vs. One-Way Roads:** A two-way road is an *undirected edge*. A one-way road is a *directed edge*.
- **Distance Between Cities:** If the road has a distance (say, 10 km), it’s a *weighted edge*. If there’s no distance mentioned, it’s *unweighted*.

Once I started seeing graphs this way, they felt a lot less abstract. They became something I could visualize and reason about clearly.

---

## The Key Properties of Graphs

Before we dive deeper, let’s get familiar with some basic terminology. You’ll hear these words often while studying graphs or solving problems.

- **Nodes (Vertices):** The individual points or entities in the graph.
- **Edges:** The connections between the nodes.
- **Directed vs. Undirected:** Edges can go one way or both ways.
- **Weighted vs. Unweighted:** Edges can have a cost (like distance or time) or no cost.
- **Cyclic vs. Acyclic:** Cyclic graphs have at least one loop or cycle; acyclic ones don’t.
- **Connected vs. Disconnected:** In a connected graph, there’s a path between every pair of nodes. In a disconnected graph, some nodes are isolated.
- **Loops and Multiedges:** A node can have an edge to itself (loop), and sometimes multiple edges can exist between the same pair of nodes.

Understanding these concepts is important, because many problems will specifically ask about cycles, connectivity, weights, or directions — and each of these factors can influence the algorithm you use.

---

## How to Think in Graphs — My Advice

The biggest shift for me came when I stopped viewing graphs as just code (`adj[u].push_back(v)`) and started thinking of them as real networks. Whenever I get a new graph problem, I always draw it out first.

Even a quick sketch on paper helps me:
- Visualize the structure
- Spot patterns
- Identify cycles or disconnected parts

Here’s a mental checklist I go through when I’m trying to decide if a problem is graph-related:

- **Is it about relationships or connections?** (e.g., people in a social network, cities connected by flights) → Probably a Graph.
- **Is it about transitions between states?** (e.g., solving a puzzle, moving from one configuration to another) → Think Graph.
- **Is it about dependencies or prerequisites?** (e.g., course schedules, task orderings, build systems) → Think *Directed Graph*.

The more you start to see problems this way, the more natural graphs become. They stop feeling like an isolated topic, and start feeling like a universal tool.

---

## What’s Next

In the next sections, we’ll look at how graphs are represented in code, how to build them, and then dive into core algorithms like BFS, DFS, Dijkstra, and more — all from both an intuitive and implementation-first perspective.

Let’s get started.
