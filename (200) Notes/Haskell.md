Functional strongly typed programming language. In Haskell functions play a key role. They work a bit like math functions, a function can only take 1 argument at a time but you can make it seem like it takes more by currying, that is function composition. For example:
```haskell
mysin x y = sin x + y
```
Is a function  that takes a number $x$ and returns a function that takes a number  $y$ and adds it to $\sin{x}$. So really there is no need to think of it like math functions but it is sometimes helpful.
