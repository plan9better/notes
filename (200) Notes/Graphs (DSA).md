A **graph** is a [[Data Structures and Algorithms|mathematical structure]] used to model pairwise relationships between objects. It consists of:

1. **Vertices (Nodes):** The objects or points in the graph.
2. **Edges:** The connections between the vertices. These can be:
    - **Directed**: Edges have a direction (e.g., A → B).
    - **Undirected**: Edges have no direction (e.g., A ↔ B).

Graphs are represented in two primary ways:

1. **Adjacency List:** A list where each vertex points to a list of its adjacent vertices.
2. **Adjacency Matrix:** A 2D matrix where the element at position \[ i \]\[ j \] indicates the presence/weight of an edge from vertex *i* to vertex *j*.

Graphs can also be:

- **Weighted:** Edges have weights (e.g., cost, distance).
- **Unweighted:** All edges are treated equally.
- **Cyclic:** Contain cycles.
- **Acyclic:** Do not contain cycles.
- **Connected:** There is a path between every pair of vertices.
- **Disconnected:** At least one pair of vertices has no path connecting them.
### Algorithms
- [[Prims algorithm]] ( [[Minimum spanning trees]] )
- [[Kruskals algorithm]] ( [[Minimum spanning trees]] )
- [[Djikstras algorithm]] ( Shortest path non-negative edge weights)
- [[Bellman-Ford algorithm]] (Shortest path with negative edge weights)