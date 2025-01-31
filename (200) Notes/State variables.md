State variables in a [Dynamical system](Dynamical%20system.md) describe the current state and help us predict the next one. They are denoted $\sigma$, and take values such as $\{1, -1\}$. In the case of a coin on a table example. It could either be heads up or tails up.

Those variables allow us to describe the system in equations. Since this coin example is discrete for time we will use $n$ instead of $t$. 

State at the time $n$ is described as $\sigma (n)$. So for a state that will always be the same (coin glued to the table one side up). We can say $\sigma(n+1) = \sigma(n)$.
Or for a state that will always be the opposite of the last it would be $\sigma(n+1) = - \sigma(n)$.
