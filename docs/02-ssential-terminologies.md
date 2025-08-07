# 02: Essential Graph Terminologies

Before diving deep into graph algorithms, it helps to get comfortable with the vocabulary. Don’t worry about memorizing these terms — once you start working with graphs, they’ll come naturally.

| **Term**                  | **Definition**                                                                 | **Simple Analogy**                                                |
|---------------------------|---------------------------------------------------------------------------------|-------------------------------------------------------------------|
| **Vertex (or Node)**      | A fundamental part of a graph that represents an object or a point.            | A person on social media.                                         |
| **Edge (or Link/Arc)**    | A connection between two vertices.                                             | A friendship connection between two people.                       |
| **Undirected Graph**      | A graph where edges have no direction. The connection is mutual.              | A two-way street or a Facebook friendship.                        |
| **Directed Graph (Digraph)** | A graph where edges have a direction from one vertex to another.           | A one-way street or a Twitter "follow".                           |
| **Weighted Graph**        | A graph where each edge has a weight (cost, distance, etc.).                   | A road map where edges have distances.                            |
| **Unweighted Graph**      | A graph where edges have no weights.                                           | A social network where all friendships are equal.                 |
| **Degree of a Vertex**    | In undirected graphs, the number of edges connected to the vertex.             | The number of friends a person has.                               |
| **In-degree (Directed)**  | Number of edges coming into a vertex.                                          | Number of followers a person has.                                 |
| **Out-degree (Directed)** | Number of edges going out from a vertex.                                       | Number of people a person is following.                           |
| **Path**                  | A sequence of vertices connected by edges.                                     | A route from one city to another.                                 |
| **Cycle**                 | A path that starts and ends at the same vertex.                                | A round trip.                                                     |
| **Connected Graph**       | An undirected graph where there’s a path between every pair of vertices.       | A friend group where everyone is connected directly or indirectly.|
| **Disconnected Graph**    | An undirected graph with two or more disconnected components.                  | Separate friend groups with no one in common.                     |
| **DAG (Directed Acyclic Graph)** | A directed graph with no cycles.                                      | A list of tasks with dependencies (e.g., socks before shoes).     |
