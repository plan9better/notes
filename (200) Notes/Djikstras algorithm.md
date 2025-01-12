Finds the shortest path from source node to every other node in the graph with non-negative weights.
### Steps:
- Set distance to source node to 0and all nodes not directly connected to source node to $\infty$
- Find the node with the lowest distance (for first iteration, source node since all others are $\infty$)
- For each directly connected node to the selected one, check if the distance to selected node + weight of connection to neighbouring node is smaller than the current distance to neighbouring node, if so, update it.
- Repeat until all nodes are processed.

### Example:
![[djikstragraph.excalidraw]]
s -> already selected
starting vortex -> 1

| Selected vortex | 2                 | 3   | 4   | 5                        | 6        |
| --------------- | ----------------- | --- | --- | ------------------------ | -------- |
| 4               | 50                | 45  | s10 | $\infty$                 | $\infty$ |
| 5               | 50                | 45  | s10 | s10 + 15 = 25 < $\infty$ | $\infty$ |
| 2               | 25 + 20 = 45 < 50 | 45  | s10 | s25                      | $\infty$ |
|                 |                   |     |     |                          |          |
