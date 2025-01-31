Whenever a system's [state-space](State%20of%20a%20system.md), gets seperated into cycles we "remember" it and call it $Q$ and give it a number. e.g.

State-Space: $\{A, B, C, D\}$
Rules:
- Whenever we are at $A$ next state we will go to $A$. ($A -> A$)
- Whenever we are at $B$ next state we will go to $B$. ($B -> B$)
- Whenever we are at $C$ next state we will go to $D$. ($C -> D$)
- Whenever we are at $D$ next state we will go to $C$. ($D->C$)

There are 3 cycles here so we can name them $\{-1, 0, 1\}$.