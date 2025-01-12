# Graphs
A **graph** is a athematical structure used to model pairwise relationships between objects. It consists of:

1. **Vertices (Nodes):** The objects or points in the graph.
2. **Edges:** The connections between the vertices. These can be:
    - **Directed**: Edges have a direction (e.g., A -> B).
    - **Undirected**: Edges have no direction (e.g., A <-> B).

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

# Minimum spanning trees
### Goals
- It is a subgraph (includes all vertices but not all edges).
- The goal is to find the lowest amount of edges with the lowest connection weight.
- The result should be a tree (shouldn't be cyclical)

#### Spanning tree with unweighed edges
![[Graph6.excalidraw]]
$\text{V - Graph Vertices, E - Graph Edges}$
$V = \{1, 2, 3, 4, 5, 6\}$
$E =\{(1,2), (2,3), (3,4), (4,5), (5,6), (6,1)\}$

$\text{V' = MST Vertices, E' = MST Edges}$
$V' = V$
$E' = \{(1,2), (2,3), (3,4), (4,5), (5,6)\}$
$|E'| = |V| - 1$

#### Same thing different way
![[Graph62.excalidraw]]

# Prims algorithm
Prim's algorithm is an algorithm for finding the minimum spanning trees of a graph. It is super simple.
### Steps
1. Choose a vertice
2. Choose a lowest cost edge connected to one of your already connected vertices.
3. Add the vertice that edge connects to to your list of connected vertices.
So in plain english just grow your tree from a single point always choosing the lowest cost edge and adding it to the tree.

# Kruskals algorithm
Kruskals algo is an algo for finding the Minimum spanning trees of a graph. It is similiar to Prims algorithm.
### Steps.
- Choose a lowest cost edge.
- Choose another lowest cost edge, but only if adding it to your list of already selected edges doesn't form a cycle (MST's have to be trees and therefore not cyclical).
- keep going until all edges are connected.
This way the time complexity will be: $$O(|V| \times |E|)$$ 
This however can be improved when using [[Min Heap]] to store the edges, then it will take $$ O(n\times \log n)$$

# Djikstra's algorithm
Finds the shortest path from source node to every other node in the graph with non-negative weights (Use Bellman-Ford algorithm for negative edge weights).
### Steps:
- Set distance to source node to 0and all nodes not directly connected to source node to $\infty$
- Find the node with the lowest distance (for first iteration, source node since all others are $\infty$)
- For each directly connected node to the selected one (not yet checked before), check if the distance to selected node + weight of connection to neighbouring node is smaller than the current distance to neighbouring node, if so, update it.
- Repeat until all nodes are processed.

### Example:
![[djikstragraph.excalidraw]]
s -> already selected
starting vortex -> 1

| Selected vortex | 2                  | 3   | 4   | 5                        | 6         |
| --------------- | ------------------ | --- | --- | ------------------------ | --------- |
| 4               | 50                 | 45  | s10 | $\infty$                 | $\infty$  |
| 5               | 50                 | 45  | s10 | s10 + 15 = 25 < $\infty$ | $\infty$  |
| 2               | s25 + 20 = 45 < 50 | 45  | s10 | s25                      | $\infty$  |
| 3               | s45                | 45  | s10 | s25                      | $\infty$  |
| 6               | s45                | s45 | s10 | s25                      | s$\infty$ |

# Bellman-Ford algorithm
Dynamic programming Algorithm for finding shortes path from single source node to all other nodes in a Graph. Unlinke Djikstras algorithm it works with negative edge weights but does not work with negative weight cycles. 
It works by checking all possible solutions therefore finding the best one. Repeatedly relaxes all edges $n-1$ times, where $n = |V|$.
Relaxation is the same as in Djikstras algorithm:
```python
if (d[u] + c(u, v) < d[v]:
    d[v] = d[u] + c(u, v)
```
So if the distance to vortex $u$ + weight of edge between $u$ and $v$ is less than the current distance to $v$ then update it. With the exception that you can select any edge. Just make sure that at the end you checked all edges.

### Steps:
- Set the distance to each node to $\infty$
- Select an edge (that wasn't selected before) and relax it.
- Select another edge and relax again, continue for all edges.
- Start again from the start, relaxing all edges one by one.
- Do that $n - 1$ times where $n = |V|$ or stop when no updates were made in an iteration.

It can take even $O(n^3)$ with a complete Graph. (Connection between every node)

It will not work with graphs which have a negetive weight cycle. This means that there are some nodes that form a cycle and the sum of weights of edges between them is negative. In that case every iteration of bellman-ford will produce a new result.
But it can detect a negative weight cycle, by performing another iteration after already iterating $n-1$ times and checking if something changed. If that is the case then there is a negative weight cycle.
