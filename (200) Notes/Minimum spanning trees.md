### Goals
- It is a [[Graphs (DSA)|subgraph]] (includes all vertices but not all edges).
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

### Algorithms:
- [[Prims algorithm]]
- [[Kruskals algorithm]]

