For functions that grow at similar pace

### mathemathic definition
$$
    \theta (g(n)) = \{f(n) : \exists_{c1, c2} \; \exists_{n_0 \in \mathbb{N}} \; \forall_{n > n_0} \quad 0 \le c_1 \times g(n) \le f(n) \le c_2 \times g(n) \}
$$
So we can say that the running time of an algorithm (f(n)) has to be between two functions g(n) multiplied by $c_1$ and $c_2$ respectively, but only once $n$ passes a certain threshhold ($n_0$).
![[function theta.png]]
