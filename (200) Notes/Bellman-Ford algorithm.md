[[Dynamic programming]] Algorithm for finding shortes path from single source node to all other nodes in a [[Graphs (DSA)|Graph]]. Unlinke [[Djikstras algorithm]] it works with negative edge weights but does not work with negative weight cycles. 
It works by checking all possible solutions therefore finding the best one. Repeatedly relaxes all edges $n-1$ times, where $n = |V|$.
Relaxation is the same as in [[Djikstras algorithm]]:
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

It can take even $O(n^3)$ with a complete [[Graphs (DSA)|Graph]]. (Connection between every node)
