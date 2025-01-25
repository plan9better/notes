Abstract branch of mathematics especially useful in programming, popular functional programming languages like [Haskell](Haskell.md). 

### What is a category?
A bunch of objects and arrows **(morphisms(functions))** that go between them, or more accurately it is the essence of `composition`. Arrows compose. If there exists and arrow from object **A** to object **B** and an arrow from object **B** to object **C** then there has to exist an arrow from object **A** to object **C** (their composition).

##### Arrows as functions. 
The above example with objects A, B and C can be represented with arrows (morphisms) as functions the following way:
$$
f(A) = B \ \land \ g(B) = C \implies g(f(A)) = C
$$
or equally valid: $g \circ f$. (notice the right to left order).
It can be read as "g after f".

##### Properties of composition.
- It's associative, if you have three morphisms that match end to end (like above $f(A) = B \ \land \ g(B) = C \ \land \ h(C) = D$ then  you can compose them freely (maintaining order) $(f \circ g) \circ h = f \circ (g \circ h) = f\circ g \circ h$.
- For every object $A$ there is an arrow which is a unit of composition. This arrow loops from the object to itself. Being a unit of composition means that when composed with any arrow that either starts at $A$ or ends at $A$ respectively, it gives back the same arrow. The unit arrow for object $A$ is called $\textbf{id}_{A}$ . In math notation if $A$ goes to $B$ then $f \circ \textbf{id}_{A} = f$ and $\textbf{id}_{B} \circ f= f$. It is similar to how `0 is the additive identity and 1 is the multiplicative identity`. It does not change anything about the morphism. e.g.
```haskell
id :: a -> a
id x = x
```
