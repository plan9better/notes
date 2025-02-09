Kruskals algo is an algo for finding the [[Minimum spanning trees]] of a graph. It is similiar to [[Prims algorithm]].
### Steps.
- Choose a lowest cost edge.
- Choose another lowest cost edge, but only if adding it to your list of already selected edges doesn't form a cycle. (MST's have to be trees and therefore not cyclical.
- keep going until all edges are connected.
This way the time complexity will be: $$O(|V| \times |E|)$$ 
This however can be improved when using [[Min Heap]] to store the edges, then it will take $$ O(n\times \log n)$$