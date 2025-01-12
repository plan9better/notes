[[Dynamic programming]] Algorithm for finding shortes path from single source node to all other nodes in a [[Graphs (DSA)|Graph]]. Unlink [[Djikstras algorithm]] it works with negative edge weights but does not work with negative weight cycles. 
It works by checking all possible solutions therefore finding the best one. Repeatedly relaxes all edges $n-1$ times, where $n = |V|$.
Relaxation is the same as in [[Djikstras algorithm]]:
```python
if (d[u] + c(u, v) < d[v]:
    d[v] = d[u] + c(u, v)
```

