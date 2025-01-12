Kruskals algo is an algo for finding the [[Minimum spanning trees]] of a graph. It is similiar to [[Prims algorithm]].
### Steps.
- Choose a lowest cost edge.
- Choose another lowest cost edge, but only if adding it to your list of already selected edges doesn't form a cycle. (MST's have to be tree's and therefore not cyclical.
- keep going until all edges are connected.
This way the time complexity will be $O(|V| * |E|